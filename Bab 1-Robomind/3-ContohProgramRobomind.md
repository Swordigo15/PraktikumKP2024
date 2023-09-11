[<<Materi Sebelumnya(Robomind Programming Structures)](2-ProgrammingStructures.md)
# 1.2 - Robomind Programming structures

## Contoh 1 : Menuliskan Nama

```py
#character 'A'
paintWhite()


forward(2)
right()
forward(1)
right()
forward(2)
backward(1)
right()
forward(1)

stopPainting()
```


## Contoh 2 : Mencari Titik Putih

File : findSpot1.map

```py
repeat(){
    if(leftIsWhite()){
        # There's a white spot on your left
        left()
        forward(1)
        end
    }
    else{
        # There's no white spot yet
        forward(1)
    }
}
```

## Contoh 3 : Mengikuti Garis

File : default.map

```py
# Go to the start of the line
right()
forward(8)


# Keep on track step by step
repeat()
{
    if(frontIsWhite()){	
        forward(1)
    }
    else if(rightIsWhite()){
        right()
    }
    else if(leftIsWhite()){
        left()
    }
    else if(frontIsObstacle()){
        end
    }
}
```

# Contoh 4 : Labirin

File : maze1.map

```py
repeat(){	
    if(rightIsObstacle()){
        if(frontIsClear()){
            forward(1)
        }
        else{
            left()
        }
    }
    else{
        right()
        forward(1)
    }

    if(frontIsBeacon()){	
        pickUp()
        end
    }
}
```
