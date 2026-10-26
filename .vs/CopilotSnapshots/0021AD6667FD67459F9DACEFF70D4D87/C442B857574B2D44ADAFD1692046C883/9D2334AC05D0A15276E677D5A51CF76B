using MemoryQuest.Games;
using MemoryQuest.Models;

namespace MemoryQuest.Views;

public partial class MainPage : ContentPage
{
    private readonly Player _player;
    private readonly Game _game;

    private Theme _currentTheme = Theme.Light;
    private bool _isShowingResult;

    public MainPage()
    {
        InitializeComponent();

        _player = new Player("Mängija");
        _game = new Game(_player);

        _currentTheme.Apply(this);
        StartNewGame();
    }

    private void StartNewGame()
    {
        _isShowingResult = false;

        _game.Start();

        CardsView.ItemsSource = _game.Cards.ToList();

        UpdateStatistics();
    }

    private async void OnCardClicked(
    object sender, EventArgs e)
    {
        if (sender is not Button button ||
            button.BindingContext is not Card card)
            return;

        bool finished = await _game.FlipCardAsync(card);

        CardsView.ItemsSource = _game.Cards.ToList();
        UpdateStatistics();

        await button.ScaleToAsync(1.05, 70);
        await button.ScaleToAsync(1.0, 70);

        if (finished && !_isShowingResult)
        {
            _isShowingResult = true;

            // Muutke DisplayAlertAsync -> DisplayAlert
            await DisplayAlert(
                "🎉 Palju õnne!",
                $"Leidsid kõik paarid!\n\n" +
                $"Punktid: {_player.Score}\n" +
                $"Käigud: {_game.Moves}\n" +
                $"Parim tulemus: {_player.BestScore}",
                "Mängi uuesti");

            StartNewGame();
        }

    }

    private void UpdateStatistics()
    {
        ScoreLabel.Text = _player.Score.ToString();
        MovesLabel.Text = _game.Moves.ToString();
        MatchesLabel.Text = $"{_game.Matches} / 6";
    }

    private void OnNewGameClicked(
        object sender, EventArgs e)
    {
        StartNewGame();
    }

    private void OnLightThemeClicked(
        object sender, EventArgs e)
    {
        ChangeTheme(Theme.Light);
    }

    private void OnDarkThemeClicked(
        object sender, EventArgs e)
    {
        ChangeTheme(Theme.Dark);
    }

    private void OnColorfulThemeClicked(
        object sender, EventArgs e)
    {
        ChangeTheme(Theme.Colorful);
    }

    private void ChangeTheme(Theme theme)
    {
        _currentTheme = theme;
        _currentTheme.Apply(this);
    }
}