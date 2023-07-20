# C-p51-2-
C语言学习笔记 p51 字符函数&amp;内存函数使用和剖析(2)
#include<stdio.h>
#include<string.h>
//strtok库函数函数原型参数：char* strtok(char* str,const char* sep);
//sep参数是个字符串，定义了用作分隔符的字符集合
//注：strtok库函数一般是用来切割临时拷贝出来的数据
int mian()
{
    //192.168.31.121
    //192 168 31 121 - strtok
    //zpw@bitedu.tech
    //zpw bitede tech
    char arr[]="zpw@bitedu.tech";
    char* p="@.";

    char buf[1024]={0};
    strcpy(buf,arr);
    //切割buf中的字符串

    char* ret=NULL;
    for(ret=strtok(arr,p);ret!=NULL;ret=strtok(NULL,p))
    {
        printf("%s\n",ret)
    }
    
    //char* ret=strtok(arr,p);
    //printf("%s\n",ret);
    //ret=strtok(NULL,p);
    //printf("%s\n",ret);
    //ret=strtok(NULL,p);
    //printf("%s\n",ret);
    return 0;
}


#include<errno.h>
//strerror库函数原型参数：char* strerror(int errnum);
//作用：返回错误码，所对应的错误信息
int main()
{
    //错误码  错误信息
    //0    - No error
    //1    - Operation not permitted
    //2    - No such file or directory
    //...
    //errno是一个全局的错误码的变量
    //当c语言的库函数在执行过程中，发生了错误，就会把对应的错误码，赋值到errno中
    char* str=strerror(errno);
    printf("%s\n",str);
    return 0;
}

int main()
{
    //打开文件
    FILE* pf=fopen("test.txt","r");
    if(pf==NULL)
    {
        printf("%s\n",strerror(srrno));
    }
    else
    {
        printf("open file success\n");
    }
    return 0;
}

#include<ctype.h>//字符分类函数
int main()
{
    char ch='w';
    //int ret=islower(ch);//判断ch是否为小写字符
    int ret=isdigit(ch);//判断是否为数字符
    printf("%d\n",ret);
    return 0;
}

int main()
{
    char ch=tolower('Q');//大写改小写
    putchar(ch);
    return 0;
}//输出q

int main()
{
    char arr[]="I Am A Student";
    int i=0;
    while(arr[i])
    {
        if(isupper(arr[i]))
        {
            arr[i]=tolower(arr[i]);
        }
        i++;
    }
    printf("%s\n",arr);
    return  0;
}
