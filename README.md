# Northview Campus Companion Config

# Usage

Import the appropriate campus config file from `./campuses/[campusname].companionconfig` into the [StreamDeck Companion Server](https://github.com/bitfocus/companion)

# Updating the Master File

Currently `./GreaterLafayette.companionconfig` serves as the base file that all other campus configs are generated from. Updates to this file are pushed to campus files via GitHub runners

# GitHub Runners

Currently GitHub runners update the `./campuses` folder with configs for each campus

At each commit or pull request it will do the following on a virtual machine:

1. Pull the latest codebase from the git repo
2. Create copies of `./GreaterLafayette.companionconfig` for each campus in the `./campuses` directory
3. Find and replace Lafayette IP Addresses with each campuses IP Addresses & Set Campus Name on the info page
4. Commit the Changes
5. Pull and subsequently Push the updates to the repo

# Known Issues/Limitations

- The Greater Lafayette production network lives at `10.4.x.x`, by doing a find and replace with `10.4.` to `10.[campusProperty].`the ip address `10.4.10.4` would be adversely impacted and replaced with `10.x.10.x` instead of `10.x.10.4`. This is solvable but we do not currently use `10.x.10.4` for anything, so right now, I don’t care to mess with the regex.
