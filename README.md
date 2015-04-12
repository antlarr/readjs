# readjs

readjs is a simple application that waits until the user presses a key in the
keyboard, moves the joystick or presses a button or there is a timeout.
It returns the event in its stdout, so this is very useful to create selection
menus from the shell in which the user can select an option by pressing a key
or a joystick button. 

# Usage

```sh
readjs [-h] [-j [JSDEVICES [JSDEVICES ...]]] [-a] [-t TIMEOUT]
```

```sh
optional arguments:

  -h, --help            show this help message and exit
  -j [JSDEVICES [JSDEVICES ...]], --js-devices [JSDEVICES [JSDEVICES ...]]
                        Read from a joystick device(s). If no joystick device
                        is specified, all available joysticks are read
  -a, --all-events      Return all events without trying to be smart since the
                        default behaviour ignores button releases from presses
                        prior to the command execution.
  -t TIMEOUT, --timeout TIMEOUT
                        Number of seconds to wait before timing out with
                        return code 2
```
# Example

```sh
readjs -j -t 5
```

This waits for 5 seconds for the user to press any key or interact with any
joystick. If the user presses a key, it's sent to stdout. If the user
interacts with the joystick text similar to the next is written to stdout:

* JS js0 Button 0 Press
* JS js0 Button 5 Release
* JS js1 Stick +X
* JS js1 Stick -y

Finally, if after 5 seconds the user didn't do anything, the application
finishes with return code 2.


# License

```
readjs waits for an event from the keyboard or js and writes it to stdout
Copyright (C) 2015 Antonio Larrosa <larrosa at kde.org>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
