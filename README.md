# GammaRegimeDetection
A custom, high-performance C# indicator for ATAS (Advanced Trade Analysis Software) that calculates and visualizes real-time Gamma Exposure (GEX) regimes and net structural exposure directly on your price chart.

Key Features
Real-Time Regime Detection: Instantly identifies positive (+ GAMMA) or negative (- GAMMA) market gamma regimes based on live options open interest and strike-proximity weightings.

0DTE & Multi-Expiry Support: Automatically targets 0DTE (Zero Days to Expiration) contracts or dynamically snaps to the nearest available options series.

Configurable Throttling: Clock-boundary update frequency settings to prevent chart noise and optimize CPU performance (Live, 30 Seconds, 1 Minute, 5 Minutes, 30 Minutes, 1 Hour).

Modular Display Toggles: Easily toggle visibility for Net GEX values and Expiration DTE labels via the indicator settings panel.

Customizable Visual HUD: Fully adjustable chip positioning, padding, font scaling, and dynamic color-coded backgrounds (Green for Positive Gamma, Red for Negative Gamma).

Configuration Settings
Group	Property	Default	Description
1. Options Data	StrikesPerSide	25	Number of strikes above and below the spot price to include in the calculation.
1. Options Data	ZeroDteOnly	True	Forces the calculation strictly to today's expiration if available.
1. Options Data	ShowGexValue	True	Toggles the display of the net exposure value (e.g., 4.2M).
1. Options Data	ShowExpiry	True	Toggles the display of the target contract DTE (e.g., 0DTE).
1. Options Data	Frequency	FiveMinutes	Sets the update frequency and clock-boundary throttling.
2. Layout & Sizing	HorizontalPosition	Left	Positions the chip on the left or right side of the chart viewport.
2. Layout & Sizing	VerticalPosition	Top	Positions the chip on the top or bottom of the chart viewport.
3. Colors	PositiveColor	Green	Background color used during a positive gamma regime.
3. Colors	NegativeColor	Red	Background color used during a negative gamma regime.
Requirements
ATAS Platform v5.x or higher with an active options data feed enabled.

<img width="583" height="376" alt="image" src="https://github.com/user-attachments/assets/4a65ada2-129a-4d8d-891b-531915529976" />
<img width="611" height="621" alt="image" src="https://github.com/user-attachments/assets/254a9b4b-49ad-4698-98cd-c8260072e8a3" />


INSTRUCTIONS:

Option A: Installing via Compiled .dll File (Easiest) If you shared a pre-compiled .dll file, users can install it instantly without editing code:

Download the .dll file.

Open your ATAS custom indicators folder by pasting this path into your Windows File Explorer address bar: %APPDATA%\ATAS\Indicators

Drop the .dll file directly into that folder.

Open or restart ATAS, open any chart, and press Ctrl + I.

Look under the Custom category to find and add Gamma Regime (0DTE).

Option B: Visual Studio

Create a New Class Library Project Open Visual Studio and click Create a new project.
Search for and select Class Library (make sure it's the C# version targeting .NET Framework or the appropriate .NET runtime version your ATAS version uses, typically .NET 10 depending on the ATAS build). Click Next.

Name your project (e.g., Gamma Regime (0DTE)), choose your saving location, and click Create.

Add ATAS Reference Assemblies To compile ATAS indicators, your project needs references to the core ATAS libraries (ATAS.Indicators.dll and OFT.Rendering.dll).
In the Solution Explorer on the right, right-click on Dependencies (or References) and select Add Reference... (or Manage NuGet Packages if applicable).

Click Browse and navigate to your ATAS installation directory (usually C:\Program Files\ATAS\ or your user path).

Select the following required DLL files:

ATAS.Indicators.dll

OFT.Rendering.dll

Any other dependencies referenced by your project (like data feed cores).

Click OK to add them. (Tip: In the reference properties, set Copy Local to False since ATAS loads these natively at runtime).

Add the Code File Visual Studio automatically creates a default file named Class1.cs. Right-click it, select Rename, and change it to MyCustomIndicator.cs.
Open the file, delete any placeholder code, and paste your indicator C# source code into it.

Save the file (Ctrl + S).

Build the Project Go to the top menu and select Build > Clean Solution (to clear out old build caches).
Select Build > Build Solution (Ctrl + Shift + B).

Check the Output window at the bottom to ensure it says 1 succeeded, 0 failed.

Deploy to ATAS Once built successfully, go to your project folder in Windows Explorer and find the compiled file located in bin\Debug\ or bin\Release.
Copy the generated .dll file.

Drop it directly into your local ATAS indicators folder: %APPDATA%\ATAS\Indicators

Open ATAS, open a chart, press Ctrl + I, and add your custom indicator from the list!

(If you have any trouble during this process, chatgpt, claude or gemini is your friend)

