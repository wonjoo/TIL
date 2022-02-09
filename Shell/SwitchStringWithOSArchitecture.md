# SwitchStringWithOSArchitecture

## 목표
OS 아키텍처가 M1일 때 지정 파일의 string값 변환

## 코드 ##
~~~shell
#!/bin/zsh
 
 # OS 아키텍처 확인 Intel or M1
arch_name="$(uname -m)"

old_txt='oldtxt'
new_txt='newtxt'
 
 
if [ "${arch_name}" = "x86_64" ]; then
    if [ "$(sysctl -in sysctl.proc_translated)" = "1" ]; then
        echo "Running on Rosetta 2"
    else
        echo "Running on native Intel"
    fi 
elif [ "${arch_name}" = "arm64" ]; then
    echo "Running on ARM"
    # M1일때 filename.txt 파일 안의 특정 문구 변경
    sed -i -e "s/${old_txt}/${new_txt}/g" filename.txt
else
    echo "Unknown architecture: ${arch_name}"
fi
~~~
