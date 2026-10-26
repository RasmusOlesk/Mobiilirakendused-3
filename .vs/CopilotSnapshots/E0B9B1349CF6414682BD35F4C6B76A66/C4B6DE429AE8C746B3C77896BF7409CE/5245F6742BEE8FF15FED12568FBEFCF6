namespace MemoryQuest.Models;

public class Card
{
    // Each card has a unique identifier and the emoji symbol it represents.
    public int Id { get; }
    public string Symbol { get; }

    // The card state tells whether it is currently visible to the player and whether it has been matched.
    public bool IsRevealed { get; private set; }
    public bool IsMatched { get; private set; }

    // The UI can display a hidden question mark until the card is revealed or solved.
    public string DisplayText =>
        IsRevealed || IsMatched ? Symbol : "?";

    public Card(int id, string symbol)
    {
        Id = id;
        Symbol = symbol;
    }

    public bool Reveal()
    {
        // A card cannot be shown twice if it is already visible or already matched.
        if (IsRevealed || IsMatched)
            return false;

        IsRevealed = true;
        return true;
    }

    public void Hide()
    {
        // Matched cards stay visible, while unmatched cards are hidden again after a short delay.
        if (!IsMatched)
            IsRevealed = false;
    }

    public void MarkAsMatched()
    {
        // When a pair is found, the card remains visible and is marked as solved.
        IsRevealed = true;
        IsMatched = true;
    }
}
