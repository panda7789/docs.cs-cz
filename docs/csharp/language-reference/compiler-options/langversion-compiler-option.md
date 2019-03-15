---
title: -langversion (možnosti kompilátoru C#)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: af30095c18a333d5ac3089fe3bf201c32739d9cf
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846347"
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
|preview|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview, který může podporovat.|
|nejnovější|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze (včetně dílčí verze), který může podporovat.|
|latestMajor|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější hlavní verzi, která může podporovat.|
|8.0|Kompilátor přijímá pouze syntaxi, která je součástí C# 8.0 nebo nižší. <sup id="TCS80">[CS80](#FCS80)</sup>|
|7.3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.3 nebo nižší <sup id="TCS73"> [CS73](#FCS73)</sup>|
|7.2|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce C# 7.2 nebo nižší <sup id="TCS72"> [CS72](#FCS72)</sup>|
|7.1|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce C# 7.1 nebo nižší <sup id="TCS71"> [CS71](#FCS71)</sup>|
|7|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce C# 7.0 nebo nižší <sup id="TCS7"> [CS7](#FCS7)</sup>|
|6|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší <sup id="TCS6"> [CS6](#FCS6)</sup>|
|5|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší <sup id="TCS5"> [CS5](#FCS5)</sup>|
|4|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší <sup id="TCS4"> [CS4](#FCS4)</sup>|
|3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v jazyce C# 3.0 nebo nižší <sup id="TCS3"> [CS3](#FCS3)</sup>|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2006 C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí 23270: ISO/IEC 2003 C# (1.0 nebo 1.2) <sup id="TISO1"> [ISO1](#FISO1)</sup>|  

## <a name="remarks"></a>Poznámky

 Metadata odkazuje vaše aplikace v C# není podléhají **- langversion** – možnost kompilátoru.  
  
 Protože každá verze kompilátoru jazyka C# obsahuje rozšíření pro specifikaci jazyka **- langversion** vám není udělena ekvivalentní funkce předchozí verze kompilátoru.  

 Kromě toho během aktualizace verze jazyka C# obecně časově shodovala se zastávkami hlavními verzemi rozhraní .NET Framework, tak novou syntaxi a funkce nejsou nutně svázán s tuto konkrétní verzi rozhraní framework verzi. Zatímco nové funkce jednoznačně vyžadují nové aktualizace kompilátoru, která je také vydán spolu s revizí C#, jednotlivé konkrétní funkce má svůj vlastní minimální rozhraní .NET API nebo společné jazykové požadavky modulu runtime, které může povolit jeho spuštění ve starší verze architektury zahrnutím Balíčky NuGet nebo jiných knihoven.
  
 Bez ohledu na to, které **- langversion** nastavení použijete, bude použita aktuální verzi modulu common language runtime k vytvoření .exe nebo .dll. Jedinou výjimkou je přátelských sestavení a [- moduleassemblyname (možnost kompilátoru C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), které pracují pod **- langversion: ISO-1**.  

 Další způsoby, jak určit verzi jazyka C#, najdete v článku [vyberte verzi jazyka C#](../configure-language-version.md) tématu.
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

### <a name="c-language-specification"></a>Specifikace jazyka C#

|Version|Odkaz|Popis|
|-------|----|-----------|
|C# 7.0 a novější||není aktuálně k dispozici|
|C# 6.0|[Odkaz](../language-specification/index.md)|Verze jazyka C# specifikace 6 - neoficiální koncept: .NET Foundation|
|C# 5.0|[Stáhnout PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standard ECMA-334 5th Edition|
|C# 3.0|[Stažení dokumentu](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Jazyk specifikace verze 3.0: Microsoft Corporation|
|C# 2.0|[Stáhnout PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|4. edice Standard ECMA-334|
|C# 1.2|[Stažení dokumentu](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C#Jazyk specifikace verze 1.2: Microsoft Corporation|
|C# 1.0|[Stažení dokumentu](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C#Jazyk specifikace verze 1.0: Microsoft Corporation|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Verze kompilátoru minimální potřebné pro podporu všech funkcí jazyka

[↩](#TCS80)<a name="FCS80">CS80</a>: Microsoft Visual Studio/Build Tools 2019, verze 16 nebo sady SDK .NET Core 3.0 [↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017 verze 15.7  
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017 verze 15.5  
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017 verze 15.3  
[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017  
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015  
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 nebo jako součást balíčku kompilátoru rozhraní .NET Framework 4.5  
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 nebo jako součást balíčku rozhraní .NET Framework 4.0 kompilátoru  
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 nebo jako součást balíčku rozhraní .NET Framework 3.5 kompilátoru  
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 nebo jako součást balíčku rozhraní .NET Framework 2.0 kompilátoru  
[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/sestavení nástroje .NET 2002 nebo jako součást balíčku. Kompilátor N Framework 1.0  
