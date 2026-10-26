namespace MemoryQuest.Models;

public class Card
{
    public int Id { get; }
    public string Symbol { get; }

    public bool IsRevealed { get; private set; }
    public bool IsMatched { get; private set; }

    public string DisplayText =>
        IsRevealed || IsMatched ? Symbol : "?";

    public Card(int id, string symbol)
    {
        Id = id;
        Symbol = symbol;
    }

    public bool Reveal()
    {
        if (IsRevealed || IsMatched)
            return false;

        IsRevealed = true;
        return true;
    }

    public void Hide()
    {
        if (!IsMatched)
            IsRevealed = false;
    }

    public void MarkAsMatched()
    {
        IsRevealed = true;
        IsMatched = true;
    }
}