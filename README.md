# COM.SQLite — sqlite.net.dll
### Оглавление
[Назначение](#Назначение)  
[Регистрация COM-сервера в реестре Windows](#Регистрация-COM-сервера-в-реестре-Windows)  
[Создание объекта COM.SQLite](#Создание-объекта-COMSQLite)  
### Назначение
Библиотека sqlite.net.dll реализует COM-сервер для VFP9 или VFPA, который в принципе может использоваться и в любых других языках, поддерживающих COM технологию обмена данными.  

Microsoft VFP имеет ограничение на размер файла БД и на количество записей в нем. Отчасти проблему размера файла dbf решает VFPA,
но проблема максимального числа записей в файле приблизительно до 1 миллиарда записей — не решима. К тому же чтобы получить на
сегодняшний день VFPA нужно оформлять платную подписку. Многие разработчики уже перешли на другие СУБД и в том числе на SQLite.
Данный COM позволяет использовать БД SQLite на языке VFP и других языках Windows, например на JScript платформы WSH. 

При создании COM-объекта COM.SQLite, файл sqlite3.dll с API от разработчика SQLite.org должен находиться рядом с файлом sqlite32.net.dll
или sqlite.net.dll в зависимости от разрядности sqlite3.dll и разрядности программы, которую вы разрабатываете. В случае с VFP могут
быть 32-х битная VFP9 и 64-х битная VFPA.  

В COM.SQLite реализованы методы Open(), DoCmd(), DoCmd1(), DoCmd2(), DoCmd3(), DoCmd4 (), DoCmd5(), DoCmd6(), DoCmd7(), DoCmd8(),
DoCmd9(), DoCmdN(), Next(), Eof() и Close(). В стадии разработки метод копирования БД.
### Регистрация COM.SQLite в реестре Windows
#### Для VFPA и другого 64-х разрядного ПО
Чтобы объект COM.SQLite был доступен в разрабатываемых программах 64-х битных версий, его нужно зарегистрировать в ОС с помощью
утилиты regasm.exe. Например:
```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\regasm.exe D:\VFP\VFPA\sqlite.net.dll /codebase
```
Предварительно поместите файл sqlite.net.dll в удобную для вас папку, например, в папку, где находятся другие библиотеки Microsoft VFP.  
Для удаления регистрации из Windows используйте ключ /unregister. Например:
```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\regasm.exe D:\VFP\VFPA\sqlite.net.dll /unregister
```
Для выполнения вышеуказанных команд требуются права администратора.
#### Для VFP9 и другого 32-х разрядного ПО
Используйте утилиту регистрации для 32-х разрядных программ, находящуюся по другому пути:
C:\Windows\Microsoft.NET\Framework\v4.0.30319\regasm.exe. Команды на регистрацию и удаление регистрации аналогичны командам
для 64-х разрядного ПО. Например, регистрация:
```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\regasm.exe D:\VFP\VFP9\sqlite32.net.dll /codebase
```
и удаление регистрации:
```
C:\Windows\Microsoft.NET\Framework\v4.0.30319\regasm.exe D:\VFP\VFP9\sqlite32.net.dll /unregister
```
