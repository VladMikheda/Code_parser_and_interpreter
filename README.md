# Parcer a interpret kódu IPPcode22

## Parser
Převádí kód napsaný v jazyce IPPcode22 do XML formatu. Kód se načítá ze standardního vstupu.

### Příklady spuštění 
```
php8.1 parse.php
```
nebo
```
php8.1 parse.php < file
```
pro zobrazeni informace 
```
php8.1 parse.php --help 
```

## Interpret
Interpretuje kód převedeny do XML formátu a generuje vystup.


### Parametry
+ --help pro zobrazení informací  
+ --source=file vstupní soubor s XML reprezentací zdrojového kódu  
+ --input=file soubor se vstupy pro samotnou interpretaci zadaného zdrojového kódu.

Alespoň jeden z parametrů (--source nebo --input) musí být vždy zadán. Pokud jeden z nich
chybí, jsou chybějící data načtěna ze standardního vstupu.
### Příklady spuštění 
```
python interpret.py --source=kode.xml --input=vystup.out
```

## Test
Skript je určen pro testování parseru a interpretu, skript generuje výstup v HTML formátu. 

### Parametry 
+ --help pro zobrazení informací  
+ --directory=path testy se budou hledat v zadaném adresáři (chybí-li tento parametr, skript
prochází aktuálním adresářem )  
+ --recursive testy se budou hledat nejen v zadaném adresáři, ale i rekurzivně ve všech jeho
podadresářích    
+ --parse-script=file soubor se skriptem v PHP 8.1 pro analýzu zdrojového kódu v IPPcode22 (chybí-li tento parametr, implicitní hodnotou je parse.php uložený v aktuálním adresáři)   
+ --int-script=file soubor se skriptem v Python 3.8 pro interpret XML reprezentace kódu
v IPPcode22 (chybí-li tento parametr, implicitní hodnotou je interpret.py uložený v aktuálním adresáři)   
+ --parse-only bude testován pouze skript pro analýzu zdrojového kódu v IPPcode22 (tento
parametr se nesmí kombinovat s parametry --int-only a --int-script), výstup s referenčním
výstupem (soubor s příponou out).   
+ --int-only bude testován pouze skript pro interpret XML reprezentace kódu v IPPcode22 (tento parametr se nesmí kombinovat s parametry --parse-only, --parse-script
a --jexampath). Vstupní program je reprezentován pomocí XML bude v souboru s příponou
src.   
+ --jexampath=path cesta k adresáři obsahující soubor jexamxml.jar s JAR balíčkem s nástrojem A7Soft JExamXML a soubor s konfigurací jménem options. Je-li parametr vynechán,
uvažuje se implicitní umístění /pub/courses/ipp/jexamxml/ na serveru Merlin, kde bude
test.php hodnocen. Koncové lomítko v path je případně nutno doplnit.   
+ --noclean během činnosti test.php nebudou mazány pomocné soubory s mezivýsledky, tj.
skript ponechá soubory, které vznikají při práci testovaných skriptů (např. soubor s výsledným
XML po spuštění parse.php atd.).

### Příklady spuštění 
```
# spuštění pro testováni dvou skript
# s zachováním mezivýsledků
php8.1 directory=./tests --recursive  --jexampath=./jexampath --noclean
```


## Zadaní 
Navrhněte, implementujte, dokumentujte a testujte sadu skriptů pro interpretaci nestrukturovaného
imperativního jazyka IPPcode22. K implementaci vytvořte odpovídající stručnou programovou dokumentaci. Projekt se skládá ze dvou úloh a je individuální.
První úloha se skládá ze skriptu parse.php v jazyce PHP 8.1 a dokumentace
k tomuto skriptu. Druhá úloha se skládá ze skriptu interpret.py v jazyce Python
3.8, testovacího skriptu test.php v jazyce PHP 8.1 a dokumentace těchto
dvou skript.