using MemoryQuest.Models;

namespace MemoryQuest.Games;

public class Game
{
    // The game keeps track of the currently open card, whether a turn is being processed,
    // and the random order used for shuffling the symbol pairs before play begins.
    private readonly Random _random = new();
    private Card? _firstCard;
    private bool _isProcessing;

    public Player Player { get; }
    public List<Card> Cards { get; private set; } = [];

    public int Moves { get; private set; }
    public int Matches { get; private set; }
    public bool IsFinished => Matches == Cards.Count / 2;

    public Game(Player player)
    {
        Player = player;
    }

    public void Start()
    {
        // A new game resets score-related counters and clears the previous card state.
        Player.StartNewGame();

        Moves = 0;
        Matches = 0;
        _firstCard = null;
        _isProcessing = false;

        // Six emoji symbols are duplicated so each one has a pair, then the list is shuffled.
        string[] symbols =
        [
            "🍎", "🚀", "🐱", "🫵", "⚽", "🎵"
        ];

        Cards = symbols
            .Concat(symbols)
            .OrderBy(_ => _random.Next())
            .Select((symbol, index) => new Card(index, symbol))
            .ToList();
    }

    public async Task<bool> FlipCardAsync(Card card)
    {
        // Ignore taps if the game is already resolving a turn, the round is over,
        // or the selected card is already matched or already visible.
        if (_isProcessing || IsFinished ||
            card.IsMatched || card.IsRevealed)
            return false;

        card.Reveal();

        // First opened card is remembered so the next click can be compared against it.
        if (_firstCard is null)
        {
            _firstCard = card;
            return false;
        }

        Moves++;

        Card first = _firstCard;
        _firstCard = null;

        // When both chosen cards match, they are locked as solved and the player earns points.
        if (first.Symbol == card.Symbol)
        {
            first.MarkAsMatched();
            card.MarkAsMatched();

            Matches++;
            Player.AddPoints(10);

            if (IsFinished)
                Player.FinishGame();

            return IsFinished;
        }

        // A mismatch is shown briefly so the player can see the symbols before both cards hide again.
        _isProcessing = true;

        await Task.Delay(800);

        first.Hide();
        card.Hide();

        _isProcessing = false;
        return false;
    }
}