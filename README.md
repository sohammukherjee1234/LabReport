## Design: 4-to-2 encoder

### Description
In general an encoder is a device or process that converts data from one format to another. In Digital Logic, an encoder is a combinational circuit that performs the reverse operation of Decoder. It has maximum of  2^n  input lines and ‘n’ output lines, hence it encodes the information from 2^n inputs into an n-bit code. It will produce a binary code equivalent to the input, which is active High. Therefore, the encoder encodes 2^n input lines with ‘n’ bits. A 4 to 2 encoder takes 4 input lines and produces 2 output lines.

### Truth Table

![alt Table 0](https://raw.githubusercontent.com/sohammukherjee1234/LabReport/master/table0.png "Truth Table")

### Diagram

![alt diagram](https://www.tutorialspoint.com/digital_circuits/images/4_2_encoder.jpg "Block Diagram")

### Implementation

#### Using Structural Modelling

```vhdl
libraryIEEE;
useIEEE.STD_LOGIC_1164.ALL;

entity fourtwoenc is
Port(i:in	STD_LOGIC_VECTOR(3downto0);
    o:out	STD_LOGIC_VECTOR(1downto0));
end fourtwoenc;

architecture Behavioral of fourtwoenc is 
begin
    o(0) <= i(1) or i(3);
    o(1) <= i(2) or i(3);
end Behavioral;

```

#### Using behaviour modelling using concurrent statements

```vhdl
libraryIEEE;
useIEEE.STD_LOGIC_1164.ALL;

entity fourtwoenc_conc is
    Port(i:in	STD_LOGIC_VECTOR(3downto0);
         o:out	STD_LOGIC_VECTOR(1downto0));
end fourtwoenc_conc;

architecture Behavioral of fourtwoenc_conc is 
begin
    with i select o<=
    "00"when"0001",
    "01"when"0010",
    "10"when"0100",
    "11"when"1000",
    "ZZ"when others;
end Behavioral;
```

#### Using behaviour modelling using sequential statements

```vhdl
libraryIEEE;
useIEEE.STD_LOGIC_1164.ALL;

entity fourtwoenc_seq is
    Port(i:in	STD_LOGIC_VECTOR(3downto0);
         o:outSTD_LOGIC_VECTOR(1downto0));
end fourtwoenc_seq;

architecture Behavioral of fourtwoenc_seq is 
    begin
        Process(i)
            begin
                case i is
                    when"0001" => o <= "00";
                    when "0010" => o <= "01";
                    when"0100" => o <= "10";
                    when"1000" => o <= "11";
                    when others => o <= "ZZ";
                end case;

        end Process;
end Behavioral;
```


## Design: 8-to-3 encoder

### Description

In general an encoder is a device or process that converts data from one format to another. In Digital Logic, an encoder is a combinational circuit that performs the reverse operation of Decoder. It has maximum of  2^n  input lines and ‘n’ output lines, hence it encodes the information from 2^n inputs into an n-bit code. It will produce a binary code equivalent to the input, which is active High. Therefore, the encoder encodes 2^n input lines with ‘n’ bits. A 8 to 3 encoder has 8 input lines and 3 output lines

### Truth Table

![alt Truth Table](https://raw.githubusercontent.com/sohammukherjee1234/LabReport/master/table1.png "Truth Table")

### Diagram

![alt Diagram](https://media.geeksforgeeks.org/wp-content/uploads/Encoder-8x3.jpg "Diagram")

### Implementation


#### Using Structural modelling

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;



entity eighttothreeenc is
    Port ( i : in    STD_LOGIC_VECTOR (7 downto 0);
           o : out    STD_LOGIC_VECTOR (2 downto 0)); 
end eighttothreeenc;

architecture Behavioral of eighttothreeenc is
begin
    o(0)<= i(1) or i(3) or i(5) or i(7);
    o(1)<= i(2) or i(3) or i(6) or i(7);
    o(2)<= i(4) or i(5) or i(6) or i(7);
end Behavioral;
```


#### Using Behavioral modelling using Select statements

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity eighttothree_select is
    Port ( i : in    STD_LOGIC_VECTOR (7 downto 0);
           o : out    STD_LOGIC_VECTOR (2 downto 0)); 
end eighttothree_select;

architecture Behavioral of eighttothree_select is
begin
    o(0)<= i(1) or i(3) or i(5) or i(7);
    o(1)<= i(2) or i(3) or i(6) or i(7);
    o(2)<= i(4) or i(5) or i(6) or i(7);
end Behavioral;
```


#### Using Behavioral modelling using Case statements

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity eighttothreee_case is
    Port ( i : in    STD_LOGIC_VECTOR (7 downto 0);
           o : out    STD_LOGIC_VECTOR (2 downto 0));
end eighttothreee_case;

architecture Behavioral of eighttothreee_case is
begin
    Process(i)
    begin
        case i is
            when "00000001" => o <= "000";
            when "00000010" => o <= "001";
            when "00000100" => o <= "010";
            when "00001000" => o <= "011";
            when "00010000" => o <= "100";
            when "00100000" => o <= "101";
            when "01000000" => o <= "110";
            when "10000000" => o <= "111";
        end case;
    end Process;
end Behavioral;
```

## Design: Decimal-to-BCD encoder

### Description

A Decimal to BCD encoder has 10 input lines and 4 output lines. If i_x is set to 1 the output is the binary equivalent of x.

### Truth Table

![alt TruthTable](https://raw.githubusercontent.com/sohammukherjee1234/LabReport/master/table2.png "Truth Table")

### Diagram

![alt Circuit Diagram](https://www.sigmatone.com/images/decimal_to_bcd.jpg "Circuit Diagram")

### Implementation

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
entity decimal_to_BCD is
    Port ( i : in    STD_LOGIC_VECTOR (9 downto 0);
           o : out    STD_LOGIC_VECTOR (3 downto 0));
end decimal_to_BCD;

architecture Behavioral of decimal_to_BCD is
begin
    o(3) <= i(9) or i(8);
    o(2) <= i(7) or i(6) or i(5) or i(4);
    o(1) <= i(7) or i(6) or i(3) or i(2);
    o(0) <= i(9) or i(7) or i(5) or i(3) or i(1);
end Behavioral;    
```

## Design: 1-to-2 Decoder

### Description

Decoder is a combinational circuit that has ‘n’ input lines and maximum of 2^n output lines. One of these outputs will be active High based on the combination of inputs present, when the decoder is enabled. That means decoder detects a particular code. A 1-to-2 decoder has 1 input lines and 2 output lines. An enable input is provided to switch the decoder on and off.

### Truth Table

![alt Truth Table](https://raw.githubusercontent.com/sohammukherjee1234/LabReport/master/table3.png "Truth Table")

### Diagram

![alt Circuit Diagram](https://www.electronicshub.org/wp-content/uploads/2015/07/1-to-2-demux.jpg "Circuit Diagram")

### Implementation

#### Using Structural Modelling

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity onetotwo_decoder is
    Port(e: in BIT;
         i: in BIT;
         o: out BIT_VECTOR(1 downto 0));
end onetotwo_decoder;

architecture Behavioral of onetotwo_decoder is
begin
    o(0) <= e and not(i);
    o(1) <= e and i;
end Behavioral;    
```

#### Using Behavioral Modelling using Concurrent Statements

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity onetotwo_decoder_conc is
    Port(e : in BIT;
         i: in BIT;
         o: out BIT_VECTOR(1 downto 0));
end onetotwo_decoder_conc;

architecture Behavioral of onetotwodecoder_conc is
begin
    with (e & i) select o <= 
        "01" when "10",
        "10" when "11",
        "00" when others;
end Behavioral        
```

#### Using Sequential Statements

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity onetotwo_decoder_sequential is
    PORT(e : in STD_LOGIC;
         i : in STD_LOGIC;
         o : out STD_LOGIC_VECTOR(1 downto 0));
end onetotwo_decoder_sequential;

architecture Behavioral of onetotwo_decoder_sequential is
begin
    process(e,i)
    begin
        if (e = '0') then o <= "00";
        elseif (i = '0') then o <= "01";
        elseif (i = '1') then o <= "10";
        end if
    end process
end Behavioral;
```

## Design: 2-to-4 decoder

### Description

A 2-to-4 decoder has 2 input lines and 4 output lines. An enable input is provided to switch the decoder on and off.

### Truth Table

![alt Truth Table](https://raw.githubusercontent.com/sohammukherjee1234/LabReport/master/table4.png "Truth Table")

### Diagram

![alt Diagram](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAXwAAACFCAMAAABv07OdAAAAflBMVEX////+/v7x8fGpqakkJCQzMzMAAADCwsLt7e2xsbHh4eErKyteXl5paWnc3Nzp6elNTU3Ly8u5ubl+fn54eHj4+PjS0tI3NzdbW1uOjo7U1NRUVFRxcXHMzMy7u7vDw8OZmZmEhIRAQEChoaGTk5MXFxceHh5FRUULCwsTExPw2EWNAAAJpElEQVR4nO1diXqyOhCdoCIgiyxB2UFs/e/7v+BNQBCrFtDUlJLTry7UpPEwDJOZyQTglwJVPyw7RMC2wz8MwhViyxVCjDv8u0CsuWJ/Nv8u2FMlJH8McLpmCB8E+YOBQNptlqywkRe8v9CUQMhflRorhDtB/ghQ8tkRxrKvGaAmH7EA4xM5AzTkM+lKkD8OLKVVSP5ICPI5QpDPEYJ8jhDkc4QgnyME+RwhyOcIQT5HCPI5QpDPEYJ8jhDkc4QgnyME+RzBh/w6U6sNIqAv7+cCHuQjdMW+ZtN3mTU77rmQj2vam/CZsvMBbF0Rkv+OvvIFgm7k0tkjaWsKtfOWvkx56+BOhi721DyYH/XsyVeHfPAoy3unI+naJpIA/MBzGI1kImBM/mGn6/pe70EkE+zURvMg8OgQ1goE5awuANbkn2KjH3tK/smpeaYZP4R8ehvAgc1oKNMAF7UTELWTtvdc8kglH4Hp5pKQ/Jf66s9SDuUo7d5wydlQ67fOcWrkP7mwpxE75tZO72hytRX5L6OxXUZDeReeXo2AgHF+5eAZ7r1jCB2zLDYnltzfnSyOasc8uXU4+bfjJcfMdWpNbqZlydFzDTmRj+4uBGtMH0ZjeRdU4yQ90awm4BeRf74SJwWsh8VT9ElFWD39FrUDMKk1vNVIzQiFe0xeSBjawQ+4fBHk/2JNBFNeAIKyBKA+QTB8GCc5aCf/8zTMbB3VzMgnVOMtnasHYHmHEFryiwGTfMPY0ab6UpD/FIh2SSLbttWIqBzXv8i92+vcIqjJ338K8p8DQpVDEEdrAM8fO9klaid+pHbQzatO6O/+f5kX+dQ40zAlxVLO5I9BKRvmN4Rp7tZIagMwKxtbEJ1NQiv2b4czL/Lrx7Np44bjXA2S+42pSTh23dKTzar7tOj8s+oEGJvsTps5kd/mAVBR9HTDGVPHAiFcPT8gDNE4NzYy2qO5kj/2xKb99Kz6/GJv7c6d/Lq+SpuJMdLQhFqNP5D8qlcl0ugrHOiOrRyC1NBxdXqPC3Bv4x7zIr+ZTDWTw5HTw/rjj8gHKvjnkIdD1E5qULvWr6YW+8TWc+u2v+FJU9+9nQ0eEkY4Vwj39RVAyVepr31P1RCKqYl6W2BklHuhrQfWvJ5hqZjHagdsw2xeOjFAcpAgPGjN/d1NBvd154OXx/o/fGPA/mE8JB+QLm8Pu6JS8ubnLsbu6rTJa0Elv/F6cF9f4WjQZdr3JKL8PFOQ3x5HaL0gWNd6J1wQfZMukvrOQg/ZNyp/MPmpXCrdW5ROGtGsKUF++4d2YnuPlLs8Ddb5sfyRa5dOzK1lbvG0HMpMwNilvPNSJ3V6kBbkdr0qrVb3l57hTDWU9QpYJ039N6Rg26aylgrctEMnakmVcVyIvJ0X+trlitULJSfUxyZuIz/g0iEoCPJBOVd/BjwiWcpG9kzoRt28c7Grozoryf+BGG4vfaWhoU4klzzGZXUOfGNqKyTQ03cp9I1v57n+BubnX7ei87lqaYQWmZO74WohfmbEzUl7f+rIF2lB57Qv21NgatYmMuTwqYYS9UvyyduBa/LrA4etF08tP9/U8+KphtgwKP08ViNeTdzQzemYDvLSPDzX0iQGX8I/aaoNSkzLsUlHjPca0hMAq1xIF3+J3Y/EDmnWiZd+JazjWID2p+P4pWEzpwkgoI7/YV7BlMpQiEzt6FKvoO1dRCr+GFL0+5NONJd3HPPu5+fKNc/qGXUez+chic6qAjVnpWo2O/Kpn0ReKVkOyLu4akOzF6GpUckvktvUEWwUqarL9rXjveN8CXW4vOl8YE7k0697oq5dQ1XJty6ScZZaIn8E2i1h1JVPnfXOSQJzJ++I8a3+kyMJSnKqJICFLG/16pgngRp7sto2nBP5RPDWMaXbiRc1+R3929sYG9Uk/y75KdCAbWhtF2ZpYHvj+IGZbNJkX4C9dMJgD9khM+MjqHKZKG3DOZHfQaN2Rki+VPtXbglDVPLJWdz7aZQ6zkmr/F5QEAnXdog+EbXjFqmTR6AGMFe1c4HkhZk7ylpG8HBNFq4kXztZ6sdutYqsuDJuipSSj12iknwdvCX5U1yRf8knnCf5CJSFKn21oL9v8mhNFs1Hy2jef0BIxoRwnJMnU1kYGMotENMKyj2N+1EvjRrM1drpoM3CGN7i4WpEhHVZ/rehsfOSWKN7RTGIRarhvSwfQrB28vIUEYvoQ/5wYVFcJhdzJf+SxTq8CapTZ24lH6Fwvc7qGizh2ib3U2xndA2LvaamlZb5ik+OJWsfg9ZxRM6V/KfBaykouvLnd+fJMwKXNVlNpn9NN67iiU+5xScOTsGU7m6k4YooM4vmwjEax2TAg/yFbl7l9QYuYGrNCvLf0Je0ugqgg7IN1/rUYlgswDx1xNLITw9o6ojRpo4gsA/VOgDQZqb4mSdNDdu/sps0Rewcvaqzo22Vedk8rCXfXae9WAe0xFqbLgjnGmu+d5pXwhpznT8k5QwZ8rK8VHchT25dY21yaTsvgkeZL0deXKWIozppCjAlf07s87B20pvUfoxb8hmNZRLgVUX85kildiQh+T/c113/HzmQxF6czEr0f0mlKTQi/vl38Hskf3ppUy9DVJriCEE+RwjyOUKQzxGCfI4Q5HOEIJ8jBPkcIcjnCEE+R/wE+T0egjpnp+PPb9Ic5+RZqPATwZS+zylBvYTm/EmxNyK7vgb4xoJloEB7lsTeiKz6GlQ2BC/l/4pLOEvsjcimr0PkDkBBK2gvC+3cbsp7I6Jn71d1A7bkH7YDEK1o3k7UVmOu90ZEC8+emvh31yyPanduwiNLeSPLxqVgxHl7vqMDxXpi5ANkdCMCb/SmNVJWXTEcbrglkXrcCPl5b0QAQ4FkatoHwWJzDIIc93/0GtjQaTHq95OvePUGI5eoLZV8SZfA9xgN5X1Y1EMeHf40ycWfoR+w81EP8NcgeqDSJZAShN7EJJ+Qv8vzvLySfNu2s57CF1mW0OX/ccp4w5oh68LuhNARGBbYAaOhvAtE7fyn7/fxlc4fVPhi86jwxdMjeekqcnLffa5sEz8Q8uPziwv6614QWFTyA/9XbNVEdZXvaFPLWLtL/iBk8sfR+iVezWauMi3uKfnyjdppq9N/A2wUdwtfvDCSV8i/l8g2AYT51xvuoO8g1SUWfwf55xqDkzN2XoIIpnCEIJ8jBPkcIcjnBzS0+PSgzgT5o0C9mrtBnsgBfQnyx4ExYYL8MajJlxRG0Ji5KmYBSv5qs9qwwYqZk24OoDpfZYnb7SoFBAQEBAQEBAR+FP8DQLmP4u/mKRUAAAAASUVORK5CYII= "Diagram")

### Implementation

#### Using Structural Modelling

```vhdl
library IEEE;
use IEEE.BIT_1164.ALL;

entity twofourdecoder is
    PORT(e: in BIT;
         i: in BIT_VECTOR(1 downto 0);
         o: out BIT_VECTOR(3 downto 0));
end twofourdecoder;

architecture Behavioral of twofourdecoder is
begin
    o(0) <= e and not(i(1)) and not (i(0));
    o(1) <= e and not(i(1)) and (i(0));
    o(2) <= e and(i(1)) and not (i(0));
    o(3) <= e and (i(1)) and (i(0));
end Behavioral;    
```

#### Using Behavioral Modelling Sequential Statements

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity two_four_decoder_sequential is
    Port(e : in STD_LOGIC;
         i : in STD_LOGIC_VECTOR(1 downto 0);
         o : out STD_LOGIC_VECTOR(3 downto 0));
end two_four_decoder_sequential;

architecture Behavioral of two_four_decoder_sequential is
begin
    process(e, i)
    begin
        if(e = '0') then o <= '0000';
        elseif(i = '00') then o <= '0001';
        elseif(i = '01') then o <= '0010';
        elseif(i = '10') then o <= '0100';
        elseif(i = '11') then o <= '1000';
        end if;
    end process;
end Behavioral;    
```

#### Using Behavioral Modelling Concurrent Statements

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity two_four_decoder_conc is 
    Port ( e : in    STD_LOGIC;
           i : in    STD_LOGIC_VECTOR (1 downto 0);
           o : out    STD_LOGIC_VECTOR (3 downto 0)); 
end two_four_decoder_conc;

architecture Behavioral of two_four_decoder_conc is 
begin
    with (e & i) select o<= 
        "0001" when "100",
        "0010" when "101",
        "0100" when "110",
        "1000" when "111",
        "0000" when others; 
end Behavioral;
```

## Design: 3-to-8 decoder

### Description

A 3-to-8 decoder has 3 input lines and 8 output lines. An enable input is provided to switch the decoder on and off.

### Truth Table

![alt Truth Table](https://raw.githubusercontent.com/sohammukherjee1234/LabReport/master/table5.png "Truth Table")

### Diagram

![alt Diagram](https://www.elprocus.com/wp-content/uploads/decoder-block-diagram.jpg "Diagram")

### Implementation

#### Using Component Instantiate
```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity three_to_eight_comp is
    Port ( inp : in STD_LOGIC_VECTOR (2 downto 0);
           en : in  STD_LOGIC;
           op : out STD_LOGIC_VECTOR (7 downto 0)); 
end three_to_eight_comp;

architecture Behavioral of three_to_eight_comp is
    component two_to_four_decoder is
        Port( e : in STD_LOGIC;
              i : in STD_LOGIC_VECTOR(1 downto 0)
              o : out STD_LOGIC_VECTOR(3 downto 0));
    end component
    
    signal notinp: STD_LOGIC;
    begin
        notinp <= not inp(2);
        dec1: two_to_four_decoder port map(inp(2),inp(1 downto 0),op(7 downto 4)); dec2: two_to_four_decoder port map(notinp,inp(1 downto 0),op(3 downto 0));
end Behavioral;        
```

#### Using Procedural Statement

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity three_to_eight_proc is
    Port ( inp : in STD_LOGIC_VECTOR (2 downto 0); 
           op : out STD_LOGIC_VECTOR (7 downto 0));
end three_to_eight_proc;

architecture Behavioral of three_to_eight_proc is
procedure two_to_four_decoder
            (e : in STD_LOGIC (1 downto 0);
             o : out STD_LOGIC_VECTOR(3 downto 0)) is
begin
    with (e&i) select o <= 
        "0001" when "100",
        "0010" when "101",
        "0100" when "110",
        "1000" when "111",
        "0000" when others;
end procedure;

begin 
    process(inp)
    variable temp_var: STD_LOGIC_VECTOR(7 downto 0);
    begin
        dec1: two_to_four_decoder(inp(2), inp(1 downto 0), temp_var(7 downto 4));
        dec2: two_to_four_decoder(not inp(2), inp(1 downto 0), temp_var(3 downto 0));
        op <= temp_var;
    end process;
end Behavioral;
```





