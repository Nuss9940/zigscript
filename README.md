Zigscript
=========

Installation
------------

Put the zigscript file in this repository on your $PATH

    # ln -s zigscript /usr/local/bin/

How to use
----------

Simply put

    #!/usr/bin/env zigscript

in the first line of your script.

Example:

    #!/usr/bin/env zigscript
    const std = @import("std");

    pub fn main() !void {
        const stdout = std.io.getStdOut().writer();
        try stdout.print("Hello, {}!\n", .{"world"});
    }

Save it as `example`, make sure it's executable and run it:

    $ ./example
    Hello, world!

How it works
------------

It simply copies your script to another directory excluding the first line. Then `zig run` is
called with the copied file as an argument. It compiles the code and runs the result. Zig's caching
system will make sure to only recompile when there are changes in the script.

Limitations
-----------

- You will need a main function, just like in any other executable zig program
- All your code needs to be in one file. You may import stuff from the standard library
- Line numbers on compile errors/warnings are off by one

See also
--------

Closed issue on this topic: https://github.com/ziglang/zig/issues/2165

