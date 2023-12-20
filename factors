#!/usr/bin/env bash
# is a factors challenge

check_factor()
{
	if [ $# -ne 3 ];
        then
                args=("$@")
                count=0
                num2=1
                for a in ${args[*]};
                do
                        if [ $count -gt 1 ];
                        then
                                num2=$(echo $a*$num2 | bc)
                        fi
                        count=$((count + 1))
                done
        else
                num2=$3
        fi

        num1=$2
        num=$(echo "$1" | tr ':' '=')

        result=$(echo "if($num2 > $num1) 1 else 0" | bc)
	        if ((result == 1)); then
		        numcp=$num1
		        num1=$num2
		        num2=$numcp
                fi

        echo "$num$num1*$num2"
}

if [ $# -ne 1 ]
then
        echo 'Usage: factors <file>'
        exit 1
else

        while read i
        do

                result=$(factor "$i")
                check_factor $result

        done < "$1"
fi
