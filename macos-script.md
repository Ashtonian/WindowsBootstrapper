
* Install macos. 
* verify trim, mem size, apfs. 
* update macos and sign into apple + google accounts. 
* cleanup dock
* adjust energy settings
* adjust topbar
* homewbrew
* brew install
* mackup restore

* package manager preference brew/cask -> mas - don't use app store gui, use `mas`


```zsh
# prereq
sudo xcode-select --install

# install homebrew 
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# install brewfile brew, cask, and mas packages, including zsh
brew bundle

# install oh my zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# set zsh as default shell for user 
chsh -s /bin/zsh


# have a look at potential menu bar options 
ls /System/Library/CoreServices/Menu\ Extras/ 

# edit plist manually with Xcode 
# open -a Xcode ~/Library/Preferences/com.apple.systemuiserver.plist  

# fix menu bar - warning if system doesn't have one of these like AirPort or Bluetooth it will break
defaults write com.apple.systemuiserver menuExtras -array \
"/System/Library/CoreServices/Menu Extras/AirPort.menu" \
"/System/Library/CoreServices/Menu Extras/Bluetooth.menu" \
"/System/Library/CoreServices/Menu Extras/Clock.menu" \
"/System/Library/CoreServices/Menu Extras/Displays.menu" \
"/System/Library/CoreServices/Menu Extras/Volume.menu" \

# refresh ui
killall SystemUIServer

# change clock format 
defaults write com.apple.menuextra.clock IsAnalog -bool false
defaults write com.apple.menuextra.clock DateFormat -string "EEE d MMM HH:mm:ss" 

# refresh ui
killall SystemUIServer

# set timezone 
sudo systemsetup -settimezone "America/Chicago"

# get current zone 
# sudo systemsetup -gettimezone

# get list of potential zones 
sudo systemsetup -listtimezones.

# for py
pip install ipython
```