---
title: Resgen.exe (generátor zdrojových souborů)
ms.date: 03/30/2017
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
ms.openlocfilehash: cf79e7c76fd54c6cb6b235251a57aba33c28552b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180336"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (generátor zdrojových souborů)
Nástroj Resource File Generator (Resgen.exe) převádí textové soubory (.txt nebo .restext) a soubory ve formátu prostředků založeném na jazyce XML (.resx) na binární soubory modulu CLR (.resources), které mohou být vloženy do binárního spustitelného souboru modulu nebo satelitního sestavení. (Viz [Vytváření souborů prostředků](../resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe je univerzální nástroj pro převod prostředků, který plní následující úlohy:  
  
- Převádí soubory .txt nebo .restext na soubory .resources nebo .resx. (Formát souborů .restext je shodný s formátem souborů .txt. Přípona .restext však usnadňuje identifikaci textových souborů obsahujících definici prostředků.)  
  
- Převádí soubory .resources na textové soubory nebo soubory .resx.  
  
- Převádí soubory .resx na textové soubory nebo soubory .resources.  
  
- Extrahuje prostředky řetězce ze sestavení do souboru Resw, který je vhodný pro použití v aplikaci pro Windows 8.x Store.  
  
- Vytvoří třídu silného typu, která poskytuje přístup <xref:System.Resources.ResourceManager> k jednotlivým pojmenovaným prostředkům a k instanci.  
  
 Pokud nástroj Resgen.exe z jakéhokoli důvodu selže, je návratová hodnota –1.  
  
 Chcete-li získat pomoc s resgen.exe, můžete použít následující příkaz, bez zadaných možností, k zobrazení syntaxe příkazu a možností pro resgen.exe:  
  
```console  
resgen  
```  
  
 Můžete také použít `/?` přepínač:  
  
```console  
resgen /?  
```  
  
 Pokud používáte resgen.exe ke generování binárních souborů .resources, můžete použít kompilátor jazyka k vložení binárních souborů do spustitelných sestavení nebo můžete použít [propojovací modul sestavení (Al.exe)](al-exe-assembly-linker.md) ke kompilaci do satelitních sestavení.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr nebo přepínač|Popis|  
|-------------------------|-----------------|  
|`/define:`*symbol1*[, *symbol2*,...]|Počínaje rozhraním .NET Framework 4.5 podporuje podmíněnou kompilaci v souborech prostředků založených na textu (.txt nebo .restext). Pokud *symbol* odpovídá symbolu obsaženému ve vstupním textovém souboru v `#ifdef` rámci konstrukce, přidružený prostředek řetězce je zahrnut do souboru .resources. Pokud vstupní textový soubor `#if !` obsahuje příkaz se symbolem, `/define` který není definován přepínačem, přidružený prostředek řetězce je zahrnut do souboru prostředků.<br /><br /> `/define`je ignorována, pokud se používá s netextovými soubory. Rozlišují se malá a velká písmena.<br /><br /> Další informace o této možnosti naleznete [v tématu Podmíněné kompilace prostředků](#Conditional) dále v tomto tématu.|  
|`useSourcePath`|Určuje, že k vyhodnocení relativních cest k souborům má být použit aktuální adresář vstupního souboru.|  
|`/compile`|Umožňuje zadat několik textových souborů nebo souborů .resx pro převod na několik souborů .resources jednou hromadnou operací. Pokud tuto možnost nezadáte, lze zadat pouze jeden argument vstupního souboru. Výstupní soubory se nazývají *.resources.*<br /><br /> Tuto možnost nelze s `/str:` touto volbou použít.<br /><br /> Další informace o této možnosti naleznete v [tématu Kompilace nebo převod více souborů](#Multiple) dále v tomto tématu.|  
|`/r:` `assembly`|Odkazuje na metadata z určeného sestavení. Používá se při převodu souborů .resx a umožňuje nástroji Resgen.exe serializovat a deserializovat prostředky objektů. Je podobný `/reference:` možnosti `/r:` nebo pro kompilátory jazyka C# a Visual Basic.|  
|`filename.extension`|Určuje název vstupního souboru, který má být převeden. Pokud používáte první, delší syntaxi příkazového řádku prezentovanou před touto tabulkou, `extension` musí být jedna z následujících možností:<br /><br /> .txt nebo .restext<br /> Textový soubor, který má být převeden na soubor .resources nebo .resx. Textové soubory mohou obsahovat pouze řetězcové prostředky. Informace o formátu souboru naleznete v části Zdroje v textových souborech v části [Vytváření souborů prostředků](../resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Soubor prostředků založený na jazyce XML, který má být převeden na soubor .resources nebo textový soubor (.txt nebo .restext).<br /><br /> .resources<br /> Binární soubor prostředků, který má být převeden na soubor .resx nebo textový soubor (.txt nebo .restext).<br /><br /> Pokud používáte druhou, kratší syntaxi příkazového řádku `extension` uvedenou před touto tabulkou, musí být následující:<br /><br /> .exe nebo .dll<br /> Sestavení rozhraní .NET Framework (spustitelné nebo knihovny), jehož prostředky řetězce mají být extrahovány do souboru .resw pro použití při vývoji aplikací pro Windows 8.x Store.|  
|`outputFilename.extension`|Určuje název a typ souboru prostředků, který má být vytvořen.<br /><br /> Při převodu ze souboru .txt, .restext nebo .resx na soubor .resources je tento argument nepovinný. Pokud nezadáte `outputFilename`, resgen.exe připojí příponu .resources k vstupu `filename` a zapíše soubor do adresáře, který obsahuje `filename,extension`.<br /><br /> Argument `outputFilename.extension` je povinný při převodu ze souboru .resources. Při převodu souboru .resources na soubor prostředků založený na jazyce XML zadejte název souboru s příponou .resx. Při převodu souboru .resources na textový soubor zadejte název souboru s příponou .txt nebo restext. Soubor .resources by měl být na soubor .txt převeden pouze v případě, že soubor .resources obsahuje výhradně řetězcové hodnoty.|  
|`outputDirectory`|Pro aplikace pro Windows 8.x Store určuje adresář, ve kterém `filename.extension` bude zapsán soubor Resw, který obsahuje prostředky řetězce. `outputDirectory`již musí existovat.|  
|`/str:` `language[,namespace[,classname[,filename]]]`|Vytvoří soubor třídy prostředků silného typu v `language` programovacím jazyce určeném v možnosti. `language`se může skládat z jednoho z následujících literálu:<br /><br /> - Pro C#: `c#`, `cs`, nebo `csharp`.<br />- Pro jazyk `vb` `visualbasic`Visual Basic: nebo .<br />- Pro VBScript: `vbs` nebo `vbscript`.<br />- Pro C++: `c++`, `mc`, nebo `cpp`.<br />- Pro JavaScript: `js`, `jscript`, nebo `javascript`.<br /><br /> Tato `namespace` možnost určuje výchozí obor názvů projektu, `classname` tato možnost určuje název generované třídy a `filename` tato možnost určuje název souboru třídy.<br /><br /> Tato `/str:` možnost umožňuje pouze jeden vstupní soubor, `/compile` takže jej nelze použít s možností.<br /><br /> Pokud `namespace` je `classname` zadán, ale není, název třídy je odvozen od názvu výstupního souboru (například podtržítka jsou nahrazena tečkami). Prostředky se silnými typy možná důsledkem toho nebudou fungovat správně. Chcete-li se tomuto problému vyhnout, zadejte název třídy i název výstupního souboru.<br /><br /> Další informace o této možnosti naleznete v [tématu Generování třídy prostředků silného typu](#Strong) dále v tomto tématu.|  
|`/publicClass`|Vytvoří třídu prostředků se silnými typy jako veřejnou třídu. Ve výchozím nastavení je `internal` třída prostředků `Friend` v jazyce C# a v jazyce Visual Basic.<br /><br /> Tato možnost je ignorována, pokud tato možnost není použita. `/str:`|  
  
## <a name="resgenexe-and-resource-file-types"></a>Nástroj Resgen.exe a typy souborů prostředků  
 Aby nástroj Resgen.exe mohl úspěšně převádět prostředky, textové soubory a soubory .resx, musí dodržovat správný formát.  
  
### <a name="text-txt-and-restext-files"></a>Textové soubory (.txt a .restext)  
 Textové soubory (.txt nebo .restext) mohou obsahovat výhradně řetězcové prostředky. Řetězcové prostředky jsou užitečné při psaní aplikace, která musí mít řetězce přeloženy do několika jazyků. Lze například snadno lokalizovat řetězce nabídky použitím příslušného řetězcového prostředku. Nástroj Resgen.exe čte textové soubory obsahující dvojice název/hodnota, kde název je řetězec popisující prostředek a hodnota je samotný řetězec prostředku.  
  
> [!NOTE]
> Informace o formátu souborů TXT a restext naleznete v části Zdroje v textových souborech v části [Vytváření souborů prostředků](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Neobsahuje-li textový soubor s prostředky pouze znaky z rozsahu základní latinky (do U+007F), musí být uložen s kódováním UTF-8 nebo Unicode (UTF-16). Při zpracovávání textového souboru uloženého s kódováním ANSI nástroj Resgen.exe odstraňuje rozšířené znaky ANSI.  
  
 Nástroj Resgen.exe kontroluje, zda textový soubor obsahuje duplicitní názvy prostředků. Obsahuje-li textový soubor duplicitní názvy prostředků, nástroj Resgen.exe vygeneruje upozornění a bude ignorovat druhou hodnotu.  
  
### <a name="resx-files"></a>Soubory .resx  
 Formát souboru prostředků .resx sestává ze záznamů jazyka XML. Uvnitř těchto záznamů jazyka XML lze zadávat řetězcové prostředky jako v textových souborech. Hlavní výhodou souborů .resx oproti textovým souborům je možnost zadávat nebo vkládat objekty. Při zobrazení souboru .resx lze vidět binární podobu vloženého objektu (například obrázku), pokud je tato binární informace součástí manifestu prostředku. Stejně jako textové soubory lze i soubory .resx otevřít v textovém editoru (například Poznámkový blok nebo Microsoft Word) a zapisovat, analyzovat či upravovat jejich obsah. To vyžaduje dobrou znalost značek XML a struktury souboru .resx. Další podrobnosti o formátu souboru Resx naleznete v části Zdroje v souborech RESX v části [Vytváření souborů prostředků](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Chcete-li vytvořit soubor .resources, který obsahuje vložené objekty neřetězci, musíte buď použít resgen.exe k převodu souboru RESX obsahujícího objekty nebo přidat prostředky objektu do souboru přímo z kódu voláním metod poskytovaných <xref:System.Resources.ResourceWriter> třídou.  
  
 Obsahuje-li soubor .resx nebo .resources objekty a použijete-li nástroj Resgen.exe k jeho převodu na textový soubor, všechny řetězcové prostředky budou převedeny správně, ale datové typy neřetězcových objektů budou do souboru také zapsány jako řetězce. Během převodu dojde ke ztrátě vložených objektů a nástroj Resgen.exe oznámí, že při načítání prostředků došlo k chybě.  
  
### <a name="converting-between-resources-file-types"></a>Převod mezi typy souborů prostředků  
 Při převádění mezi různými typy souborů prostředků nástroj Resgen.exe nemusí být schopen převod provést nebo může ztratit informace o určitých prostředcích v závislosti na zdrojovém a cílovém typu souboru. Následující tabulka obsahuje typy převodů, které jsou při převádění jednoho typu souboru prostředků na jiný úspěšné.  
  
|Převod z|Na textový soubor|Na soubor .resx|Na soubor .resw|Na soubor .resources|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Textový soubor (.txt nebo .restext)|--|Žádné problémy|Nepodporuje se|Žádné problémy|  
|Soubor .resx|Obsahuje-li soubor neřetězcové prostředky (včetně odkazů na soubory), převod se nezdaří.|--|Nepodporuje se|Žádné problémy|  
|Soubor .resources|Obsahuje-li soubor neřetězcové prostředky (včetně odkazů na soubory), převod se nezdaří.|Žádné problémy|Nepodporuje se|--|  
|Sestavení .exe nebo .dll|Nepodporuje se|Nepodporuje se|Pouze řetězcové prostředky (včetně názvů cest) jsou rozpoznány jako prostředky|Nepodporuje se|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Provádění konkrétních úloh nástroje Resgen.exe  
 Resgen.exe můžete použít různými způsoby: zkompilovat textový soubor prostředků nebo soubor prostředků založený na jazyce XML do binárního souboru, převést mezi formáty souborů prostředků a generovat třídu, která obtéká <xref:System.Resources.ResourceManager> funkce a poskytuje přístup k prostředkům. Tato část poskytuje podrobné informace o každém úkolu:  
  
- [Kompilace prostředků do binárního souboru](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Převod mezi typy souborů prostředků](resgen-exe-resource-file-generator.md#Convert)  
  
- [Kompilace nebo převod více souborů](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Exportování prostředků do souboru .resw](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Podmíněná kompilace prostředků](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generování třídy prostředků se silnými typy](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>
### <a name="compiling-resources-into-a-binary-file"></a>Kompilace prostředků do binárního souboru  
 Nejběžnější použití nástroje Resgen.exe je kompilování textového souboru prostředků (soubor .txt nebo .restext) nebo souboru prostředků založeného na jazyce XML (soubor .resx) do binárního souboru .resources. Výstupní soubor pak může být vložen do hlavního sestavení kompilátorem jazyka nebo v satelitním sestavení [linkerem sestavení (AL.exe).](al-exe-assembly-linker.md)  
  
 Syntaxe pro kompilaci souboru prostředků je následující:  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 kde parametry jsou:  
  
 `inputFilename`  
 Název kompilovaného souboru prostředků (včetně přípony). Nástroj Resgen.exe kompiluje pouze soubory s příponami .txt, .restext nebo .resx.  
  
 `outputFilename`  
 Název výstupního souboru Pokud jej vynechete `outputFilename`, program Resgen.exe vytvoří `inputFilename` soubor .resources `inputFilename`s názvem kořenového souboru ve stejném adresáři jako . Pokud `outputFilename` obsahuje cestu k adresáři, musí adresář existovat.  
  
 Souboru .resources je poskytován plně kvalifikovaný obor názvů jeho zadáním v názvu souboru a oddělením od názvu kořenového souboru tečkou. Například pokud `outputFilename` `MyCompany.Libraries.Strings.resources`je , obor názvů je MyCompany.Libraries.  
  
 Následující příklad přečte dvojice název/hodnota v souboru Resources.txt a zapíše binární soubor .resources pojmenovaný Resources.resources. Soubor dostane dle výchozího nastavení název shodný s názvem vstupního souboru, protože název výstupního souboru nebyl explicitně zadán.  
  
```console  
resgen Resources.txt
```  
  
 Následující příkaz přečte dvojice název/hodnota v souboru Resources.restext a zapíše binární soubor .resources pojmenovaný StringResources.resources.  
  
```console  
resgen Resources.restext StringResources.resources  
```  
  
 Následující příkaz přečte vstupní soubor založený na jazyce XML pojmenovaný Resources.resx a zapíše binární soubor .resources pojmenovaný Resources.resources.  
  
```console  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>
### <a name="converting-between-resource-file-types"></a>Převod mezi typy souborů prostředků  
 Kromě kompilování textových souborů prostředků nebo souborů prostředků založených na jazyce XML do binárních souborů .resources dokáže nástroj Resgen.exe také převést libovolný podporovaný typ souboru na libovolný jiný podporovaný typ. To znamená, že může provést následující převody:  
  
- Soubory .txt a .restext na soubory .resx.  
  
- Soubory .resx na soubory .txt a .restext.  
  
- Soubory .resources na soubory .txt a .restext.  
  
- Soubory .resources na soubory .resx.  
  
 Syntaxe je shodná se syntaxí uvedenou v předchozí části.  
  
 Kromě toho můžete použít resgen.exe k převodu vložených prostředků v sestavení rozhraní .NET Framework na aplikace .resw file tor Windows 8.x Store.  
  
 Následující příkaz přečte binární soubor prostředků Resources.resources a zapíše výstupní soubor založený na jazyce XML pojmenovaný Resources.resx.  
  
```console  
resgen Resources.resources Resources.resx  
```  
  
 Následující příkaz přečte vstupní textový soubor StringResources.txt a zapíše soubor prostředků založený na jazyce XML pojmenovaný LibraryResources.resx. Kromě řetězcových prostředků může být soubor .resx použit také pro uchování neřetězcových prostředků.  
  
```console  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Následující dva příkazy přečtou vstupní soubor prostředků založený na jazyce XML pojmenovaný Resources.resx a zapíší textové soubory pojmenované Resources.txt a Resources.restext. Pokud soubor .resx obsahuje jakékoli vložené objekty, nebudou do textových souborů převedeny přesně.  
  
```console  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>
### <a name="compiling-or-converting-multiple-files"></a>Kompilace nebo převod více souborů  
 `/compile` Přepínač můžete použít k převodu seznamu souborů prostředků z jednoho formátu do druhého v jedné operaci. Syntaxe je:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Následující příkaz zkompiluje tři soubory, StringResources.txt, TableResources.resw a ImageResources.resw, do oddělených souborů .resources pojmenovaných StringResources.resources, TableResources.resources a ImageResources.resources.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>
### <a name="exporting-resources-to-a-resw-file"></a>Exportování prostředků do souboru .resw  
 Pokud vyvíjíte aplikaci pro Windows 8.x Store, můžete použít prostředky z existující desktopové aplikace. Tyto dva druhy aplikací však používají různé formáty souborů. U aplikací klasické pracovní plochy jsou prostředky v textových souborech (.txt nebo .restext) nebo souborech .resx kompilovány do binárních souborů .resources. V aplikacích pro Windows 8.x Store jsou soubory .resw kompilovány do binárních souborů indexu prostředků balíčku (PRI). Resgen.exe můžete použít k překlenutí této mezery extrahováním prostředků ze spustitelného souboru nebo satelitního sestavení a jejich zápisem do jednoho nebo více souborů RESW, které lze použít při vývoji aplikace pro Windows 8.x Store.  
  
> [!IMPORTANT]
> Visual Studio automaticky zpracovává všechny převody potřebné pro začlenění prostředků v přenosné knihovně do aplikace pro Windows 8.x Store. Použití resgen.exe přímo převést prostředky v sestavení do formátu .resw souboru je zajímavé pouze pro vývojáře, kteří chtějí vyvinout aplikaci Windows 8.x Store mimo Visual Studio.  
  
 Syntaxe pro vygenerování souborů .resw ze sestavení je následující:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 kde parametry jsou:  
  
 `filename.extension`  
 Název sestavení .NET Framework (soubor .exe nebo .dll). Neobsahuje-li soubor žádné prostředky, nástroj Resgen.exe nevytvoří žádné soubory.  
  
 `outputDirectory`  
 Existující adresář, do nějž budou zapsány soubory .resw. Pokud `outputDirectory` je vynechán, .resw soubory jsou zapsány do aktuálního adresáře. Nástroj Resgen.exe vytváří jeden soubor .resw pro každý soubor .resources v sestavení. Kořenový název souboru .resw je stejný jako kořenový název souboru .resources.  
  
 Následující příkaz vytvoří pro každý soubor .resources vložený do aplikace MyApp.exe soubor .resw v adresáři Win8Resources:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>
### <a name="conditionally-compiling-resources"></a>Podmíněná kompilace prostředků  
 Počínaje rozhraním .NET Framework 4.5 podporuje program Resgen.exe podmíněnou kompilaci řetězcových prostředků v textových souborech (.txt a .restext). To umožňuje použití jediného textového souboru prostředků v několika konfiguracích sestavení.  
  
 V souboru .txt nebo .restext `#ifdef`použijete ...`#endif` konstrukce zahrnout zdroj do binárního souboru .resources, pokud je `#if !`definován symbol, a použít ... `#endif` konstrukce zahrnout prostředek, pokud symbol není definován. V době kompilace pak definujete `/define:` symboly pomocí možnosti následované seznamem symbolů oddělených čárkami. Porovnání je citlivé na malá a velká písmena; písmeno symbolů `/define` definovaných v písmenu musí odpovídat velikosti symbolů v textových souborech, které mají být kompilovány.  
  
 Například následující soubor s názvem UIResources.rext `AppTitle` obsahuje řetězec prostředek s názvem, který `PRODUCTION`může `CONSULT`trvat jednu ze tří hodnot, v závislosti na tom, zda symboly s názvem , , nebo `RETAIL` jsou definovány.  
  
```text
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 Soubor může být poté zkompilován do binárního souboru .resources následujícím příkazem:  
  
```console  
resgen /define:CONSULT UIResources.restext  
```  
  
 To vytvoří soubor .resources obsahující dva řetězcové prostředky. Hodnota `AppTitle` zdroje je "Můj konzultant společnosti Project Manager".  
  
<a name="Strong"></a>
### <a name="generating-a-strongly-typed-resource-class"></a>Generování třídy prostředků se silnými typy  
 Nástroj Resgen.exe podporuje prostředky se silnými typy, což zapouzdřuje přístup k prostředkům vytvořením tříd obsahujících sadu statických vlastností určených pouze pro čtení. To poskytuje alternativu k volání <xref:System.Resources.ResourceManager> metody třídy přímo načíst prostředky. Podporu prostředků silného typu můžete povolit pomocí možnosti `/str` v resgen.exe, <xref:System.Resources.Tools.StronglyTypedResourceBuilder> která zalomí funkce třídy. Když zadáte `/str` možnost, výstup Resgen.exe je třída, která obsahuje vlastnosti silného typu, které odpovídají prostředkům, které jsou odkazovány ve vstupním parametru. Tato třída poskytuje k prostředkům dostupným ve zpracovaném souboru přístup se silnými typy určený pouze pro čtení.  
  
 Syntaxe pro vytvoření prostředku se silnými typy je následující:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry a přepínače jsou následující:  
  
 `inputFilename`  
 Název souboru prostředku (včetně přípony), pro který má být vygenerována třída prostředku se silnými typy. Souborem může být textový soubor, binární soubor .resources nebo soubor založený na jazyce XML. Může mít příponu .txt, .restext, .resw nebo .resources.  
  
 `outputFilename`  
 Název výstupního souboru Pokud `outputFilename` obsahuje cestu k adresáři, musí adresář existovat. Pokud jej vynechete `outputFilename`, program Resgen.exe vytvoří `inputFilename` soubor .resources `inputFilename`s názvem kořenového souboru ve stejném adresáři jako .  
  
 `outputFilename`může být textový soubor založený na xml nebo binárním souboru .resources. Pokud se přípona souboru `outputFilename` liší `inputFilename`od přípony souboru , resgen.exe provede převod souboru.  
  
 Pokud `inputFilename` je soubor .resources, resgen.exe zkopíruje `outputFilename` soubor .resources, pokud je také soubor emitovaných prostředků. Pokud `outputFilename` je vynechán, resgen.exe `inputFilename` přepíše s identický soubor .resources.  
  
 *Jazyk*  
 Jazyk, v němž má být vygenerován zdrojový kód pro třídu prostředků se silnými typy. Možné hodnoty `cs` `C#`jsou `csharp` , , a `vb` `visualbasic` pro kód Jazyka `vbs` `vbscript` C# a pro `c++`kód `mc`jazyka `cpp` A pro kód Jazyka VBScript a , a pro kód Jazyka C++.  
  
 *Namespace*  
 Obor názvů obsahující třídu prostředku se silnými typy. Soubor .resources a třída prostředků by měly mít stejný obor názvů. Informace o určení oboru názvů `outputFilename`v oblasti , naleznete v [tématu Kompilace prostředků do binárního souboru](resgen-exe-resource-file-generator.md#Compiling). Pokud je *obor názvů* vynechán, třída prostředků není v oboru názvů obsažena.  
  
 *Classname*  
 Název třídy prostředku se silnými typy. Tento parametr by měl odpovídat názvu kořenového souboru .resources. Pokud například nástroj Resgen.exe vygeneruje soubor .resources pojmenovaný MyCompany.Libraries.Strings.resources, název třídy prostředků silného typu je Strings. Pokud název *třídy* je vynechán, generované třídy je `outputFilename`odvozen od kořenového názvu . Pokud `outputFilename` je vynechán, generované třídy je odvozen z `inputFilename`kořenový název .  
  
 *název třídy* nemůže obsahovat neplatné znaky, například vložené mezery. Pokud *název classname* obsahuje vložené mezery nebo pokud název *třídy* je generován ve výchozím nastavení z *inputFilename*a *inputFilename* \_obsahuje vložené mezery, Resgen.exe nahradí všechny neplatné znaky podtržítkem ( ).  
  
 *Název_souboru*  
 Název souboru třídy.  
  
 `/publicclass`  
 Nařkne třídu prostředků silného typu jako veřejnou, nikoli `internal` (v jazyce C#) nebo `Friend` (v jazyce Visual Basic). To umožňuje přístup k prostředkům z míst mimo sestavení, v němž jsou vloženy.  
  
> [!IMPORTANT]
> Při vytváření třídy prostředku se silnými typy se musí název souboru .resources shodovat s oborem názvů a názvem třídy generovaného kódu. Nástroj Resgen.exe však umožňuje zadat možnosti, které vytvoří soubor .resources nekompatibilního názvu. Chcete-li toto chování obejít, přejmenujte po vygenerování výstupní soubor.  
  
 Třída prostředků se silnými typy má následující členy:  
  
- Konstruktor bez parametrů, který lze použít k vytvoření instance třídy prostředků silného typu.  
  
- Vlastnost `static` (C#) `Shared` nebo (Visual Basic) `ResourceManager` a vlastnost <xref:System.Resources.ResourceManager> jen pro čtení, která vrací instanci, která spravuje prostředek silného typu.  
  
- Statická `Culture` vlastnost, která umožňuje nastavit jazykovou verzi používanou pro načítání prostředků. Ve výchozím nastavení `null`je jeho hodnota , což znamená, že se používá aktuální jazyková verze ui.  
  
- Jedna `static` (C#) `Shared` nebo (Visual Basic) a vlastnost jen pro čtení pro každý prostředek v souboru .resources. Název vlastnosti je názvem prostředku.  
  
 Následující příkaz například zkompiluje soubor prostředků s názvem StringResources.txt do `StringResources` souboru StringResources.resources a vygeneruje třídu pojmenovanou v souboru zdrojového kódu jazyka Visual Basic s názvem StringResources.vb, který lze použít pro přístup ke Správci prostředků.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Prostředky v aplikacích klasické pracovní plochy](../resources/index.md)
- [Vytváření zdrojových souborů](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
