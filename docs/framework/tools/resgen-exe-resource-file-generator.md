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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c8a619021f8e398c5c3dfc974b9130ecacb44d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (generátor zdrojových souborů)
Nástroj Resource File Generator (Resgen.exe) převádí textové soubory (.txt nebo .restext) a soubory ve formátu prostředků založeném na jazyce XML (.resx) na binární soubory modulu CLR (.resources), které mohou být vloženy do binárního spustitelného souboru modulu nebo satelitního sestavení. (Viz [vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe je univerzální nástroj pro převod prostředků, který plní následující úlohy:  
  
-   Převádí soubory .txt nebo .restext na soubory .resources nebo .resx. (Formát souborů .restext je shodný s formátem souborů .txt. Přípona .restext však usnadňuje identifikaci textových souborů obsahujících definici prostředků.)  
  
-   Převádí soubory .resources na textové soubory nebo soubory .resx.  
  
-   Převádí soubory .resx na textové soubory nebo soubory .resources.  
  
-   Extrahuje řetězcové prostředky ze sestavení do .resw souboru, který je vhodný pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
-   Vytvoří třídu silného typu, který zajišťuje přístup k prostředkům jednotlivých s názvem a na <xref:System.Resources.ResourceManager> instance.  
  
 Pokud nástroj Resgen.exe z jakéhokoli důvodu selže, je návratová hodnota –1.  
  
 Chcete-li získat nápovědu k nástroji Resgen.exe, lze použít následující příkaz bez jakýchkoli možností a zobrazit tak syntaxi příkazů a možnosti nástroje Resgen.exe:  
  
```  
resgen  
```  
  
 Můžete také `/?` přepínače:  
  
```  
resgen /?  
```  
  
 Pokud používáte nástroj Resgen, exe ke generování .resources binární soubory, můžete kompilátor jazyka pro vložení binární soubory do spustitelného souboru sestavení nebo můžete použít [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) jejich kompilace na satelitní sestavení.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
resgen  [/define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```  
resgen filename.extension [outputDirectory]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr nebo přepínač|Popis|  
|-------------------------|-----------------|  
|`/define:` *symbol1*[, *symbol2*,...]|Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], podporuje Podmíněná kompilace v založený na textu (s příponou TXT nebo .restext) soubory prostředků. Pokud *symbol* odpovídá symbol součástí souboru vstupního textu v rámci `#ifdef` konstrukce, přidružené řetězec prostředku je součástí souboru .resources. Pokud soubor vstupního textu obsahuje `#if !` příkaz s symbol, který není definované `/define` přepínače, přidružené řetězec prostředku je součástí souboru prostředků.<br /><br /> `/define` Pokud se používá s bez textových souborů je ignorována. Rozlišují se malá a velká písmena.<br /><br /> Další informace o této možnosti najdete v tématu [Podmíněná kompilace prostředky](#Conditional) dál v tomto tématu.|  
|`useSourcePath`|Určuje, že k vyhodnocení relativních cest k souborům má být použit aktuální adresář vstupního souboru.|  
|`/compile`|Umožňuje zadat několik textových souborů nebo souborů .resx pro převod na několik souborů .resources jednou hromadnou operací. Pokud tuto možnost nezadáte, lze zadat pouze jeden argument vstupního souboru. Výstupní soubory jsou pojmenované *filename*.resources.<br /><br /> Tuto možnost nelze použít s `/str:` možnost.<br /><br /> Další informace o této možnosti najdete v tématu [kompilace nebo převádění více souborů](#Multiple) dál v tomto tématu.|  
|`/r:``assembly`|Odkazuje na metadata z určeného sestavení. Používá se při převodu souborů .resx a umožňuje nástroji Resgen.exe serializovat a deserializovat prostředky objektů. Je podobná `/reference:` nebo `/r:` možnosti kompilátory jazyka C# a Visual Basic.|  
|`filename.extension`|Určuje název vstupního souboru, který má být převeden. Pokud používáte první, delší syntaxi příkazového řádku uvedené před tuto tabulku, `extension` musí mít jednu z následujících akcí:<br /><br /> .txt nebo .restext<br /> Textový soubor, který má být převeden na soubor .resources nebo .resx. Textové soubory mohou obsahovat pouze řetězcové prostředky. Informace o formátu souborů, najdete v části "Prostředky v textových souborů" [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Soubor prostředků založený na jazyce XML, který má být převeden na soubor .resources nebo textový soubor (.txt nebo .restext).<br /><br /> .resources<br /> Binární soubor prostředků, který má být převeden na soubor .resx nebo textový soubor (.txt nebo .restext).<br /><br /> Pokud používáte druhou, kratší syntaxi příkazového řádku uvedené před tuto tabulku, `extension` musí být následující:<br /><br /> .exe nebo .dll<br /> Jejichž řetězcové prostředky se mají extrahovat do souboru .resw pro použití při vývoji sestavení rozhraní .NET Framework (spustitelný soubor nebo knihovna) [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.|  
|`outputFilename.extension`|Určuje název a typ souboru prostředků, který má být vytvořen.<br /><br /> Při převodu ze souboru .txt, .restext nebo .resx na soubor .resources je tento argument nepovinný. Pokud nezadáte `outputFilename`, Resgen.exe připojí .resources rozšíření do vstupní `filename` a zapíše soubor do adresáře, který obsahuje `filename,extension`.<br /><br /> `outputFilename.extension` Argument je povinný při převodu ze souboru .resources. Při převodu souboru .resources na soubor prostředků založený na jazyce XML zadejte název souboru s příponou .resx. Při převodu souboru .resources na textový soubor zadejte název souboru s příponou .txt nebo restext. Soubor .resources by měl být na soubor .txt převeden pouze v případě, že soubor .resources obsahuje výhradně řetězcové hodnoty.|  
|`outputDirectory`|Pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, určuje adresář, ve kterém .resw souboru, který obsahuje řetězcové prostředky v `filename.extension` budou zapisovat. `outputDirectory` již musí existovat.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Vytvoří soubor Třída prostředků se silnými typy v programovacím jazyce zadaný v `language` možnost. `language` Můžete se skládá z jedné z následujících literály:<br /><br /> -Pro jazyk C#: `c#`, `cs`, nebo `csharp`.<br />-Pro jazyk Visual Basic: `vb` nebo `visualbasic`.<br />-Pro jazyk VBScript: `vbs` nebo `vbscript`.<br />-Pro jazyk C++: `c++`, `mc`, nebo `cpp`.<br />-Pro JavaScript: `js`, `jscript`, nebo `javascript`.<br /><br /> `namespace` Možnost určuje výchozí obor názvů projektu, `classname` možnost určuje název vygenerované třídy a `filename` možnost určuje název souboru třídy.<br /><br /> `/str:` Možnost umožňuje pouze jeden vstupní soubor, takže jej nelze použít s `/compile` možnost.<br /><br /> Pokud `namespace` je zadán, ale `classname` není, název třídy je odvozený od názvu výstupního souboru (například dobu jsou nahrazena podtržítka). Prostředky se silnými typy možná důsledkem toho nebudou fungovat správně. Chcete-li se tomuto problému vyhnout, zadejte název třídy i název výstupního souboru.<br /><br /> Další informace o této možnosti najdete v tématu [generování silně typované třídy prostředku](#Strong) dál v tomto tématu.|  
|`/publicClass`|Vytvoří třídu prostředků se silnými typy jako veřejnou třídu. Ve výchozím nastavení, je třída prostředků `internal` v jazyce C# a `Friend` v jazyce Visual Basic.<br /><br /> Tato možnost je ignorována, pokud `/str:` možnost nepoužívá.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Nástroj Resgen.exe a typy souborů prostředků  
 Aby nástroj Resgen.exe mohl úspěšně převádět prostředky, textové soubory a soubory .resx, musí dodržovat správný formát.  
  
### <a name="text-txt-and-restext-files"></a>Textové soubory (.txt a .restext)  
 Textové soubory (.txt nebo .restext) mohou obsahovat výhradně řetězcové prostředky. Řetězcové prostředky jsou užitečné při psaní aplikace, která musí mít řetězce přeloženy do několika jazyků. Lze například snadno lokalizovat řetězce nabídky použitím příslušného řetězcového prostředku. Nástroj Resgen.exe čte textové soubory obsahující dvojice název/hodnota, kde název je řetězec popisující prostředek a hodnota je samotný řetězec prostředku.  
  
> [!NOTE]
>  Informace o formátu souborů TXT a .restext, najdete v části "Prostředky v textových souborů" [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Neobsahuje-li textový soubor s prostředky pouze znaky z rozsahu základní latinky (do U+007F), musí být uložen s kódováním UTF-8 nebo Unicode (UTF-16). Při zpracovávání textového souboru uloženého s kódováním ANSI nástroj Resgen.exe odstraňuje rozšířené znaky ANSI.  
  
 Nástroj Resgen.exe kontroluje, zda textový soubor obsahuje duplicitní názvy prostředků. Obsahuje-li textový soubor duplicitní názvy prostředků, nástroj Resgen.exe vygeneruje upozornění a bude ignorovat druhou hodnotu.  
  
### <a name="resx-files"></a>Soubory .resx  
 Formát souboru prostředků .resx sestává ze záznamů jazyka XML. Uvnitř těchto záznamů jazyka XML lze zadávat řetězcové prostředky jako v textových souborech. Hlavní výhodou souborů .resx oproti textovým souborům je možnost zadávat nebo vkládat objekty. Při zobrazení souboru .resx lze vidět binární podobu vloženého objektu (například obrázku), pokud je tato binární informace součástí manifestu prostředku. Stejně jako textové soubory lze i soubory .resx otevřít v textovém editoru (například Poznámkový blok nebo Microsoft Word) a zapisovat, analyzovat či upravovat jejich obsah. To vyžaduje dobrou znalost značek XML a struktury souboru .resx. Další informace o formátu souboru RESX, najdete v části "Zdroje v soubory RESX" [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Chcete-li vytvořit .resources soubor, který obsahuje vložené neřetězcový objekty, musí buď pomocí Resgen.exe převeďte soubor .resx obsahující objekty nebo přidejte objekt prostředky do souboru přímo z kódu voláním metody poskytované <xref:System.Resources.ResourceWriter> Třída.  
  
 Obsahuje-li soubor .resx nebo .resources objekty a použijete-li nástroj Resgen.exe k jeho převodu na textový soubor, všechny řetězcové prostředky budou převedeny správně, ale datové typy neřetězcových objektů budou do souboru také zapsány jako řetězce. Během převodu dojde ke ztrátě vložených objektů a nástroj Resgen.exe oznámí, že při načítání prostředků došlo k chybě.  
  
### <a name="converting-between-resources-file-types"></a>Převod mezi typy souborů prostředků  
 Při převádění mezi různými typy souborů prostředků nástroj Resgen.exe nemusí být schopen převod provést nebo může ztratit informace o určitých prostředcích v závislosti na zdrojovém a cílovém typu souboru. Následující tabulka obsahuje typy převodů, které jsou při převádění jednoho typu souboru prostředků na jiný úspěšné.  
  
|Převod z|Na textový soubor|Na soubor .resx|Na soubor .resw|Na soubor .resources|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Textový soubor (.txt nebo .restext)|--|Žádné problémy|Nepodporováno|Žádné problémy|  
|Soubor .resx|Obsahuje-li soubor neřetězcové prostředky (včetně odkazů na soubory), převod se nezdaří.|--|Nepodporováno|Žádné problémy|  
|Soubor .resources|Obsahuje-li soubor neřetězcové prostředky (včetně odkazů na soubory), převod se nezdaří.|Žádné problémy|Nepodporováno|--|  
|Sestavení .exe nebo .dll|Nepodporováno|Nepodporováno|Pouze řetězcové prostředky (včetně názvů cest) jsou rozpoznány jako prostředky|Nepodporováno|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Provádění konkrétních úloh nástroje Resgen.exe  
 Resgen.exe můžete používat různé způsoby: ke kompilaci souboru prostředků založený na textu nebo formátu XML do binárního souboru, pro převod mezi formáty souborů prostředků a ke generování třídu, která zabalí <xref:System.Resources.ResourceManager> funkce a poskytuje přístup k prostředkům. Tato část poskytuje podrobné informace o každém úkolu:  
  
-   [Kompilování prostředky do binárního souboru](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
-   [Převod mezi typy souborů prostředků](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
-   [Kompilování nebo převod více souborů](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
-   [Export prostředků do souboru .resw](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
-   [Podmíněná kompilace prostředky](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
-   [Generování třídy prostředků se silnými typy](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilace prostředků do binárního souboru  
 Nejběžnější použití nástroje Resgen.exe je kompilování textového souboru prostředků (soubor .txt nebo .restext) nebo souboru prostředků založeného na jazyce XML (soubor .resx) do binárního souboru .resources. Výstupní soubor pak můžete vložit do hlavní sestavení kompilátoru jazyka nebo v satelitní sestavení pomocí [Linker sestavení (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Syntaxe pro kompilaci souboru prostředků je následující:  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 kde parametry jsou:  
  
 `inputFilename`  
 Název kompilovaného souboru prostředků (včetně přípony). Nástroj Resgen.exe kompiluje pouze soubory s příponami .txt, .restext nebo .resx.  
  
 `outputFilename`  
 Název výstupního souboru Pokud vynecháte `outputFilename`, Resgen.exe vytvoří soubor s příponou RESOURCES s názvem souboru kořenové `inputFilename` ve stejném adresáři jako `inputFilename`. Pokud `outputFilename` obsahuje cestu k adresáři tento adresář musí existovat.  
  
 Souboru .resources je poskytován plně kvalifikovaný obor názvů jeho zadáním v názvu souboru a oddělením od názvu kořenového souboru tečkou. Například pokud `outputFilename` je `MyCompany.Libraries.Strings.resources`, MyCompany.Libraries je obor názvů.  
  
 Následující příklad přečte dvojice název/hodnota v souboru Resources.txt a zapíše binární soubor .resources pojmenovaný Resources.resources. Soubor dostane dle výchozího nastavení název shodný s názvem vstupního souboru, protože název výstupního souboru nebyl explicitně zadán.  
  
```  
resgen Resources.txt   
```  
  
 Následující příkaz přečte dvojice název/hodnota v souboru Resources.restext a zapíše binární soubor .resources pojmenovaný StringResources.resources.  
  
```  
resgen Resources.restext StringResources.resources  
```  
  
 Následující příkaz přečte vstupní soubor založený na jazyce XML pojmenovaný Resources.resx a zapíše binární soubor .resources pojmenovaný Resources.resources.  
  
```  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>   
### <a name="converting-between-resource-file-types"></a>Převod mezi typy souborů prostředků  
 Kromě kompilování textových souborů prostředků nebo souborů prostředků založených na jazyce XML do binárních souborů .resources dokáže nástroj Resgen.exe také převést libovolný podporovaný typ souboru na libovolný jiný podporovaný typ. To znamená, že může provést následující převody:  
  
-   Soubory .txt a .restext na soubory .resx.  
  
-   Soubory .resx na soubory .txt a .restext.  
  
-   Soubory .resources na soubory .txt a .restext.  
  
-   Soubory .resources na soubory .resx.  
  
 Syntaxe je shodná se syntaxí uvedenou v předchozí části.  
  
 Kromě toho můžete použít Resgen.exe převést vložené prostředky v sestavení rozhraní .NET Framework na soubor tor .resw [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 Následující příkaz přečte binární soubor prostředků Resources.resources a zapíše výstupní soubor založený na jazyce XML pojmenovaný Resources.resx.  
  
```  
resgen Resources.resources Resources.resx  
```  
  
 Následující příkaz přečte vstupní textový soubor StringResources.txt a zapíše soubor prostředků založený na jazyce XML pojmenovaný LibraryResources.resx. Kromě řetězcových prostředků může být soubor .resx použit také pro uchování neřetězcových prostředků.  
  
```  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Následující dva příkazy přečtou vstupní soubor prostředků založený na jazyce XML pojmenovaný Resources.resx a zapíší textové soubory pojmenované Resources.txt a Resources.restext. Pokud soubor .resx obsahuje jakékoli vložené objekty, nebudou do textových souborů převedeny přesně.  
  
```  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>   
### <a name="compiling-or-converting-multiple-files"></a>Kompilace nebo převod více souborů  
 Můžete použít `/compile` přepínač převést seznam souborů prostředků z jednoho formátu do druhého v rámci jedné operace. Syntaxe je následující:  
  
```  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Následující příkaz zkompiluje tři soubory, StringResources.txt, TableResources.resw a ImageResources.resw, do oddělených souborů .resources pojmenovaných StringResources.resources, TableResources.resources a ImageResources.resources.  
  
```  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Exportování prostředků do souboru .resw  
 Pokud vyvíjíte [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, můžete využívat prostředky z existujících klientů aplikace. Tyto dva druhy aplikací však používají různé formáty souborů. U aplikací klasické pracovní plochy jsou prostředky v textových souborech (.txt nebo .restext) nebo souborech .resx kompilovány do binárních souborů .resources. V [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] kompilované aplikace, .resw soubory do balíčku binární soubory indexu (PRI) prostředků. Resgen.exe můžete použít přemostění během této poměrně extrahování prostředky z spustitelný soubor nebo satelitní sestavení a jejich zápis do jednoho nebo více .resw soubory, které lze použít při vývoji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
> [!IMPORTANT]
>  Visual Studio automaticky zpracovává všechny potřebné pro zahrnutí prostředků v přenosné knihovny do převody [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Pomocí Resgen.exe přímo převést prostředky v sestavení .resw formát souboru je určen pouze pro vývojáře, kteří chtějí k vývoji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace mimo Visual Studio.  
  
 Syntaxe pro vygenerování souborů .resw ze sestavení je následující:  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 kde parametry jsou:  
  
 `filename.extension`  
 Název sestavení .NET Framework (soubor .exe nebo .dll). Neobsahuje-li soubor žádné prostředky, nástroj Resgen.exe nevytvoří žádné soubory.  
  
 `outputDirectory`  
 Existující adresář, do nějž budou zapsány soubory .resw. Pokud `outputDirectory` je tento parametr vynechán, .resw soubory jsou zapsány do aktuální adresář. Nástroj Resgen.exe vytváří jeden soubor .resw pro každý soubor .resources v sestavení. Kořenový název souboru .resw je stejný jako kořenový název souboru .resources.  
  
 Následující příkaz vytvoří pro každý soubor .resources vložený do aplikace MyApp.exe soubor .resw v adresáři Win8Resources:  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Podmíněná kompilace prostředků  
 Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Resgen.exe podporuje Podmíněná kompilace prostředků řetězec v textových souborů (.txt a .restext). To umožňuje použití jediného textového souboru prostředků v několika konfiguracích sestavení.  
  
 V souboru .txt nebo .restext, můžete použít `#ifdef`...`#endif` konstrukce zahrnout prostředku v souboru .resources binární, pokud symbol je definovaný a použít `#if !`... `#endif` konstrukce zahrnout prostředku, pokud symbol není definován. Při kompilaci, pak definujete symboly pomocí `/define:` následovaný čárkami oddělený seznam symbolů. Porovnání je použita citlivé; v případě symboly definované `/define` malá symboly v textové soubory, které mají být zkompilovány, do se musí shodovat.  
  
 Například následující soubor s názvem UIResources.rext obsahuje řetězec prostředek s názvem `AppTitle` , může trvat jednu ze tří hodnot, v závislosti na tom, jestli s názvem symboly `PRODUCTION`, `CONSULT`, nebo `RETAIL` jsou definovány.  
  
```  
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
  
```  
resgen /define:CONSULT UIResources.restext  
```  
  
 To vytvoří soubor .resources obsahující dva řetězcové prostředky. Hodnota `AppTitle` prostředků je Moje konzultace ohledně společnosti projektu správce.  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generování třídy prostředků se silnými typy  
 Nástroj Resgen.exe podporuje prostředky se silnými typy, což zapouzdřuje přístup k prostředkům vytvořením tříd obsahujících sadu statických vlastností určených pouze pro čtení. To představuje alternativu k volání metod <xref:System.Resources.ResourceManager> třída přímo k načtení prostředků. Podporu silného typu prostředků můžete povolit pomocí `/str` možnost v Resgen.exe, který zabalí funkce <xref:System.Resources.Tools.StronglyTypedResourceBuilder> třídy. Pokud zadáte `/str` možnost výstup Resgen.exe je třída, která obsahuje silného typu vlastnosti, které odpovídají prostředky, které jsou odkazované ve vstupní parametr. Tato třída poskytuje k prostředkům dostupným ve zpracovaném souboru přístup se silnými typy určený pouze pro čtení.  
  
 Syntaxe pro vytvoření prostředku se silnými typy je následující:  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry a přepínače jsou následující:  
  
 `inputFilename`  
 Název souboru prostředku (včetně přípony), pro který má být vygenerována třída prostředku se silnými typy. Souborem může být textový soubor, binární soubor .resources nebo soubor založený na jazyce XML. Může mít příponu .txt, .restext, .resw nebo .resources.  
  
 `outputFilename`  
 Název výstupního souboru Pokud `outputFilename` obsahuje cestu k adresáři tento adresář musí existovat. Pokud vynecháte `outputFilename`, Resgen.exe vytvoří soubor s příponou RESOURCES s názvem souboru kořenové `inputFilename` ve stejném adresáři jako `inputFilename`.  
  
 `outputFilename` může být souboru .resources založený na textu, formátu XML nebo binární. Pokud přípona souboru `outputFilename` se liší od přípona souboru `inputFilename`, Resgen.exe provede převod souborů.  
  
 Pokud `inputFilename` je soubor .resources Resgen.exe kopie souboru .resources Pokud `outputFilename` je také soubor s příponou RESOURCES. Pokud `outputFilename` je tento parametr vynechán, přepíše Resgen.exe `inputFilename` se souborem .resources identické.  
  
 *Jazyk*  
 Jazyk, v němž má být vygenerován zdrojový kód pro třídu prostředků se silnými typy. Možné hodnoty jsou `cs`, `C#`, a `csharp` pro kód C#, `vb` a `visualbasic` pro kód jazyka Visual Basic, `vbs` a `vbscript` pro kód v jazyce VBScript, a `c++`, `mc`a `cpp` pro C++ – kód.  
  
 *namespace*  
 Obor názvů obsahující třídu prostředku se silnými typy. Soubor .resources a třída prostředků by měly mít stejný obor názvů. Informace o zadání oboru názvů v `outputFilename`, najdete v části [kompilování prostředky do binárního souboru](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling). Pokud *obor názvů* je tento parametr vynechán, třída prostředků není obsažen v oboru názvů.  
  
 *Název třídy*  
 Název třídy prostředku se silnými typy. Tento parametr by měl odpovídat názvu kořenového souboru .resources. Pokud například nástroj Resgen.exe vygeneruje soubor .resources pojmenovaný MyCompany.Libraries.Strings.resources, název třídy prostředků silného typu je Strings. Pokud *classname* je tento parametr vynechán, generovaná třída je odvozený od název kořenového `outputFilename`. Pokud `outputFilename` je tento parametr vynechán, generovaná třída je odvozený od název kořenového `inputFilename`.  
  
 *Název třídy* nemůže obsahovat neplatné znaky, jako jsou mezery. Pokud *classname* obsahuje mezery, nebo pokud *classname* je generována ve výchozím nastavení z *inputFilename*, a *inputFilename* obsahuje mezery, Resgen.exe nahradí všechny neplatné znaky podtržítkem (_).  
  
 *Název souboru*  
 Název souboru třídy.  
  
 `/publicclass`  
 Díky Třída prostředků se silnými typy veřejné místo `internal` (v jazyku C#) nebo `Friend` (v jazyce Visual Basic). To umožňuje přístup k prostředkům z míst mimo sestavení, v němž jsou vloženy.  
  
> [!IMPORTANT]
>  Při vytváření třídy prostředku se silnými typy se musí název souboru .resources shodovat s oborem názvů a názvem třídy generovaného kódu. Nástroj Resgen.exe však umožňuje zadat možnosti, které vytvoří soubor .resources nekompatibilního názvu. Chcete-li toto chování obejít, přejmenujte po vygenerování výstupní soubor.  
  
 Třída prostředků se silnými typy má následující členy:  
  
-   Konstruktor bez parametrů, který lze použít k vytvoření instance třídy prostředku silného typu.  
  
-   A `static` (C#) nebo `Shared` (Visual Basic) a jen pro čtení `ResourceManager` vlastnost, která vrací <xref:System.Resources.ResourceManager> instance, která spravuje silného typu prostředku.  
  
-   Statického `Culture` vlastnosti, která vám umožní nastavit jazyková verze použitá pro načtení prostředků. Ve výchozím nastavení, jeho hodnota může být `null`, to znamená, že aby se používala aktuální jazykové verze uživatelského rozhraní.  
  
-   Jeden `static` (C#) nebo `Shared` (Visual Basic) a pro každý prostředek v souboru .resources vlastnost jen pro čtení. Název vlastnosti je názvem prostředku.  
  
 Například následující příkaz zkompiluje soubor prostředků s názvem StringResources.txt do StringResources.resources a vygeneruje třídy s názvem `StringResources` v jazyce Visual Basic zdroji kódu soubor s názvem StringResources.vb, který slouží pro přístup k prostředku Správce.  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)  
 [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
