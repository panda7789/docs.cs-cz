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
ms.openlocfilehash: c6b908cadc02e0d1739d8b36b6904bb47c5ea090
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378467"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (generátor zdrojových souborů)
Nástroj Resource File Generator (Resgen.exe) převádí textové soubory (.txt nebo .restext) a soubory ve formátu prostředků založeném na jazyce XML (.resx) na binární soubory modulu CLR (.resources), které mohou být vloženy do binárního spustitelného souboru modulu nebo satelitního sestavení. (Viz [vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe je univerzální nástroj pro převod prostředků, který plní následující úlohy:  
  
- Převádí soubory .txt nebo .restext na soubory .resources nebo .resx. (Formát souborů .restext je shodný s formátem souborů .txt. Přípona .restext však usnadňuje identifikaci textových souborů obsahujících definici prostředků.)  
  
- Převádí soubory .resources na textové soubory nebo soubory .resx.  
  
- Převádí soubory .resx na textové soubory nebo soubory .resources.  
  
- Extrahuje prostředky řetězce ze sestavení do souboru .resw vhodného pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
- Vytvoří třídu silného typu, který poskytuje přístup k jednotlivým pojmenovaným prostředkům a získat <xref:System.Resources.ResourceManager> instance.  
  
 Pokud nástroj Resgen.exe z jakéhokoli důvodu selže, je návratová hodnota –1.  
  
 Chcete-li získat nápovědu k nástroji Resgen.exe, lze použít následující příkaz bez jakýchkoli možností a zobrazit tak syntaxi příkazů a možnosti nástroje Resgen.exe:  
  
```  
resgen  
```  
  
 Můžete také použít `/?` přepínače:  
  
```  
resgen /?  
```  
  
 Pokud používáte Resgen.exe ke generování binárních souborů .resources, můžete použít kompilátor jazyka pro vložení binárních souborů do spustitelných sestavení nebo můžete použít [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pro jejich zkompilování do satelitních sestavení.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
resgen  [/define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr nebo přepínač|Popis|  
|-------------------------|-----------------|  
|`/define:` *symbol1*[, *symbol2*,...]|Od verze rozhraní .NET Framework 4.5, podporuje podmíněnou kompilaci v založený na textu (.txt nebo .restext) soubory prostředků. Pokud *symbol* odpovídá symbolu zahrnutému ve vstupním textovém souboru v rámci `#ifdef` konstrukce, příslušný řetězcový prostředek jsou uvedeny v souboru .resources. Pokud vstupní textový soubor obsahuje `#if !` příkazu se symbolem nedefinovaným `/define` přepínače, příslušný řetězcový prostředek je součástí souboru prostředků.<br /><br /> `/define` Pokud se používá s netextovými soubory je ignorována. Rozlišují se malá a velká písmena.<br /><br /> Další informace o této možnosti najdete v tématu [Podmíněná kompilace prostředků](#Conditional) dále v tomto tématu.|  
|`useSourcePath`|Určuje, že k vyhodnocení relativních cest k souborům má být použit aktuální adresář vstupního souboru.|  
|`/compile`|Umožňuje zadat několik textových souborů nebo souborů .resx pro převod na několik souborů .resources jednou hromadnou operací. Pokud tuto možnost nezadáte, lze zadat pouze jeden argument vstupního souboru. Výstupní soubory jsou pojmenovány *filename*.resources.<br /><br /> Tento parametr nelze použít s `/str:` možnost.<br /><br /> Další informace o této možnosti najdete v tématu [kompilace nebo převod více souborů](#Multiple) dále v tomto tématu.|  
|`/r:``assembly`|Odkazuje na metadata z určeného sestavení. Používá se při převodu souborů .resx a umožňuje nástroji Resgen.exe serializovat a deserializovat prostředky objektů. Se podobá `/reference:` nebo `/r:` možnosti pro kompilátory jazyků C# a Visual Basic.|  
|`filename.extension`|Určuje název vstupního souboru, který má být převeden. Pokud používáte první, delší syntaxi příkazového řádku popsanou nad touto tabulkou `extension` musí být jedna z následujících akcí:<br /><br /> .txt nebo .restext<br /> Textový soubor, který má být převeden na soubor .resources nebo .resx. Textové soubory mohou obsahovat pouze řetězcové prostředky. Informace o formátu souborů, najdete v části "Prostředky v textových souborech" [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Soubor prostředků založený na jazyce XML, který má být převeden na soubor .resources nebo textový soubor (.txt nebo .restext).<br /><br /> .resources<br /> Binární soubor prostředků, který má být převeden na soubor .resx nebo textový soubor (.txt nebo .restext).<br /><br /> Pokud používáte druhou, kratší syntaxi příkazového řádku popsanou nad touto tabulkou `extension` musí být následující:<br /><br /> .exe nebo .dll<br /> Jehož řetězcové prostředky mají být extrahovány do souboru .resw pro použití při vývoji sestavení rozhraní .NET Framework (spustitelné nebo knihovna) [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.|  
|`outputFilename.extension`|Určuje název a typ souboru prostředků, který má být vytvořen.<br /><br /> Při převodu ze souboru .txt, .restext nebo .resx na soubor .resources je tento argument nepovinný. Pokud nezadáte `outputFilename`, Resgen.exe připojí příponu .resources na vstup `filename` a zapíše soubor do adresáře, který obsahuje `filename,extension`.<br /><br /> `outputFilename.extension` Při převodu ze souboru .resources je povinný argument. Při převodu souboru .resources na soubor prostředků založený na jazyce XML zadejte název souboru s příponou .resx. Při převodu souboru .resources na textový soubor zadejte název souboru s příponou .txt nebo restext. Soubor .resources by měl být na soubor .txt převeden pouze v případě, že soubor .resources obsahuje výhradně řetězcové hodnoty.|  
|`outputDirectory`|Pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací, určuje adresář, ve kterém soubor .resw obsahující řetězcové prostředky v `filename.extension` budou zapsány. `outputDirectory` už musí existovat.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Vytvoří soubor třídy prostředků se silnými typy v programovacím jazyce určeném `language` možnost. `language` se může skládat z jedné z následujících literálů:<br /><br /> -Pro jazyk C#: `c#`, `cs`, nebo `csharp`.<br />-Pro jazyk Visual Basic: `vb` nebo `visualbasic`.<br />-Pro jazyk VBScript: `vbs` nebo `vbscript`.<br />-Pro jazyk C++: `c++`, `mc`, nebo `cpp`.<br />-Pro jazyk JavaScript: `js`, `jscript`, nebo `javascript`.<br /><br /> `namespace` Určuje výchozí obor názvů projektu, `classname` Určuje název generované třídy a `filename` parametr určuje název souboru třídy.<br /><br /> `/str:` Možnost umožňuje pouze jednoho vstupního souboru, takže ho nejde použít s `/compile` možnost.<br /><br /> Pokud `namespace` je zadán, ale `classname` není, název třídy je odvozen z názvu výstupního souboru (například podtržítka jsou nahrazena tečkami). Prostředky se silnými typy možná důsledkem toho nebudou fungovat správně. Chcete-li se tomuto problému vyhnout, zadejte název třídy i název výstupního souboru.<br /><br /> Další informace o této možnosti najdete v tématu [generování silně typované třídy prostředků](#Strong) dále v tomto tématu.|  
|`/publicClass`|Vytvoří třídu prostředků se silnými typy jako veřejnou třídu. Ve výchozím nastavení je třída prostředků `internal` v jazyce C# a `Friend` v jazyce Visual Basic.<br /><br /> Tato možnost se ignoruje, pokud `/str:` není použita možnost.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Nástroj Resgen.exe a typy souborů prostředků  
 Aby nástroj Resgen.exe mohl úspěšně převádět prostředky, textové soubory a soubory .resx, musí dodržovat správný formát.  
  
### <a name="text-txt-and-restext-files"></a>Textové soubory (.txt a .restext)  
 Textové soubory (.txt nebo .restext) mohou obsahovat výhradně řetězcové prostředky. Řetězcové prostředky jsou užitečné při psaní aplikace, která musí mít řetězce přeloženy do několika jazyků. Lze například snadno lokalizovat řetězce nabídky použitím příslušného řetězcového prostředku. Nástroj Resgen.exe čte textové soubory obsahující dvojice název/hodnota, kde název je řetězec popisující prostředek a hodnota je samotný řetězec prostředku.  
  
> [!NOTE]
>  Informace o formátu souborů .txt a .restext, najdete v části "Prostředky v textových souborech" [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Neobsahuje-li textový soubor s prostředky pouze znaky z rozsahu základní latinky (do U+007F), musí být uložen s kódováním UTF-8 nebo Unicode (UTF-16). Při zpracovávání textového souboru uloženého s kódováním ANSI nástroj Resgen.exe odstraňuje rozšířené znaky ANSI.  
  
 Nástroj Resgen.exe kontroluje, zda textový soubor obsahuje duplicitní názvy prostředků. Obsahuje-li textový soubor duplicitní názvy prostředků, nástroj Resgen.exe vygeneruje upozornění a bude ignorovat druhou hodnotu.  
  
### <a name="resx-files"></a>Soubory .resx  
 Formát souboru prostředků .resx sestává ze záznamů jazyka XML. Uvnitř těchto záznamů jazyka XML lze zadávat řetězcové prostředky jako v textových souborech. Hlavní výhodou souborů .resx oproti textovým souborům je možnost zadávat nebo vkládat objekty. Při zobrazení souboru .resx lze vidět binární podobu vloženého objektu (například obrázku), pokud je tato binární informace součástí manifestu prostředku. Stejně jako textové soubory lze i soubory .resx otevřít v textovém editoru (například Poznámkový blok nebo Microsoft Word) a zapisovat, analyzovat či upravovat jejich obsah. To vyžaduje dobrou znalost značek XML a struktury souboru .resx. Podrobné informace o formátu souboru .resx, najdete v části "Prostředky v souborech .resx" [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Chcete-li vytvořit soubor .resources obsahující vložené neřetězcové objekty, musíte použít Resgen.exe a převést soubory .resx obsahující objekty nebo přidat prostředek objektu do souboru přímo z kódu zavoláním metod poskytovaných parametrem <xref:System.Resources.ResourceWriter> Třída.  
  
 Obsahuje-li soubor .resx nebo .resources objekty a použijete-li nástroj Resgen.exe k jeho převodu na textový soubor, všechny řetězcové prostředky budou převedeny správně, ale datové typy neřetězcových objektů budou do souboru také zapsány jako řetězce. Během převodu dojde ke ztrátě vložených objektů a nástroj Resgen.exe oznámí, že při načítání prostředků došlo k chybě.  
  
### <a name="converting-between-resources-file-types"></a>Převod mezi typy souborů prostředků  
 Při převádění mezi různými typy souborů prostředků nástroj Resgen.exe nemusí být schopen převod provést nebo může ztratit informace o určitých prostředcích v závislosti na zdrojovém a cílovém typu souboru. Následující tabulka obsahuje typy převodů, které jsou při převádění jednoho typu souboru prostředků na jiný úspěšné.  
  
|Převod z|Na textový soubor|Na soubor .resx|Na soubor .resw|Na soubor .resources|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Textový soubor (.txt nebo .restext)|--|Žádné problémy|Není podporováno|Žádné problémy|  
|Soubor .resx|Obsahuje-li soubor neřetězcové prostředky (včetně odkazů na soubory), převod se nezdaří.|--|Není podporováno|Žádné problémy|  
|Soubor .resources|Obsahuje-li soubor neřetězcové prostředky (včetně odkazů na soubory), převod se nezdaří.|Žádné problémy|Není podporováno|--|  
|Sestavení .exe nebo .dll|Není podporováno|Není podporováno|Pouze řetězcové prostředky (včetně názvů cest) jsou rozpoznány jako prostředky|Není podporováno|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Provádění konkrétních úloh nástroje Resgen.exe  
 Resgen.exe lze použít různými způsoby: Chcete-li zkompilovat soubor prostředků založený na textu nebo založený na formátu XML do binárního souboru, k převodu mezi formáty souborů prostředků a ke generování třídy, která obaluje <xref:System.Resources.ResourceManager> funkce a poskytuje přístup k prostředkům. Tato část poskytuje podrobné informace o každém úkolu:  
  
- [Kompilace prostředků do binárního souboru](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
- [Převod mezi typy souborů prostředků](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
- [Kompilace nebo převod více souborů](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
- [Exportování prostředků do souboru .resw](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
- [Podmíněná kompilace prostředků](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generování třídy prostředků se silnými typy](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilace prostředků do binárního souboru  
 Nejběžnější použití nástroje Resgen.exe je kompilování textového souboru prostředků (soubor .txt nebo .restext) nebo souboru prostředků založeného na jazyce XML (soubor .resx) do binárního souboru .resources. Výstupní soubor lze poté vložit do hlavního sestavení pomocí kompilátoru jazyka nebo satelitního sestavení nástrojem [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Syntaxe pro kompilaci souboru prostředků je následující:  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 kde parametry jsou:  
  
 `inputFilename`  
 Název kompilovaného souboru prostředků (včetně přípony). Nástroj Resgen.exe kompiluje pouze soubory s příponami .txt, .restext nebo .resx.  
  
 `outputFilename`  
 Název výstupního souboru Vynecháte-li `outputFilename`, Resgen.exe vytvoří soubor .resources s názvem kořenového souboru `inputFilename` ve stejném adresáři jako `inputFilename`. Pokud `outputFilename` obsahuje cestu k adresáři, tento adresář musí existovat.  
  
 Souboru .resources je poskytován plně kvalifikovaný obor názvů jeho zadáním v názvu souboru a oddělením od názvu kořenového souboru tečkou. Například pokud `outputFilename` je `MyCompany.Libraries.Strings.resources`, obor názvů je MyCompany.Libraries.  
  
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
  
- Soubory .txt a .restext na soubory .resx.  
  
- Soubory .resx na soubory .txt a .restext.  
  
- Soubory .resources na soubory .txt a .restext.  
  
- Soubory .resources na soubory .resx.  
  
 Syntaxe je shodná se syntaxí uvedenou v předchozí části.  
  
 Kromě toho můžete Resgen.exe použít k převodu vložených prostředků v sestavení rozhraní .NET Framework do souboru .resw tor [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
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
 Pokud vytváříte [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, můžete použít prostředky z existující aplikace klasické pracovní plochy. Tyto dva druhy aplikací však používají různé formáty souborů. U aplikací klasické pracovní plochy jsou prostředky v textových souborech (.txt nebo .restext) nebo souborech .resx kompilovány do binárních souborů .resources. V [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, soubory .resw jsou zkompilovány do souborů indexu (PRI) binární balíček prostředků. Můžete použít Resgen.exe extrahováním prostředků ze spustitelného nebo satelitního sestavení a jejich zápis do jednoho nebo více souborů .resw, které lze použít při vývoji přemostění překonání tohoto rozdílu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
> [!IMPORTANT]
>  Visual Studio automaticky zpracovává všechny převody potřebné pro začlenění prostředků v přenosné knihovně do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Použití Resgen.exe přímo pro převod prostředků v sestavení .resw formát souboru je zajímavé pouze pro vývojáře, kteří chtějí vyvíjet [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci mimo sadu Visual Studio.  
  
 Syntaxe pro vygenerování souborů .resw ze sestavení je následující:  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 kde parametry jsou:  
  
 `filename.extension`  
 Název sestavení .NET Framework (soubor .exe nebo .dll). Neobsahuje-li soubor žádné prostředky, nástroj Resgen.exe nevytvoří žádné soubory.  
  
 `outputDirectory`  
 Existující adresář, do nějž budou zapsány soubory .resw. Pokud `outputDirectory` je tento parametr vynechán, budou soubory .resw zapsány do aktuálního adresáře. Nástroj Resgen.exe vytváří jeden soubor .resw pro každý soubor .resources v sestavení. Kořenový název souboru .resw je stejný jako kořenový název souboru .resources.  
  
 Následující příkaz vytvoří pro každý soubor .resources vložený do aplikace MyApp.exe soubor .resw v adresáři Win8Resources:  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Podmíněná kompilace prostředků  
 Od verze rozhraní .NET Framework 4.5, Resgen.exe podporuje podmíněnou kompilaci řetězcových prostředků v textových souborech (.txt a .restext). To umožňuje použití jediného textového souboru prostředků v několika konfiguracích sestavení.  
  
 V souboru .txt nebo .restext je použít `#ifdef`...`#endif` konstrukci pro zahrnutí prostředků do binárního souboru .resources v případě, že je definován symbol, a použít `#if !`... `#endif` konstrukci pro zahrnutí prostředků v případě, že symbol definován není. Při kompilování pak definujete symboly pomocí `/define:` následovaný čárkami oddělený seznam symbolů. Porovnání je notaci citlivé; velikost písmen symbolů definovaných podle `/define` musí rozlišovat velikost písmen symbolů v textových souborech ke kompilaci.  
  
 Například následující soubor pojmenovaný UIResources.rext obsahuje řetězcový prostředek pojmenovaný `AppTitle` , který může přijmout jednu ze tří hodnot, v závislosti na tom, jestli symboly pojmenované `PRODUCTION`, `CONSULT`, nebo `RETAIL` jsou definovány.  
  
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
  
 To vytvoří soubor .resources obsahující dva řetězcové prostředky. Hodnota `AppTitle` prostředků je "My Consulting Company Project Manager".  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generování třídy prostředků se silnými typy  
 Nástroj Resgen.exe podporuje prostředky se silnými typy, což zapouzdřuje přístup k prostředkům vytvořením tříd obsahujících sadu statických vlastností určených pouze pro čtení. To poskytuje alternativu k volání metod <xref:System.Resources.ResourceManager> třídy k načtení prostředků přímým. Povolíte podporu prostředků se silnými typy pomocí `/str` možnost v Resgen.exe, což obalí funkci <xref:System.Resources.Tools.StronglyTypedResourceBuilder> třídy. Pokud zadáte `/str` možnost, výstupem nástroje Resgen.exe je třída obsahující vlastnosti se silnými typy, které odpovídají prostředky, které jsou odkazovány jako vstupní parametr. Tato třída poskytuje k prostředkům dostupným ve zpracovaném souboru přístup se silnými typy určený pouze pro čtení.  
  
 Syntaxe pro vytvoření prostředku se silnými typy je následující:  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry a přepínače jsou následující:  
  
 `inputFilename`  
 Název souboru prostředku (včetně přípony), pro který má být vygenerována třída prostředku se silnými typy. Souborem může být textový soubor, binární soubor .resources nebo soubor založený na jazyce XML. Může mít příponu .txt, .restext, .resw nebo .resources.  
  
 `outputFilename`  
 Název výstupního souboru Pokud `outputFilename` obsahuje cestu k adresáři, tento adresář musí existovat. Vynecháte-li `outputFilename`, Resgen.exe vytvoří soubor .resources s názvem kořenového souboru `inputFilename` ve stejném adresáři jako `inputFilename`.  
  
 `outputFilename` může být založený na textu, XML, binární .resources nebo soubor. Pokud přípona souboru `outputFilename` se liší od přípony souboru `inputFilename`, provádí Resgen.exe převod souborů.  
  
 Pokud `inputFilename` soubor .resources, Resgen.exe zkopíruje Pokud `outputFilename` je také soubor .resources. Pokud `outputFilename` je tento parametr vynechán, Resgen.exe přepíše `inputFilename` s identickým souborem .resources.  
  
 *Jazyk*  
 Jazyk, v němž má být vygenerován zdrojový kód pro třídu prostředků se silnými typy. Možné hodnoty jsou `cs`, `C#`, a `csharp` pro kód jazyka C#, `vb` a `visualbasic` pro kód jazyka Visual Basic, `vbs` a `vbscript` pro kód jazyka VBScript a `c++`, `mc`a `cpp` pro kód C++.  
  
 *namespace*  
 Obor názvů obsahující třídu prostředku se silnými typy. Soubor .resources a třída prostředků by měly mít stejný obor názvů. Informace o zadávání názvů v `outputFilename`, naleznete v tématu [kompilace prostředků do binárního souboru](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling). Pokud *obor názvů* je tento parametr vynechán, třída prostředků není obsažen v oboru názvů.  
  
 *classname*  
 Název třídy prostředku se silnými typy. Tento parametr by měl odpovídat názvu kořenového souboru .resources. Pokud například nástroj Resgen.exe vygeneruje soubor .resources pojmenovaný MyCompany.Libraries.Strings.resources, název třídy prostředků silného typu je Strings. Pokud *classname* je tento parametr vynechán, generovaná třída odvozena od kořenového názvu `outputFilename`. Pokud `outputFilename` je tento parametr vynechán, generovaná třída odvozena od kořenového názvu `inputFilename`.  
  
 *ClassName* nesmí obsahovat neplatné znaky, jako například vložené mezery. Pokud *classname* obsahuje vložené mezery, nebo pokud *classname* je generována ve výchozím nastavení *inputFilename*, a *inputFilename* obsahuje vložené mezery, Resgen.exe nahradí všechny neplatné znaky podtržítkem (_).  
  
 *Název souboru*  
 Název souboru třídy.  
  
 `/publicclass`  
 Vytvoří třídu prostředků se silnými typy veřejnou namísto `internal` (v jazyce C#) nebo `Friend` (v jazyce Visual Basic). To umožňuje přístup k prostředkům z míst mimo sestavení, v němž jsou vloženy.  
  
> [!IMPORTANT]
>  Při vytváření třídy prostředku se silnými typy se musí název souboru .resources shodovat s oborem názvů a názvem třídy generovaného kódu. Nástroj Resgen.exe však umožňuje zadat možnosti, které vytvoří soubor .resources nekompatibilního názvu. Chcete-li toto chování obejít, přejmenujte po vygenerování výstupní soubor.  
  
 Třída prostředků se silnými typy má následující členy:  
  
- Konstruktor bez parametrů, který lze použít k vytvoření instance třídy prostředku silného typu.  
  
- A `static` (C#) nebo `Shared` (Visual Basic) a jen pro čtení `ResourceManager` vlastnost, která vrací <xref:System.Resources.ResourceManager> instanci spravující prostředek silného typu.  
  
- Statický `Culture` vlastnost, která vám umožní nastavit jazykovou verzi použitou k načtení prostředku. Ve výchozím nastavení, je jeho hodnota `null`, což znamená, že se používá aktuální jazyková verze uživatelského rozhraní.  
  
- Jeden `static` (C#) nebo `Shared` (Visual Basic) a vlastnost jen pro čtení pro každý prostředek v souboru .resources. Název vlastnosti je názvem prostředku.  
  
 Například následující příkaz kompiluje soubor prostředek pojmenovaný StringResources.txt do StringResources.resources a vygeneruje třídu pojmenovanou `StringResources` v jazyce Visual Basic zdroji souboru s kódem pojmenovaném StringResources.vb, kterou lze použít pro přístup k prostředku Správce.  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
- [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
