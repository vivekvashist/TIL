How to apply a macro to a set of lines?

> Use the `normal` command in `Ex` mode

```python
# Exccute the macros in register a on lines 5 through 10

:5,10norm! @a

# Exccute the macros in register a on lines 5 through to the end of the file

:5,$norm! @a

# Exccute the macros in register a on all lines 

:%norm! @a

:5,$norm! @a

# Execute the macro stored in a register a on all lines matching a pattern

:g/pattern/norm! @a

# Execute macro on visually selected lines, press V and j or k until desred region is selected and then type :norm! @a

:'<,'>norm! @a
```
