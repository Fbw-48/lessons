# Additional commands

1. Go to last directory

```bash
  cd - # got to previous folder
```

2. Reference last command
   You can use this to prefix or append something on your last input

```bash
  !! # repeat last cmd - this is especially helpful with sudo ;)

  # For example
  apt-get install tree
  # -> not permitted
  sudo !!
  # equals to: sudo apt-get install tree
```
