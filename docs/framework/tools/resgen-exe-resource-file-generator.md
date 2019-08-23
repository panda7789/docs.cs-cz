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
ms.openlocfilehash: b018672fbc9e669f6010871a150dd9b060babd88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957997"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (generátor zdrojových souborů)
Nástroj Resource File Generator (Resgen.exe) převádí textové soubory (.txt nebo .restext) a soubory ve formátu prostředků založeném na jazyce XML (.resx) na binární soubory modulu CLR (.resources), které mohou být vloženy do binárního spustitelného souboru modulu nebo satelitního sestavení. (Viz [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe je univerzální nástroj pro převod prostředků, který plní následující úlohy:  
  
- Převádí soubory .txt nebo .restext na soubory .resources nebo .resx. (Formát souborů .restext je shodný s formátem souborů .txt. Přípona .restext však usnadňuje identifikaci textových souborů obsahujících definici prostředků.)  
  
- Převádí soubory .resources na textové soubory nebo soubory .resx.  
  
- Převádí soubory .resx na textové soubory nebo soubory .resources.  
  
- Extrahuje řetězcové prostředky ze sestavení do souboru. resw, který je vhodný pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci.  
  
- Vytvoří třídu silného typu, která poskytuje přístup k jednotlivým pojmenovaným prostředkům <xref:System.Resources.ResourceManager> a instanci.  
  
 Pokud nástroj Resgen.exe z jakéhokoli důvodu selže, je návratová hodnota –1.  
  
 Chcete-li získat nápovědu k nástroji Resgen.exe, lze použít následující příkaz bez jakýchkoli možností a zobrazit tak syntaxi příkazů a možnosti nástroje Resgen.exe:  
  
```  
resgen  
```  
  
 Můžete použít `/?` také přepínač:  
  
```  
resgen /?  
```  
  
 Použijete-li Resgen, exe ke generování binárních souborů. Resources, můžete použít kompilátor jazyka pro vložení binárních souborů do spustitelných sestavení, nebo můžete použít [linker sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) a zkompilovat je do satelitních sestavení.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|`/define:` *symbol1*[, *symbol2*,...]|Počínaje .NET Framework 4,5 podporuje Podmíněná kompilace v souborech prostředků (. txt nebo. restext), které jsou založené na textovém souboru (. txt nebo.). Pokud *symbol* odpovídá symbolu obsaženému ve vstupním textovém souboru v rámci `#ifdef` konstrukce, je prostředek přidruženého řetězce obsažen v souboru. Resources. Pokud vstupní textový soubor obsahuje `#if !` příkaz se symbolem, který není definován `/define` přepínačem, je prostředek přidruženého řetězce obsažen v souboru prostředků.<br /><br /> `/define`je ignorován, je-li použit s netextovým soubory. Rozlišují se malá a velká písmena.<br /><br /> Další informace o této možnosti naleznete v části [bezpodmínečně zkompilování prostředků](#Conditional) dále v tomto tématu.|  
|`useSourcePath`|Určuje, že k vyhodnocení relativních cest k souborům má být použit aktuální adresář vstupního souboru.|  
|`/compile`|Umožňuje zadat několik textových souborů nebo souborů .resx pro převod na několik souborů .resources jednou hromadnou operací. Pokud tuto možnost nezadáte, lze zadat pouze jeden argument vstupního souboru. Výstupní soubory jsou pojmenovány *filename*. Resources.<br /><br /> Tuto možnost nelze použít s `/str:` možností.<br /><br /> Další informace o této možnosti naleznete v tématu [kompilace nebo převod více souborů](#Multiple) dále v tomto tématu.|  
|`/r:``assembly`|Odkazuje na metadata z určeného sestavení. Používá se při převodu souborů .resx a umožňuje nástroji Resgen.exe serializovat a deserializovat prostředky objektů. Je podobný `/reference:` možnosti nebo `/r:` pro kompilátory Visual Basic C# a.|  
|`filename.extension`|Určuje název vstupního souboru, který má být převeden. Pokud používáte první lengthier syntaxi příkazového řádku prezentovanou před touto tabulkou, `extension` musí být jedna z následujících:<br /><br /> .txt nebo .restext<br /> Textový soubor, který má být převeden na soubor .resources nebo .resx. Textové soubory mohou obsahovat pouze řetězcové prostředky. Informace o formátu souboru naleznete v části "prostředky v textových souborech" v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Soubor prostředků založený na jazyce XML, který má být převeden na soubor .resources nebo textový soubor (.txt nebo .restext).<br /><br /> .resources<br /> Binární soubor prostředků, který má být převeden na soubor .resx nebo textový soubor (.txt nebo .restext).<br /><br /> Pokud používáte druhou, kratší syntaxe příkazového řádku prezentovaná před touto tabulkou, `extension` musí být následující:<br /><br /> .exe nebo .dll<br /> .NET Framework sestavení (spustitelný soubor nebo knihovna), jehož řetězcové prostředky mají být extrahovány do souboru. resw pro použití při [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] vývoji aplikací.|  
|`outputFilename.extension`|Určuje název a typ souboru prostředků, který má být vytvořen.<br /><br /> Při převodu ze souboru .txt, .restext nebo .resx na soubor .resources je tento argument nepovinný. Pokud nezadáte `outputFilename`, nástroj Resgen. exe připojí k vstupu `filename` rozšíření. Resources a zapíše soubor do adresáře, který obsahuje `filename,extension`.<br /><br /> Při převodu ze souboru. Resources je argumentpovinný.`outputFilename.extension` Při převodu souboru .resources na soubor prostředků založený na jazyce XML zadejte název souboru s příponou .resx. Při převodu souboru .resources na textový soubor zadejte název souboru s příponou .txt nebo restext. Soubor .resources by měl být na soubor .txt převeden pouze v případě, že soubor .resources obsahuje výhradně řetězcové hodnoty.|  
|`outputDirectory`|Pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace určí adresář, ve kterém se bude zapisovat soubor. resw, který obsahuje prostředky řetězce `filename.extension` v. `outputDirectory`již musí existovat.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Vytvoří soubor třídy prostředků se silnými typy v programovacím jazyce zadaném v `language` možnosti. `language`může se skládat z jednoho z následujících literálů:<br /><br /> – Pro C#: `c#`, `cs`nebo. `csharp`<br />– Pro Visual Basic: `vb` nebo `visualbasic`.<br />– Pro VBScript: `vbs` nebo `vbscript`.<br />– Pro C++: `c++`, `mc`nebo. `cpp`<br />– Pro JavaScript: `js`, `jscript`, nebo `javascript`.<br /><br /> Možnost určuje výchozí obor názvů projektu `classname` , možnost určuje název `filename` generované třídy a možnost určuje název souboru třídy. `namespace`<br /><br /> Možnost umožňuje pouze jeden vstupní soubor, takže jej nelze použít `/compile` s možností. `/str:`<br /><br /> Je `namespace` -li parametr `classname` zadán, ale není, název třídy je odvozen z názvu výstupního souboru (například podtržítka jsou nahrazena tečkami). Prostředky se silnými typy možná důsledkem toho nebudou fungovat správně. Chcete-li se tomuto problému vyhnout, zadejte název třídy i název výstupního souboru.<br /><br /> Další informace o této možnosti naleznete v části [generování třídy prostředků se silnými typy](#Strong) dále v tomto tématu.|  
|`/publicClass`|Vytvoří třídu prostředků se silnými typy jako veřejnou třídu. Ve výchozím nastavení je `internal` Třída prostředků v C# a `Friend` Visual Basic.<br /><br /> Tato možnost je ignorována, `/str:` Pokud není použita možnost.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Nástroj Resgen.exe a typy souborů prostředků  
 Aby nástroj Resgen.exe mohl úspěšně převádět prostředky, textové soubory a soubory .resx, musí dodržovat správný formát.  
  
### <a name="text-txt-and-restext-files"></a>Textové soubory (.txt a .restext)  
 Textové soubory (.txt nebo .restext) mohou obsahovat výhradně řetězcové prostředky. Řetězcové prostředky jsou užitečné při psaní aplikace, která musí mít řetězce přeloženy do několika jazyků. Lze například snadno lokalizovat řetězce nabídky použitím příslušného řetězcového prostředku. Nástroj Resgen.exe čte textové soubory obsahující dvojice název/hodnota, kde název je řetězec popisující prostředek a hodnota je samotný řetězec prostředku.  
  
> [!NOTE]
> Informace o formátu souborů. txt a. restext naleznete v části "prostředky v textových souborech" v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Neobsahuje-li textový soubor s prostředky pouze znaky z rozsahu základní latinky (do U+007F), musí být uložen s kódováním UTF-8 nebo Unicode (UTF-16). Při zpracovávání textového souboru uloženého s kódováním ANSI nástroj Resgen.exe odstraňuje rozšířené znaky ANSI.  
  
 Nástroj Resgen.exe kontroluje, zda textový soubor obsahuje duplicitní názvy prostředků. Obsahuje-li textový soubor duplicitní názvy prostředků, nástroj Resgen.exe vygeneruje upozornění a bude ignorovat druhou hodnotu.  
  
### <a name="resx-files"></a>Soubory .resx  
 Formát souboru prostředků .resx sestává ze záznamů jazyka XML. Uvnitř těchto záznamů jazyka XML lze zadávat řetězcové prostředky jako v textových souborech. Hlavní výhodou souborů .resx oproti textovým souborům je možnost zadávat nebo vkládat objekty. Při zobrazení souboru .resx lze vidět binární podobu vloženého objektu (například obrázku), pokud je tato binární informace součástí manifestu prostředku. Stejně jako textové soubory lze i soubory .resx otevřít v textovém editoru (například Poznámkový blok nebo Microsoft Word) a zapisovat, analyzovat či upravovat jejich obsah. To vyžaduje dobrou znalost značek XML a struktury souboru .resx. Další informace o formátu souboru. resx naleznete v části "prostředky v souborech. resx" v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Aby bylo možné vytvořit soubor. Resources, který obsahuje vložené neřetězcové objekty, je nutné buď pomocí nástroje Resgen. exe převést soubor. resx obsahující objekty nebo přidat prostředky objektu do souboru přímo z kódu voláním metod poskytovaných <xref:System.Resources.ResourceWriter> Deník.  
  
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
 Nástroj Resgen. exe lze použít různými způsoby: Chcete-li zkompilovat textový soubor nebo soubor prostředků založený na jazyce XML do binárního souboru, provést převod mezi formáty souborů prostředků a vygenerovat třídu, která zabalí <xref:System.Resources.ResourceManager> funkce a poskytuje přístup k prostředkům. Tato část poskytuje podrobné informace o každém úkolu:  
  
- [Kompilace prostředků do binárního souboru](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
- [Převod mezi typy souborů prostředků](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
- [Kompilace nebo převod více souborů](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
- [Export prostředků do souboru. resw](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
- [Podmíněně kompilování prostředků](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generování třídy prostředků se silnými typy](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilace prostředků do binárního souboru  
 Nejběžnější použití nástroje Resgen.exe je kompilování textového souboru prostředků (soubor .txt nebo .restext) nebo souboru prostředků založeného na jazyce XML (soubor .resx) do binárního souboru .resources. Výstupní soubor pak může být vložen do hlavního sestavení kompilátorem jazyka nebo v satelitním sestavení pomocí [linkeru sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Syntaxe pro kompilaci souboru prostředků je následující:  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 kde parametry jsou:  
  
 `inputFilename`  
 Název kompilovaného souboru prostředků (včetně přípony). Nástroj Resgen.exe kompiluje pouze soubory s příponami .txt, .restext nebo .resx.  
  
 `outputFilename`  
 Název výstupního souboru Vynecháte `outputFilename`-li nástroj Resgen. exe, vytvoří soubor. Resources s `inputFilename` názvem kořenového souboru ve stejném `inputFilename`adresáři jako. Pokud `outputFilename` zahrnuje cestu k adresáři, musí existovat adresář.  
  
 Souboru .resources je poskytován plně kvalifikovaný obor názvů jeho zadáním v názvu souboru a oddělením od názvu kořenového souboru tečkou. Například pokud `outputFilename` je `MyCompany.Libraries.Strings.resources`, obor názvů je spolecnost. Libraries.  
  
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
  
 Nástroj Resgen. exe navíc můžete použít k převodu integrovaných prostředků v .NET Framework sestavení na [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace pro používání souborů. resw.  
  
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
 Pomocí `/compile` přepínače můžete převést seznam souborů prostředků z jednoho formátu na jiný v rámci jedné operace. Syntaxe je následující:  
  
```  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Následující příkaz zkompiluje tři soubory, StringResources.txt, TableResources.resw a ImageResources.resw, do oddělených souborů .resources pojmenovaných StringResources.resources, TableResources.resources a ImageResources.resources.  
  
```  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Exportování prostředků do souboru .resw  
 Pokud vyvíjíte [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci, můžete chtít použít prostředky z existující desktopové aplikace. Tyto dva druhy aplikací však používají různé formáty souborů. U aplikací klasické pracovní plochy jsou prostředky v textových souborech (.txt nebo .restext) nebo souborech .resx kompilovány do binárních souborů .resources. V [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacích jsou soubory. resw zkompilovány do binárních souborů indexu prostředků balíčku (PRI). Nástroj Resgen. exe můžete použít k přemostění této mezery extrahováním prostředků ze spustitelného souboru nebo satelitního sestavení a jejich zápisem do jednoho nebo více souborů. resw, které lze použít při [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] vývoji aplikace.  
  
> [!IMPORTANT]
> Visual Studio automaticky zpracovává všechny převody nutné pro zahrnutí prostředků do přenositelné knihovny do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Použití nástroje Resgen. exe přímo k převedení prostředků v sestavení na formát souboru. resw je důležité pouze pro vývojáře, kteří chtějí vyvíjet [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci mimo sadu Visual Studio.  
  
 Syntaxe pro vygenerování souborů .resw ze sestavení je následující:  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 kde parametry jsou:  
  
 `filename.extension`  
 Název sestavení .NET Framework (soubor .exe nebo .dll). Neobsahuje-li soubor žádné prostředky, nástroj Resgen.exe nevytvoří žádné soubory.  
  
 `outputDirectory`  
 Existující adresář, do nějž budou zapsány soubory .resw. Pokud `outputDirectory` je vynechán, soubory. resw jsou zapsány do aktuálního adresáře. Nástroj Resgen.exe vytváří jeden soubor .resw pro každý soubor .resources v sestavení. Kořenový název souboru .resw je stejný jako kořenový název souboru .resources.  
  
 Následující příkaz vytvoří pro každý soubor .resources vložený do aplikace MyApp.exe soubor .resw v adresáři Win8Resources:  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Podmíněná kompilace prostředků  
 Počínaje .NET Framework 4,5 nástroj Resgen. exe podporuje podmíněné kompilování řetězcových prostředků v souborech textu (. txt a. restext). To umožňuje použití jediného textového souboru prostředků v několika konfiguracích sestavení.  
  
 V souboru. txt nebo. restext použijte `#ifdef`...`#endif` konstrukce pro zahrnutí prostředku do binárního souboru. Resources, pokud je definován symbol, a použijete `#if !`... `#endif` konstrukce pro zahrnutí prostředku, pokud není definován symbol. V době kompilace pak definujete symboly pomocí `/define:` možnosti následované čárkami odděleným seznamem symbolů. Porovnání je použita; velikost symbolů definovaných pomocí `/define` musí odpovídat znakům v textových souborech, které mají být zkompilovány.  
  
 Například následující soubor s názvem UIResources. rext obsahuje `AppTitle` prostředek řetězce s názvem, který může mít jednu ze tří hodnot v závislosti na tom, zda jsou definovány symboly s názvem `RETAIL` `PRODUCTION`, `CONSULT`nebo.  
  
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
  
 To vytvoří soubor .resources obsahující dva řetězcové prostředky. Hodnota `AppTitle` prostředku je "My konzultační společnost vedoucí projektu".  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generování třídy prostředků se silnými typy  
 Nástroj Resgen.exe podporuje prostředky se silnými typy, což zapouzdřuje přístup k prostředkům vytvořením tříd obsahujících sadu statických vlastností určených pouze pro čtení. To poskytuje alternativu k volání metod <xref:System.Resources.ResourceManager> třídy přímo k načtení prostředků. Podporu prostředků se silnými typy lze povolit pomocí `/str` možnosti v nástroji Resgen. exe, která zabalí funkce <xref:System.Resources.Tools.StronglyTypedResourceBuilder> třídy. Pokud zadáte `/str` možnost, je výstupem nástroje Resgen. exe třída, která obsahuje vlastnosti silného typu, které odpovídají prostředkům, na které je odkazováno ve vstupním parametru. Tato třída poskytuje k prostředkům dostupným ve zpracovaném souboru přístup se silnými typy určený pouze pro čtení.  
  
 Syntaxe pro vytvoření prostředku se silnými typy je následující:  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry a přepínače jsou následující:  
  
 `inputFilename`  
 Název souboru prostředku (včetně přípony), pro který má být vygenerována třída prostředku se silnými typy. Souborem může být textový soubor, binární soubor .resources nebo soubor založený na jazyce XML. Může mít příponu .txt, .restext, .resw nebo .resources.  
  
 `outputFilename`  
 Název výstupního souboru Pokud `outputFilename` zahrnuje cestu k adresáři, musí existovat adresář. Vynecháte `outputFilename`-li nástroj Resgen. exe, vytvoří soubor. Resources s `inputFilename` názvem kořenového souboru ve stejném `inputFilename`adresáři jako.  
  
 `outputFilename`může to být textový soubor. Resources nebo Binary. Resources založený na jazyce XML. Pokud `outputFilename` je přípona souboru jiného než `inputFilename`Přípona souboru, nástroj Resgen. exe provede převod souboru.  
  
 Pokud `inputFilename` je soubor. Resources, nástroj Resgen. exe zkopíruje soubor. Resources, pokud `outputFilename` je také souborem. Resources. Pokud `outputFilename` je tento parametr vynechán, nástroj Resgen. exe `inputFilename` přepíše stejný soubor. Resources.  
  
 *Language*  
 Jazyk, v němž má být vygenerován zdrojový kód pro třídu prostředků se silnými typy. Možné hodnoty jsou `cs`, `C#`, `csharp` `vb` `mc`a pro C# kód, VisualBasickód`vbscript` a pro kód`c++`jazyka VBScript a,, `visualbasic` `vbs` a `cpp` pro C++ kód.  
  
 *namespace*  
 Obor názvů obsahující třídu prostředku se silnými typy. Soubor .resources a třída prostředků by měly mít stejný obor názvů. Informace o určení oboru názvů v `outputFilename`naleznete v tématu [kompilace prostředků do binárního souboru](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling). Pokud je *obor názvů* vynechán, Třída prostředků není obsažena v oboru názvů.  
  
 *NázevTřídy*  
 Název třídy prostředku se silnými typy. Tento parametr by měl odpovídat názvu kořenového souboru .resources. Pokud například nástroj Resgen.exe vygeneruje soubor .resources pojmenovaný MyCompany.Libraries.Strings.resources, název třídy prostředků silného typu je Strings. Pokud je název *ClassName* vynechán, vygenerovaná třída je odvozena z kořenového názvu `outputFilename`. Pokud `outputFilename` je vynecháno, vygenerovaná třída je odvozena z kořenového `inputFilename`názvu.  
  
 *ClassName* nemůže obsahovat neplatné znaky, jako jsou například vložené mezery. Pokud *ClassName* obsahuje vložené mezery nebo pokud se ve výchozím nastavení generuje *ClassName* z *inputFilename*a *inputFilename* obsahuje vložené mezery, nástroj Resgen. exe nahradí všechny neplatné znaky podtržítkem (\_).  
  
 *Bitmap*  
 Název souboru třídy.  
  
 `/publicclass`  
 Zpřístupňuje třídu prostředků se silnými typy spíše `internal` než ( C#v) `Friend` nebo (v Visual Basic). To umožňuje přístup k prostředkům z míst mimo sestavení, v němž jsou vloženy.  
  
> [!IMPORTANT]
> Při vytváření třídy prostředku se silnými typy se musí název souboru .resources shodovat s oborem názvů a názvem třídy generovaného kódu. Nástroj Resgen.exe však umožňuje zadat možnosti, které vytvoří soubor .resources nekompatibilního názvu. Chcete-li toto chování obejít, přejmenujte po vygenerování výstupní soubor.  
  
 Třída prostředků se silnými typy má následující členy:  
  
- Konstruktor bez parametrů, který lze použít k vytvoření instance třídy prostředku silného typu.  
  
- `ResourceManager` <xref:System.Resources.ResourceManager> Vlastnost () nebo `Shared` (Visual Basic) a vlastnost jen pro čtení, která vrací instanci, která spravuje prostředek silného typu.C# `static`  
  
- Statická `Culture` vlastnost, která umožňuje nastavit jazykovou verzi použitou pro načtení prostředků. Ve výchozím nastavení je `null`jeho hodnota, což znamená, že je použita aktuální jazyková verze uživatelského rozhraní.  
  
- Jedna `static` (C#) nebo `Shared` (Visual Basic) a vlastnost jen pro čtení pro každý prostředek v souboru. Resources. Název vlastnosti je názvem prostředku.  
  
 Následující příkaz například zkompiluje soubor prostředků s názvem StringResources. txt do StringResources. Resources a vygeneruje třídu s názvem `StringResources` v souboru zdrojového kódu Visual Basic s názvem StringResources. vb, kterou lze použít pro přístup k prostředku. Programu.  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
- [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
