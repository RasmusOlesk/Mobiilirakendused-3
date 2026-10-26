using Microsoft.Extensions.DependencyInjection;

namespace MemoryQuest
{
    public partial class App : Application
    {
        // The app entry point creates the main window and loads the shell-based navigation structure.
        public App()
        {
            InitializeComponent();
        }

        protected override Window CreateWindow(IActivationState? activationState)
        {
            return new Window(new AppShell());
        }
    }
}
