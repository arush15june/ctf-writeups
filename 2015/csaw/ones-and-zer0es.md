### Solved by superkojiman

"Video" file with a title from Mr. Robot: eps1.1_ones-and-zer0es_c4368e65e1883044f3917485ec928173.mpeg

Not really video, run xxd on it to get binary dump:

```
$ xxd -g1 eps1.1_ones-and-zer0es_c4368e65e1883044f3917485ec928173.mpeg
00000000: 30 31 31 30 30 31 31 30 30 31 31 30 31 31 30 30  0110011001101100
00000010: 30 31 31 30 30 30 30 31 30 31 31 31 30 31 30 30  0110000101110100
00000020: 30 31 31 31 31 30 31 31 30 31 30 31 30 30 30 30  0111101101010000
00000030: 30 31 31 30 30 31 30 31 30 31 31 30 31 31 31 31  0110010101101111
00000040: 30 31 31 31 30 30 30 30 30 31 31 30 31 31 30 30  0111000001101100
00000050: 30 31 31 30 30 31 30 31 30 30 31 30 30 30 30 30  0110010100100000
00000060: 30 31 31 30 30 30 30 31 30 31 31 30 31 31 30 30  0110000101101100
.
.
.
```

Extract the binary:

```
$ xxd -ps eps1.1_ones-and-zer0es_c4368e65e1883044f3917485ec928173.mpeg | sed 's/30/0/g' | sed 's/31/1/g' | tr -d '\n'
```

This gives us

```
01100110011011000110000101110100011110110101000001100101011011110111000001101100011001010010000001100001011011000111011101100001011110010111001100100000011011010110000101101011011001010010000001110100011010000110010100100000011000100110010101110011011101000010000001100101011110000111000001101100011011110110100101110100011100110010111001111101001000000100100100100111011101100110010100100000011011100110010101110110011001010111001000100000011001100110111101110101011011100110010000100000011010010111010000100000011010000110000101110010011001000010000001110100011011110010000001101000011000010110001101101011001000000110110101101111011100110111010000100000011100000110010101101111011100000110110001100101001011100010000001001001011001100010000001111001011011110111010100100000011011000110100101110011011101000110010101101110001000000111010001101111001000000111010001101000011001010110110100101100001000000111011101100001011101000110001101101000001000000111010001101000011001010110110100101100001000000111010001101000011001010110100101110010001000000111011001110101011011000110111001100101011100100110000101100010011010010110110001101001011101000110100101100101011100110010000001100001011100100110010100100000011011000110100101101011011001010010000001100001001000000110111001100101011011110110111000100000011100110110100101100111011011100010000001110011011000110111001001100101011101110110010101100100001000000110100101101110011101000110111100100000011101000110100001100101011010010111001000100000011010000110010101100001011001000111001100101110
```

Which translates to:

```
flat{People always make the best exploits.} I've never found it hard to hack most people. If you listen to them, watch them, their vulnerabilities are like a neon sign screwed into their heads.
```

Flag: People always make the best exploits.