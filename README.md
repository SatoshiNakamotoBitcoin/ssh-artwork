# SSH Artist

Want to find an SSH key with a specific hash visualization pattern? If so, then
this is the tool for you. If not, just don't make me SSH into your servers with
their ugly-ass keys.

## Visualizing Public Keys

OpenSSH 5.1 introduced a visual hash representation of public keys. From its changelog:

 * Introduce experimental SSH Fingerprint ASCII Visualisation to ssh(1)
   and ssh-keygen(1). Visual fingerprinnt display is controlled by a new
   ssh_config(5) option "VisualHostKey". The intent is to render
   SSH host keys in a visual form that is amenable to easy recall and
   rejection of changed host keys. This technique inspired by the
   graphical hash visualisation schemes known as "random art[*]", and
   by Dan Kaminsky's musings at 23C3 in Berlin.

   Fingerprint visualisation in is currently disabled by default, as the
   algorithm used to generate the random art is still subject to change.

   [*] "Hash Visualization: a New Technique to improve Real-World
       Security", Perrig A. and Song D., 1999, International Workshop on
       Cryptographic Techniques and E-Commerce (CrypTEC '99)
   
   http://users.ece.cmu.edu/~adrian/projects/validation/validation.pdf
   
   http://lists.mindrot.org/pipermail/openssh-unix-dev/2008-July/026693.html
   
You can visualize your existing keys with the following command:

```
ssh-keygen -lv -f ~/.ssh/id_rsa.pub
```

It's probably gibberish, as expected from all the randomness involved. My
original key looked like this:

```
+---[RSA 4096]----+
|          **o.ooO|
|         *oo.+.B.|
|        o E*o** =|
|         .o O++=o|
|        S  . =o+ |
|            . o  |
|             . o |
|            oo  =|
|            .o++o|
+----[SHA256]-----+
```

## Good Looking Public Keys

Once visualization is introduced, so is aesthetics. This feature presents a
great opportunity to fight against truly random key generation in order to trade
security for arbitrary human desires.

For example, I wanted a key that looked like this:

```
+------[RSA]------+
|                 |
|  .OOOO    OOO   |
|  ..OOOO  OOO.   |
|  ...OOOOOOO.    |
|   ...OOSOO.     |
|    ...OEO.      |
|     .....       |
|      ...        |
|                 |
+-----[SHA256]----+
```

In order to get it, draw the desired end state on the `keys/E.art` and then
start the artist creative process with

```
./ssh-artist
```

and kill the artist when patience is depleted.
