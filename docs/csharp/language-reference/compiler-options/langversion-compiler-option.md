---
title: "-langversion (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 11aab223ee70ff69d8c3470e747738bfe44540ea
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-langversion-c-compiler-options"></a>-langversion (možnosti kompilátoru C#)
Způsobí, že kompilátor tak, aby přijímal pouze syntaxi, která je součástí vybrané specifikace jazyka C#.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Platné jsou následující hodnoty:  
  
|Možnost|Význam|  
|------------|-------------|  
|default|Kompilátor přijímá všechny platné syntaxe jazyka, jakou může podporovat. <sup id="TDefault">[Výchozí](#FDefault)</sup>| 
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2003 C# (1.0/1.1) <sup id="TISO1"> [ISO1](#FISO1)</sup>|  
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2006 C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 3.0 nebo nižší <sup id="TCS3"> [CS3](#FCS3)</sup>|
|4|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší <sup id="TCS4"> [CS4](#FCS4)</sup>|
|5|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší <sup id="TCS5"> [CS5](#FCS5)</sup>|
|6|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší <sup id="TCS6"> [CS6](#FCS6)</sup>|
|7|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.0 nebo nižší <sup id="TCS7"> [CS7](#FCS7)</sup>|
|Nejnovější|Kompilátor přijímá všechny platné syntaxe jazyka, jakou může podporovat. <sup id="TLatest">[Latest](#FLatest)</sup>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>Poznámky  
 Metadata odkazuje aplikace C# není podléhají **- langversion** – možnost kompilátoru.  
  
 Protože každá verze kompilátoru jazyka C# obsahuje rozšíření pro specifikaci jazyka **- langversion** nezískáte ekvivalentní funkce kompilátoru starší verze.  
 
 Kromě toho při aktualizace verzí jazyka C# obecně neshoduje se hlavní rozhraní .net Framework verze, nové syntaxe a funkce nejsou se nevztahuje na danou verzi konkrétní framework. Při nových funkcí bude vyžadovat výborný nové aktualizace kompilátoru, která je také vydané spolu s revize C#, každou konkrétní funkci má svou vlastní minimální rozhraní API .net nebo běžné požadavky modulu runtime jazyka, které může povolit jeho spuštění v nižší úrovně rozhraní pomocí včetně balíčky NuGet, nebo jiné knihovny.
  
 Bez ohledu na to, které **- langversion** nastavení použijete, bude použita aktuální verzí common language runtime pro vytvoření .exe nebo .dll. Jedinou výjimkou je přátelských sestavení a [- moduleassemblyname (možnost kompilátoru C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), které pracovní pod **- langversion: ISO-1**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **vlastnosti** stránky.  
  
2.  Klikněte **sestavení** stránku vlastností.  
  
3.  Klikněte **Upřesnit** tlačítko.  
  
4.  Změnit **jazyková verze** vlastnost.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
    
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>Specifikace jazyka C#
 [Referenční dokumentace specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md) : Foundation rozhraní .NET  
 C# 1.0/1.1 [ISO/IEC 23270: 2003](https://www.iso.org/standard/36768.html) informačních technologií – specifikace jazyka C#: ISO katalogu  
 C# 2.0 [ISO/IEC 23270: 2006](https://www.iso.org/standard/42926.html) informačních technologií – specifikace jazyka C#: ISO katalogu  
 C# 2.0 [c042926_ISO_IEC_23270_2006 (E) .zip](http://standards.iso.org/ittf/PubliclyAvailableStandards/c042926_ISO_IEC_23270_2006(E).zip) ISO/IEC 23270: 2006 ve formátu PDF: volně dostupných standardy ISO  
 C# 3.0 [CSharp jazyk Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# jazyková specifikace verze 3.0: Microsoft Corporation.  
 C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard Edition 4. ECMA-334    
 C# 5.0 [CSharp jazyk Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# jazyková specifikace verze 5.0: Microsoft Corporation.  
 C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# jazyková specifikace verze 6 - neoficiální konceptu: Foundation rozhraní .NET  
 C# 7.0 (není aktuálně k dispozici)  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Vyžadovaná pro podporu všech funkcí jazyka kompilátoru minimální verze   
[↩](#TDefault)<a name="FDefault">výchozí</a>, <a name="FISO1">ISO1</a>: nástroje sady Microsoft Visual Studio nebo sestavení .net 2002 nebo připojené rozhraní .net Framework 1.0 kompilátoru     
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio nebo sestavení nástroje 2005 nebo připojené rozhraní .net Framework 2.0 kompilátoru    
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio nebo sestavení nástroje 2008 nebo připojené rozhraní .net Framework 3.5 kompilátoru    
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio nebo sestavení nástroje 2010 nebo připojené rozhraní .net Framework 4.0 kompilátoru    
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio nebo sestavení nástroje 2012 nebo připojené rozhraní .net Framework 4.5 kompilátoru    
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio nebo sestavení nástroje 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">nejnovější</a>: Microsoft Visual Studio nebo sestavení nástroje 2017   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
