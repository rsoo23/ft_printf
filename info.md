
Mandatory
man 3 stdarg: https://linux.die.net/man/3/stdarg
    va_list ap;
    va_start(ap, last); 
        - initialise var arg list
    va_arg(ap, type); 
        - each call to va_arg() modifies ap so that the next call returns the next argument
    va_end(ap); 
        - clean up var arg list

Notes:
    - % indicates that the following characters specify a conversion specification
    - return value: number of characters printed (output error: return neg value)

Conversions / Specifiers: cspdiuxX%
    [x] c: char
    [x] s: string of char
    [x] p: memory address
    [x] d: decimal int (same as %i for printf, but for scanf, %i auto detects the base)
    [x] i: dec / oct / hex int
    [x] u: unsigned int
    [x] x: hex int (lowercase: a-f)
    [x] X: hex int (lowercase: A-F)
    [x] %

-----------------------------------------------------------------------------------------------
Bonus

Format tag prototypes: %[flags][width][.precision][length]specifier

%[-+0# ][int][.int][char]

Summary:

| Flag         | Desc                       | Valid Specifiers | Exceptions       | Error Check
|--------------|----------------------------|------------------|------------------|-------------
| [ ] #        | Adds 0x / 0X               | xX               |                  | done
| [ ] 0        | Zero padding               | diuxX            | ignore when '-0' | done
| [ ] +        | Adds '+'                   | diu              |                  | done
| [ ] -        | Left adjust                | cspdiuxX%        |                  | no need
| [ ] ' '      | Adds ' ' in front of + num | diu              | ignore when ' +' | done 
| [ ] precision| Truncates string           | s                |                  | done
| [ ] mfw      | Space padding              | cspdiuxX%        |                  | no need

Checklist:
- [x] handle the inconsistency between format specifier and input
        - apparently like casting
        - %x able to print char since it has ascii val
        - conclusion: still works even if error in compiling

- [x] error handling
        - placement:
        - [x] check flag
        - [x] mfw and prec
        - [x] check spec
        - exceptions:
        - [x] duplicate flags
        - [x] check -0 and ' +', ignore the respective flag

- [ ] implement the easy extra: # + precision



Cases:
ft_printf("%%", )
ft_printf("%d")
ft_printf("testing", )