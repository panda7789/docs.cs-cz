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
ms.openlocfilehash: 5fc2bcb03ae6814d69e229ba083c1d5c44ae8ff3
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204613"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (generátor zdrojových souborů)
Nástroj Resource File Generator (Resgen.exe) převádí textové soubory (.txt nebo .restext) a soubory ve formátu prostředků založeném na jazyce XML (.resx) na binární soubory modulu CLR (.resources), které mohou být vloženy do binárního spustitelného souboru modulu nebo satelitního sestavení. (See [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).)  
  
 Resgen.exe je univerzální nástroj pro převod prostředků, který plní následující úlohy:  
  
- Převádí soubory .txt nebo .restext na soubory .resources nebo .resx. (Formát souborů .restext je shodný s formátem souborů .txt. Přípona .restext však usnadňuje identifikaci textových souborů obsahujících definici prostředků.)  
  
- Převádí soubory .resources na textové soubory nebo soubory .resx.  
  
- Převádí soubory .resx na textové soubory nebo soubory .resources.  
  
- Extracts the string resources from an assembly into a .resw file that is suitable for use in a Windows 8.x Store app.  
  
- Creates a strongly typed class that provides access to individual named resources and to the <xref:System.Resources.ResourceManager> instance.  
  
 Pokud nástroj Resgen.exe z jakéhokoli důvodu selže, je návratová hodnota –1.  
  
 To get help with Resgen.exe, you can use the following command, with no options specified, to display the command syntax and options for Resgen.exe:  
  
```console  
resgen  
```  
  
 You can also use the `/?` switch:  
  
