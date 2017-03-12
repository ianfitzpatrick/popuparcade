# Popup Arcade Using Attract Mode

This is a combination guide and collection of settings files you need to run your own popup arcade. 

What you get is a sort of kiosk of games that you can scroll through using your game pad. Each entry includes:

- A full screen video trailer of the game
- A lower third with:
    + Game title
    + Game creator (company / person / whatever)
    + Game description
    + Number of total games + what entry you are viewing ("2/15")

[Here's how it looks!](https://www.youtube.com/watch?v=1sqFD52btIo)

This is a custom layout I adapted for Attract Mode. It's working within the constraint of "getting artwork for games at the appropriate sizes is hard, but everybody has a trailer."

It's also assumed you are using a bigscreen TV and XBox 360 Gamepads. So 1080p reoslution is hardcoded into the layout and XBox 360 gamepad configs are hardcoded into the configs. 

Hitting the `a button` on XBox 360 gamepad will launch a game.

And if you follow the `Enjoyable` instructions, `select` + `start` will quit any game.

Please note all instructions are for Mac OS X, and have been tested specifically on 10.11 El Capitan. 

However it should be fairly easy to adapt these instructions to Windows as well.

##### Sidebar For Those Who Know What They Are Doing Already

If you already know how to use Attract Mode and just want a layout that works well for a popup arcade, [get the popuparacde layout here](https://github.com/ianfitzpatrick/popuparcadelayout).


### The Basics

The five things you need to run the arcade are:
 
1. Attract Mode (front end launcher app)
2. Folder that contains Attract mode settings folder that contains:
    +  All settings files
    +  Custom popuparcade layout
    +  The actual game executables (called 'roms')
    +  Video trailers for games
3. Latest XBox 360 Driver for Mac
4. Enjoyable (gamepad -> key mapper)
5. Re-map Attract Mode quit key

### 1. Attract Mode

Attract Mode is a cross-platform front-end launcher app, typically used to in mutli-game arcade cabinets. It's able to launch games from a huge selection of emulators, and provide a cool cohesive sorta experience.

We're using it in a slightly weird way. Instead of launching games from multiple emulators (mame, nes, genesis, etc.) we are launching using the `mac` emulator. It's called an emulator, but really think of it more as just a launcher. 

##### Attract Mode Version

This config has been tested with Attract Mode version `v2.0.0-rc3-22`, which is a nightly build. **Not** the binary that appears on the main download page.

It's important to use this version or higher, because previous versions had a few deal breaker bugs.

[Download Attract Mode Nightly Builds for Mac here](https://build.zaplabs.com/project/attractmode/)

### 2. Attract Mode Settings Folder

Attract Mode stores it's settings in:

`~/.attract`

in other words:

`/Users/<yourusername>/.attract`   

Copy the `.attract/` folder in this repo to your home folder

If you aren't comfortable with the command line, you'll need to [enable showing hidden files in the finder](http://ianlunn.co.uk/articles/quickly-showhide-hidden-files-mac-os-x-mavericks/) to complete this task.

##### Setting Up Games In Attract Mode

There's a few directories and files inside the `~/.attract` folder you need to know about in order to add your games to the arcade.

I've included my game *Super Deference Fighter* as a reference game, complete with video trailer, so you can see a working example.

To add a game, first open:

    ~/.attract/romlists/mac.txt

Copy and paste the existing game and edit each field appropritately. 

**romlists fields**

- Name Field: The exact name of the game app executable as it will appear in `~/.attract/mac/roms`
- Title Field: How the name of the game will appear in the attract mode display
- Emulator Field: This should always just be `mac`
- Manufacturer Field: The name of the company or person that made this game
- Extra Field (last field): A one paragraph description of the game that is 300 characters or less

Next, put your game's executable file in:

`~/.attract/mac/roms/`

The name of your exexcutable should **exactly** match the `Name Field` value in your romlist.

Next, put the game's video trailer here:

`~/.attract/mac/videos/`

Again, the filename of this video should match exactly the `Name Field` in your romlist. The file extension can be whatever is appropriate (mp4, mkv) etc.

Protip: Use [youtube-dl](https://rg3.github.io/youtube-dl/) to just download trailers from Youtube, rather than trying to wrangle the original files from gamedevs.

That's it for Attract Mode!

### 3. XBox 360 Driver for Mac

[Download and install the latest Xbox 360 Driver here](https://github.com/360Controller/360Controller/releases)

Plug it in and make sure things are working.

Gamepads have a way of changing "who player one is" so all gamepads have been configured to control Attract Mode.

### 4. Enjoyable Key Mappings

Enjoyable allows us to map `Select + Start` to `⌘Q`, creating a global quit key combo.

This allows players to have a totally keyboard-less gaming experience. Launching and quitting back to attract mode entirely with the gamepad.

##### Configuring Enjoyable

First [get and install Enjoy 2](https://yukkurigames.com/enjoyable/). 

Next double click the the `popuparcade.enjoyable` key layout file. 

This will load the saved profile that allows you to quit any game with by pressing `SEELCT` + `START`. Just minimize Enjoy 2 and keep it running in the background.

This mapping also includes some extra keys mappings for games that don't natively support gamepads. Here are the mappings:

```
D-Pad Up: p
D-Pad Down: ;
D-Pad Left: l
D-Pad Right: '


A : [
B : ]
X : -
Y : =
```

Rarely used keys were purposely selected here, so as to try and avoid key mapping conflicts with other games.

Mappings for players 1-4 XBOX 360 controllers have already been entered.

### 5. Re-map Attract Mode Quit Key

This is an optional step, but it keeps your players from accidentally quitting attract mode.

1. Open system preferences
2. Keyboard panel
3. Shortcuts tab
4. App Shortcuts in left-hand list
5. Create new app shortcut
    - Application: Attract
    - Menu Title: Quit Attract
    - Keyboard Shortcut: ⌥⌘Q (or whatever you prefer)




