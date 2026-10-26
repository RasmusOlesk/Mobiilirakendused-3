namespace MemoryQuest.Models;

public class Player
{
    public string Name { get; private set; }

    public int Score { get; private set; }
    public int GamesPlayed { get; private set; }
    public int BestScore { get; private set; }

    public Player(string name)
    {
        Name = string.IsNullOrWhiteSpace(name)
            ? "Mängija"
            : name.Trim();
    }

    public void AddPoints(int points)
    {
        if (points > 0)
            Score += points;
    }

    public void StartNewGame()
    {
        Score = 0;
    }

    public void FinishGame()
    {
        GamesPlayed++;

        if (Score > BestScore)
            BestScore = Score;
    }
}