```console  
resgen /?  
```  
  
 If you use Resgen.exe to generate binary .resources files, you can use a language compiler to embed the binary files into executable assemblies, or you can use the [Assembly Linker (Al.exe)](al-exe-assembly-linker.md) to compile them into satellite assemblies.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
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
|`/define:` *symbol1*[, *symbol2*,...]|Starting with the .NET Framework 4.5, supports conditional compilation in text-based (.txt or .restext) resource files. If *symbol* corresponds to a symbol included in the input text file within a `#ifdef` construct, the associated string resource is included in the .resources file. If the input text file includes an `#if !` statement with a symbol that is not defined by the `/define` switch, the associated string resource is included in the resources file.<br /><br /> `/define` is ignored if it is used with non-text files. Rozlišují se malá a velká písmena.<br /><br /> For more information about this option, see [Conditionally Compiling Resources](#Conditional) later in this topic.|  
|`useSourcePath`|Určuje, že k vyhodnocení relativních cest k souborům má být použit aktuální adresář vstupního souboru.|  
|`/compile`|Umožňuje zadat několik textových souborů nebo souborů .resx pro převod na několik souborů .resources jednou hromadnou operací. Pokud tuto možnost nezadáte, lze zadat pouze jeden argument vstupního souboru. Output files are named *filename*.resources.<br /><br /> This option cannot be used with the `/str:` option.<br /><br /> For more information about this option, see [Compiling or Converting Multiple Files](#Multiple) later in this topic.|  
|`/r:``assembly`|Odkazuje na metadata z určeného sestavení. Používá se při převodu souborů .resx a umožňuje nástroji Resgen.exe serializovat a deserializovat prostředky objektů. It is similar to the `/reference:` or `/r:` options for the C# and Visual Basic compilers.|  
|`filename.extension`|Určuje název vstupního souboru, který má být převeden. If you're using the first, lengthier command-line syntax presented before this table,  `extension` must be one of the following:<br /><br /> .txt nebo .restext<br /> Textový soubor, který má být převeden na soubor .resources nebo .resx. Textové soubory mohou obsahovat pouze řetězcové prostředky. For information about the file format, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Soubor prostředků založený na jazyce XML, který má být převeden na soubor .resources nebo textový soubor (.txt nebo .restext).<br /><br /> .resources<br /> Binární soubor prostředků, který má být převeden na soubor .resx nebo textový soubor (.txt nebo .restext).<br /><br /> If you're using the second, shorter command-line syntax presented before this table, `extension` must be the following:<br /><br /> .exe nebo .dll<br /> A .NET Framework assembly (executable or library) whose string resources are to be extracted to a .resw file for use in developing Windows 8.x Store apps.|  
|`outputFilename.extension`|Určuje název a typ souboru prostředků, který má být vytvořen.<br /><br /> Při převodu ze souboru .txt, .restext nebo .resx na soubor .resources je tento argument nepovinný. If you do not specify `outputFilename`, Resgen.exe appends a .resources extension to the input `filename` and writes the file to the directory that contains `filename,extension`.<br /><br /> The `outputFilename.extension` argument is mandatory when converting from a .resources file. Při převodu souboru .resources na soubor prostředků založený na jazyce XML zadejte název souboru s příponou .resx. Při převodu souboru .resources na textový soubor zadejte název souboru s příponou .txt nebo restext. Soubor .resources by měl být na soubor .txt převeden pouze v případě, že soubor .resources obsahuje výhradně řetězcové hodnoty.|  
|`outputDirectory`|For Windows 8.x Store apps, specifies the directory in which a .resw file that contains the string resources in `filename.extension` will be written. `outputDirectory` must already exist.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Creates a strongly typed resource class file in the programming language specified in the `language` option. `language` can consist of one of the following literals:<br /><br /> -   For C#: `c#`, `cs`, or `csharp`.<br />-   For Visual Basic: `vb` or `visualbasic`.<br />-   For VBScript: `vbs` or `vbscript`.<br />-   For C++: `c++`, `mc`, or `cpp`.<br />-   For JavaScript: `js`, `jscript`, or `javascript`.<br /><br /> The `namespace` option specifies the project's default namespace, the `classname` option specifies the name of the generated class, and the `filename` option specifies the name of the class file.<br /><br /> The `/str:` option allows only one input file, so it cannot be used with the `/compile` option.<br /><br /> If `namespace` is specified but `classname` is not, the class name is derived from the output file name (for example, underscores are substituted for periods). Prostředky se silnými typy možná důsledkem toho nebudou fungovat správně. Chcete-li se tomuto problému vyhnout, zadejte název třídy i název výstupního souboru.<br /><br /> For more information about this option, see [Generating a Strongly Typed Resource Class](#Strong) later in this topic.|  
|`/publicClass`|Vytvoří třídu prostředků se silnými typy jako veřejnou třídu. By default, the resource class is `internal` in C# and `Friend` in Visual Basic.<br /><br /> This option is ignored if the `/str:` option is not used.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Nástroj Resgen.exe a typy souborů prostředků  
 Aby nástroj Resgen.exe mohl úspěšně převádět prostředky, textové soubory a soubory .resx, musí dodržovat správný formát.  
  
### <a name="text-txt-and-restext-files"></a>Textové soubory (.txt a .restext)  
 Textové soubory (.txt nebo .restext) mohou obsahovat výhradně řetězcové prostředky. Řetězcové prostředky jsou užitečné při psaní aplikace, která musí mít řetězce přeloženy do několika jazyků. Lze například snadno lokalizovat řetězce nabídky použitím příslušného řetězcového prostředku. Nástroj Resgen.exe čte textové soubory obsahující dvojice název/hodnota, kde název je řetězec popisující prostředek a hodnota je samotný řetězec prostředku.  
  
> [!NOTE]
> For information about the format of .txt and .restext files, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Neobsahuje-li textový soubor s prostředky pouze znaky z rozsahu základní latinky (do U+007F), musí být uložen s kódováním UTF-8 nebo Unicode (UTF-16). Při zpracovávání textového souboru uloženého s kódováním ANSI nástroj Resgen.exe odstraňuje rozšířené znaky ANSI.  
  
 Nástroj Resgen.exe kontroluje, zda textový soubor obsahuje duplicitní názvy prostředků. Obsahuje-li textový soubor duplicitní názvy prostředků, nástroj Resgen.exe vygeneruje upozornění a bude ignorovat druhou hodnotu.  
  
### <a name="resx-files"></a>Soubory .resx  
 Formát souboru prostředků .resx sestává ze záznamů jazyka XML. Uvnitř těchto záznamů jazyka XML lze zadávat řetězcové prostředky jako v textových souborech. Hlavní výhodou souborů .resx oproti textovým souborům je možnost zadávat nebo vkládat objekty. Při zobrazení souboru .resx lze vidět binární podobu vloženého objektu (například obrázku), pokud je tato binární informace součástí manifestu prostředku. Stejně jako textové soubory lze i soubory .resx otevřít v textovém editoru (například Poznámkový blok nebo Microsoft Word) a zapisovat, analyzovat či upravovat jejich obsah. To vyžaduje dobrou znalost značek XML a struktury souboru .resx. For more details on the .resx file format, see the "Resources in .resx Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).  
  
 In order to create a .resources file that contains embedded nonstring objects, you must either use Resgen.exe to convert a .resx file containing objects or add the object resources to your file directly from code by calling the methods provided by the <xref:System.Resources.ResourceWriter> class.  
  
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
 You can use Resgen.exe in diverse ways: to compile a text-based or XML-based resource file into a binary file, to convert between resource file formats, and to generate a class that wraps <xref:System.Resources.ResourceManager> functionality and provides access to resources. Tato část poskytuje podrobné informace o každém úkolu:  
  
- [Compiling Resources into a Binary File](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Converting Between Resource File Types](resgen-exe-resource-file-generator.md#Convert)  
  
- [Compiling or Converting Multiple Files](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Exporting Resources to a .resw File](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Conditionally Compiling Resources](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generating a Strongly Typed Resource Class](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilace prostředků do binárního souboru  
 Nejběžnější použití nástroje Resgen.exe je kompilování textového souboru prostředků (soubor .txt nebo .restext) nebo souboru prostředků založeného na jazyce XML (soubor .resx) do binárního souboru .resources. The output file then can be embedded in a main assembly by a language compiler or in a satellite assembly by [Assembly Linker (AL.exe)](al-exe-assembly-linker.md).  
  
 Syntaxe pro kompilaci souboru prostředků je následující:  
  
```console  
resgen inputFilename [outputFilename]   
```  
  
 kde parametry jsou:  
  
 `inputFilename`  
 Název kompilovaného souboru prostředků (včetně přípony). Nástroj Resgen.exe kompiluje pouze soubory s příponami .txt, .restext nebo .resx.  
  
 `outputFilename`  
 Název výstupního souboru If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`. If `outputFilename` includes a directory path, the directory must exist.  
  
 Souboru .resources je poskytován plně kvalifikovaný obor názvů jeho zadáním v názvu souboru a oddělením od názvu kořenového souboru tečkou. For example, if `outputFilename` is `MyCompany.Libraries.Strings.resources`, the namespace is MyCompany.Libraries.  
  
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
  
 In addition, you can use Resgen.exe to convert embedded resources in a .NET Framework assembly to a .resw file tor Windows 8.x Store apps.  
  
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
 You can use the `/compile` switch to convert a list of resource files from one format to another in a single operation. Syntaxe je následující:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Následující příkaz zkompiluje tři soubory, StringResources.txt, TableResources.resw a ImageResources.resw, do oddělených souborů .resources pojmenovaných StringResources.resources, TableResources.resources a ImageResources.resources.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Exportování prostředků do souboru .resw  
 If you're developing a Windows 8.x Store app, you may want to use resources from an existing desktop app. Tyto dva druhy aplikací však používají různé formáty souborů. U aplikací klasické pracovní plochy jsou prostředky v textových souborech (.txt nebo .restext) nebo souborech .resx kompilovány do binárních souborů .resources. In Windows 8.x Store apps, .resw files are compiled into binary package resource index (PRI) files. You can use Resgen.exe to bridge this gap by extracting resources from an executable or a satellite assembly and writing them to one or more .resw files that can be used when developing a Windows 8.x Store app.  
  
> [!IMPORTANT]
> Visual Studio automatically handles all conversions necessary for incorporating the resources in a portable library into a Windows 8.x Store app. Using Resgen.exe directly to convert the resources in an assembly to .resw file format is of interest only to developers who want to develop a Windows 8.x Store app outside of Visual Studio.  
  
 Syntaxe pro vygenerování souborů .resw ze sestavení je následující:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 kde parametry jsou:  
  
 `filename.extension`  
 Název sestavení .NET Framework (soubor .exe nebo .dll). Neobsahuje-li soubor žádné prostředky, nástroj Resgen.exe nevytvoří žádné soubory.  
  
 `outputDirectory`  
 Existující adresář, do nějž budou zapsány soubory .resw. If `outputDirectory` is omitted, .resw files are written to the current directory. Nástroj Resgen.exe vytváří jeden soubor .resw pro každý soubor .resources v sestavení. Kořenový název souboru .resw je stejný jako kořenový název souboru .resources.  
  
 Následující příkaz vytvoří pro každý soubor .resources vložený do aplikace MyApp.exe soubor .resw v adresáři Win8Resources:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Podmíněná kompilace prostředků  
 Starting with the .NET Framework 4.5, Resgen.exe supports conditional compilation of string resources in text (.txt and .restext) files. To umožňuje použití jediného textového souboru prostředků v několika konfiguracích sestavení.  
  
 In a .txt or .restext file, you use the `#ifdef`…`#endif` construct to include a resource in the binary .resources file if a symbol is defined, and you use the `#if !`... `#endif` construct to include a resource if a symbol is not defined. At compile time, you then define symbols by using the `/define:` option followed by a comma-delimited list of symbols. The comparison is cased-sensitive; the case of symbols defined by `/define` must match the case of symbols in the text files to be compiled.  
  
 For example, the following file named UIResources.rext includes a string resource named `AppTitle` that can take one of three values, depending on whether symbols named `PRODUCTION`, `CONSULT`, or `RETAIL` are defined.  
  
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
  
 To vytvoří soubor .resources obsahující dva řetězcové prostředky. The value of the `AppTitle` resource is "My Consulting Company Project Manager".  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generování třídy prostředků se silnými typy  
 Nástroj Resgen.exe podporuje prostředky se silnými typy, což zapouzdřuje přístup k prostředkům vytvořením tříd obsahujících sadu statických vlastností určených pouze pro čtení. This provides an alternative to calling the methods of the <xref:System.Resources.ResourceManager> class directly to retrieve resources. You can enable strongly typed resource support by using the `/str` option in Resgen.exe, which wraps the functionality of the <xref:System.Resources.Tools.StronglyTypedResourceBuilder> class. When you specify the `/str` option, the output of Resgen.exe is a class that contains strongly typed properties that match the resources that are referenced in the input parameter. Tato třída poskytuje k prostředkům dostupným ve zpracovaném souboru přístup se silnými typy určený pouze pro čtení.  
  
 Syntaxe pro vytvoření prostředku se silnými typy je následující:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry a přepínače jsou následující:  
  
 `inputFilename`  
 Název souboru prostředku (včetně přípony), pro který má být vygenerována třída prostředku se silnými typy. Souborem může být textový soubor, binární soubor .resources nebo soubor založený na jazyce XML. Může mít příponu .txt, .restext, .resw nebo .resources.  
  
 `outputFilename`  
 Název výstupního souboru If `outputFilename` includes a directory path, the directory must exist. If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`.  
  
 `outputFilename` can be a text-based, XML-based, or binary .resources file. If the file extension of `outputFilename` is different from the file extension of `inputFilename`, Resgen.exe performs the file conversion.  
  
 If `inputFilename` is a .resources file, Resgen.exe copies the .resources file if `outputFilename` is also a .resources file. If `outputFilename` is omitted, Resgen.exe overwrites `inputFilename` with an identical .resources file.  
  
 *language*  
 Jazyk, v němž má být vygenerován zdrojový kód pro třídu prostředků se silnými typy. Possible values are `cs`, `C#`, and `csharp` for C# code, `vb` and `visualbasic` for Visual Basic code, `vbs` and `vbscript` for VBScript code, and `c++`, `mc`, and `cpp` for C++ code.  
  
 *namespace*  
 Obor názvů obsahující třídu prostředku se silnými typy. Soubor .resources a třída prostředků by měly mít stejný obor názvů. For information about specifying the namespace in the `outputFilename`, see [Compiling Resources into a Binary File](resgen-exe-resource-file-generator.md#Compiling). If *namespace* is omitted, the resource class is not contained in a namespace.  
  
 *classname*  
 Název třídy prostředku se silnými typy. Tento parametr by měl odpovídat názvu kořenového souboru .resources. Pokud například nástroj Resgen.exe vygeneruje soubor .resources pojmenovaný MyCompany.Libraries.Strings.resources, název třídy prostředků silného typu je Strings. If *classname* is omitted, the generated class is derived from the root name of `outputFilename`. If `outputFilename` is omitted, the generated class is derived from the root name of `inputFilename`.  
  
 *classname* cannot contain invalid characters such as embedded spaces. If *classname* contains embedded spaces, or if *classname* is generated by default from *inputFilename*, and *inputFilename* contains embedded spaces, Resgen.exe replaces all invalid characters with an underscore (\_).  
  
 *filename*  
 Název souboru třídy.  
  
 `/publicclass`  
 Makes the strongly typed resource class public rather than `internal` (in C#) or `Friend` (in Visual Basic). To umožňuje přístup k prostředkům z míst mimo sestavení, v němž jsou vloženy.  
  
> [!IMPORTANT]
> Při vytváření třídy prostředku se silnými typy se musí název souboru .resources shodovat s oborem názvů a názvem třídy generovaného kódu. Nástroj Resgen.exe však umožňuje zadat možnosti, které vytvoří soubor .resources nekompatibilního názvu. Chcete-li toto chování obejít, přejmenujte po vygenerování výstupní soubor.  
  
 Třída prostředků se silnými typy má následující členy:  
  
- A parameterless constructor, which can be used to instantiate the strongly typed resource class.  
  
- A `static` (C#) or `Shared` (Visual Basic) and read-only `ResourceManager` property, which returns the <xref:System.Resources.ResourceManager> instance that manages the strongly typed resource.  
  
- A static `Culture` property, which allows you to set the culture used for resource retrieval. By default, its value is `null`, which means that the current UI culture is used.  
  
- One `static` (C#) or `Shared` (Visual Basic) and read-only property for each resource in the .resources file. Název vlastnosti je názvem prostředku.  
  
 For example, the following command compiles a resource file named StringResources.txt into StringResources.resources and generates a class named `StringResources` in a Visual Basic source code file named StringResources.vb that can be used to access the Resource Manager.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Prostředky v desktopových aplikacích](../resources/index.md)
- [Vytváření zdrojových souborů](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
