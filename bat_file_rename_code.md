# 下列均为复制代码于新建的记事本而后保存ANSI格式的.bat文件双击运行

# for中*.*后面的*表示任意后缀名的文件，%%~nf表示获取文件名，%%~xf表示获取后缀名， a为递增序列号
set a=0 
setlocal EnableDelayedExpansion
for /f "delims=" %%f in ('dir /a /b *.*') do ( 
   if not "%%~nxf"=="%%~nx0" (
          set /A a+=1
          ren "%%f" "文件批量修改前缀名!a!%%~xf"
   )
）
pause

# 批量去文件名字
setlocal enabledelayedexpansion
for /f "delims=" %%i in ('dir /a /b *要求掉的文件名*‘) do (
   set var%%i
   set var=!var:要求去掉的文件名 =!
   ren "%%i" "!var!"
)
pause

# 批量修改文件名的复杂情况

# 下列代码为新建Exel文件将要修改的名字录入其中保存为list.csv

DIR *.* /B > list.csv

# 在csv中要添加的文件名后一格加 
=”ren "&A1&" "&B1&C1&“.docx"
# 批量拉取识别而后复制到新的bat文件运行