namespace MemoryQuest.Models;

public class Theme
{
    // Each theme defines the colors and font used to style the game screen.
    public string Name { get; }
    public Color BackgroundColor { get; }
    public Color TextColor { get; }
    public Color CardColor { get; }
    public Color AccentColor { get; }
    public string FontFamily { get; }

    public Theme(
        string name,
        Color backgroundColor,
        Color textColor,
        Color cardColor,
        Color accentColor,
        string fontFamily)
    {
        Name = name;
        BackgroundColor = backgroundColor;
        TextColor = textColor;
        CardColor = cardColor;
        AccentColor = accentColor;
        FontFamily = fontFamily;
    }

    public void Apply(ContentPage page)
    {
        // The selected theme is applied directly to the page and the XAML resources used by the UI.
        page.BackgroundColor = BackgroundColor;

        page.Resources["BackgroundColor"] = BackgroundColor;
        page.Resources["TextColor"] = TextColor;
        page.Resources["CardColor"] = CardColor;
        page.Resources["AccentColor"] = AccentColor;
        page.Resources["GameFont"] = FontFamily;
    }

    // These static themes let the player switch between a light, dark, and colorful visual style.
    public static Theme Light => new(
        "Hele",
        Colors.WhiteSmoke,
        Colors.DarkSlateGray,
        Colors.White,
        Colors.RoyalBlue,
        "OpenSansRegular");

    public static Theme Dark => new(
        "Tume",
        Color.FromArgb("#171923"),
        Color.FromArgb("#F7FAFC"),
        Color.FromArgb("#2D3748"),
        Color.FromArgb("#9F7AEA"),
        "OpenSansRegular");

    public static Theme Colorful => new(
        "Värviline",
        Color.FromArgb("#FFF0F5"),
        Color.FromArgb("#54245C"),
        Color.FromArgb("#FFFFFF"),
        Color.FromArgb("#E75480"),
        "OpenSansRegular");
}
