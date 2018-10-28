#!/bin/bash
 
#guess number game;
init()
{
echo " ################################### "
echo "                                     "
echo "        Guess Number Game            "
echo "                                     "
echo " ################################### "
}
number=$[$RANDOM%100]
game()
{
while :
do
read -p "输入你要猜测的数字: " n1
n2=`echo $n1 | sed 's/[0-9]//g'`
if [ ! -z $n2 ]
    then
        echo "你输入的不是一个数字."
        continue
fi
if [ $n1 == $number ]
    then
        echo "你猜对了."
	echo -e "\033[41m you are winner"
	echo -e "\033[42m you are winner"
	echo -e "\033[43m you are winner"
	echo -e "\033[44m you are winner"
	echo -e "\033[45m you are winner"
	echo -e "\033[46m you are winner"
	activity
        read -p "你还想再玩一次么？（yes/no）" an1
        while true
                do
                        case $an1 in
                        yes)
                        game
                        break
                        ;;
                        no)
                        break
                        ;;
                        *)
                        exit
                        esac
        done
        break
    elif [ $n1 -gt $number ]
    then
        echo "猜大了."
        continue
    else
        echo "猜小了."
        continue
    fi
done
}
 
activity()
{
	read number
	i=1
	c=1
	while [ $i -le $n ]
	do
	i=$(expr $i + 1)
	r=$(expr $number % $i)
	if [ $r -eq 0 ]
	then
	c=$(expr $c + 1)
	fi
	done
	if [ $c -eq 2 ]
	then
	echo “Prime”
	else
	echo “Not Prime”
	fi
}


while true
do
init
echo "1: 游戏开始 "
echo "0: 游戏退出 "
read -p " please input 0-1:" NUM
 
case $NUM in
1)
	game
	break
        ;;
0)
        break
        ;;

esac
 
done
