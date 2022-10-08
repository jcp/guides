# Linux

## Table of Contents

* [Commands](#commands)
  * [diff](#diff)
  * [find](#find)
  * [grep](#grep)
  * [ln](#ln)
  * [sed](#sed)
  * [tail](#tail)
* [Shortcuts](#shortcuts)

## Commands

### `diff`

Compare difference between two files.

```shell
diff -u [file1] [file2]
```

### `find`

Search for a file in a directory.

```shell
find [dir] -name [filename]
```

### `grep`

Search for a pattern in a file.

```shell
grep -i [pattern] [file]
```

### `ln`

Create a symbolic link

```shell
ln -s [source] [destination]
```

### `sed`

Find and replace a string within a file.

```shell
sed -i 's/[find]/[replace]/' [file]
```

### `tail`

Monitor a file.

```shell
tail -f [file]
```

## Shortcuts

### Terminal

| Shortcut | Description |
| -------- | ----------- |
| <kbd>Control</kbd> + <kbd>Alt</kbd> + <kbd>A</kbd> | Add terminal |
| <kbd>Control</kbd> + <kbd>Alt</kbd> + <kbd>D</kbd> | Add terminal down |
| <kbd>Control</kbd> + <kbd>Alt</kbd> + <kbd>R</kbd> | Add terminal right |
| <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>▲, ▼, ◄, ►</kbd> | Directionally resize a terminal |
| <kbd>Control</kbd> + <kbd>Tab</kbd> | Switch to next terminal |
| <kbd>Control</kbd> + <kbd>Shift</kbd> + <kbd>Tab</kbd> | Switch to previous terminal |
| <kbd>Alt</kbd> + <kbd>▲, ▼, ◄, ►</kbd> | Directionally switch to a terminal |
| <kbd>Alt</kbd> + <kbd>0 - 9</kbd> | Switch to a specific terminal |
