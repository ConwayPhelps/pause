# pause_5.0.1

What this script does:
  1. Allows for the interruption of the current process until either the optional timer reaches [00] or the user presses any alphanumeric key. 
  2. You can change the prompt text. (Must be double quoted)
  3. You can add a response after the key press. (Must be double quoted)
  4. Offers a quiet mode for countdown without prompt. (Timer must be set)
  5. All text inputed for prompt and response are sanatized to remove malicious escape codes from being used.
  6. The single key input of the pressed key is echoed for use in other parts of script 
     
  To get the return key pressed, use command substitution to execute the script and the script will echo the key directly into the variable.

Example of command substitution:

    echo "Your options are:
    echo "1. Check service status"
    echo "2. Start service"
    echo "3. Stop service"
    echo
    choice=$(pause -p "Enter your selection: ")
    case "$choice" in
        "1")
            echo "Checking service status..."
            # Add actual status check command here
            ;;
        "2")
            echo "Starting service..."
            # Add start command here
            ;;
        "3")
            echo "Stopping service..."
            # Add stop command here
            ;;
        *)
            # Default case for any other input
            echo "Invalid choice: $choice" >&2
            exit 1
            ;;
    esac

    
Switch options:

    [-p|--prompt] [-t|--timer] [-r|--response] [-h|--help] [-q|--quiet]
  
    -p, --prompt    [ input required (string must be in quotes) ]
    -t, --timer     [ number of seconds ]\n"
    -r, --response  [ requires text (string must be in quotes) ]
    -h, --help      [ this information ]
    -q, --quiet     [ quiet text, requires timer to be set. ]
Example:

    $ pause
    $ Press any key to continue...
                
Example:

    $ pause -t 10
    $ [10] Press any key to continue... 
                
Example:

    $ pause -t 10 -p Hello World
    $ [10] Hello World
                
Example:

    $ pause -t 10 -p "Hello World" -r "And here we go."
    $ [10] Hello World
    $ And here we go.
    
The timer will be in the format [00:00:00] and each part will disappear once that part reaches zero until only the seconds, [00], remains.
The key pressed will echo as an output that can be grabbed or ignored.
