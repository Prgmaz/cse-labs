## Bit stuffing and destuffing program
```
inp = input("Enter bit sequence (without spaces): ")
inp = list(map(int, inp))

def bit_stuffing(inp):
    count = 0
    out = list()
    for i in range(len(inp)):
        out.append(inp[i])
        if inp[i] == 1:
            count += 1
        else:
            count = 0
        if count == 5:
            out.append(0)
            count = 0
        
    return out
    

def bit_destuffing(inp):
    count = 0
    out = list()
    for i in range(len(inp)):
        if count == 5:
            count = 0
            continue
        out.append(inp[i])
        if inp[i] == 1:
            count += 1
        else:
            count = 0
        
    return out

bit_stuffed = bit_stuffing(inp)
bit_unstuffed = bit_destuffing(bit_stuffed)
print("Bit Stuffing:", bit_stuffed)
print("Bit Destuffing:", bit_unstuffed)
```

## Output
![Output](https://raw.githubusercontent.com/Programmer101N/cse-labs/master/Computer%20Networks/bit_stuffing_and_destuffing.png)
