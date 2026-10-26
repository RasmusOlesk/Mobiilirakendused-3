namespace MemoryQuest.Models;

public class Player
{
    // The player keeps their name and the statistics used during the game session.
    public string Name { get; private set; }

    public int Score { get; private set; }
    public int GamesPlayed { get; private set; }
    public int BestScore { get; private set; }

    public Player(string name)
    {
        // A blank name falls back to a default player name so the UI still has a valid display value.
        Name = string.IsNullOrWhiteSpace(name)
            ? "Mängija"
            : name.Trim();
    }

    public void AddPoints(int points)
    {
        // Points are only awarded for positive values to avoid any accidental score resets.
        if (points > 0)
            Score += points;
    }

    public void StartNewGame()
    {
        // A new round always starts with a clean score.
        Score = 0;
    }

    public void FinishGame()
    {
        // Finished rounds are counted and the best result is stored for later comparisons.
        GamesPlayed++;

        if (Score > BestScore)
            BestScore = Score;
    }
}
