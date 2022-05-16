package tictactoe
fun main() {
    val list1 : MutableList<Char> = mutableListOf(' ',' ',' ',' ',' ',' ',' ',' ',' ')
    var temp = 1
    var result:String
    var flag:Int =0
    var row1 :String; var row2 :String; var row3 :String
    var xWin :Boolean; var oWin :Boolean
    do{
        display(list1)
        row1 = (list1.subList(0,3)).joinToString("")
        row2 = (list1.subList(3,6)).joinToString("")
        row3 = (list1.subList(6,9)).joinToString("")
        xWin = checkWin("XXX", 'X', row1, row2, row3)
        oWin = checkWin("OOO", 'O', row1, row2, row3)
        val a:(Char) -> Boolean = {it=='X'}
        val xcount = list1.count(a)
        val b:(Char) -> Boolean = {it=='O'}
        val ocount = list1.count(b)
        if((xcount-ocount >=2)||(xcount-ocount<=-2) || xWin && oWin)
            result="Impossible"
        else if(xWin && !oWin)
            result="X wins"
        else if(!xWin && oWin)
            result= "O wins"
        else if(list1.contains(' ')||list1.contains('_'))
            result="Game not finished"
        else
            result="Draw"
        if(result!="Game not finished")
            break
        flag=0
        while(flag==0){
            println("Enter the coordinates")
            var(a,b) = readln().split(' ')
            if(!(a[0].isDigit() && a.length==1) || !(b[0].isDigit() && b.length==1)){
                println("You should enter numbers!")
                continue
            }
            val x=a.toInt()
            val y=b.toInt()
            if(!(x in 1..3)||!(y in 1..3)){
                println("Coordinates should be from 1 to 3!")
                continue
            }
            else if(!(checkSpace(x,y,list1))){
                println("This cell is occupied! Choose another one!")
                continue
            }
            else{
                firstMove(x,y,list1,temp)
                flag=1
            }
        }
        temp++
    }
    while(result=="Game not finished")
    println(result)
}
fun display(list1: MutableList<Char>){
    var k=0
    println("---------")
    for(i in 0..2){
        println("| ${list1[i+k]} ${list1[i+k+1]} ${list1[i+k+2]} |")
        k+=2
    }
    println("---------")
}
fun checkWin(a: String, b: Char, row1: String, row2: String, row3: String): Boolean{
    var win= (row1 == a || row2 == a || row3 == a)
    for(i in 0..2){
        if(row1[i]== b && row2[i]== b && row3[i]== b){
            win = true
            break
        }
    }
    if((row1[0]== b && row2[1]== b &&row3[2]== b)||(row1[2]== b && row2[1]== b &&row3[0]== b)){
        win = true
    }
    return win
}
fun firstMove(a:Int,b:Int,list1: MutableList<Char>, temp: Int){
    if(temp % 2 == 0)
        list1[((a-1)*3)+b-1] = 'O'
    else
        list1[((a-1)*3)+b-1] = 'X'
    display(list1)
}
fun checkSpace(a:Int,b:Int,list1: MutableList<Char>):Boolean{
    return (list1[((a-1)*3)+b-1]==' '||list1[((a-1)*3)+b-1]=='_')
}
