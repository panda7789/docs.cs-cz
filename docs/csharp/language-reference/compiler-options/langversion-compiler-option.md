---
title: -langversion – (C# možnosti kompilátoru)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 007b10f6f27233c43caad4c1910e3d1158682950
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920370"
---
# <a name="-langversion-c-compiler-options"></a>-langversion – (C# možnosti kompilátoru)

Způsobí, že kompilátor přijme pouze syntaxi, která je obsažena ve C# zvolené specifikaci jazyka.

## <a name="syntax"></a>Syntaxe

```console
-langversion:option
```

## <a name="arguments"></a>Arguments

`option`

Platné jsou následující hodnoty:

|Možnost|Význam|
|------------|-------------|
|preview|Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze Preview, kterou může podporovat.|
|nejnovější|Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější verze (včetně dílčích verzí), které může podporovat.|
|latestMajor|Kompilátor přijímá všechny platné jazykové syntaxe z nejnovější hlavní verze, kterou může podporovat.|
|8.0|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 8,0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,2 nebo nižší.|
|7,1|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 7,0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 6,0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 5,0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 4,0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je obsažena C# v 3,0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2006 (2,0).|
|ISO-1|Kompilátor přijímá pouze syntaxi, která je obsažena v normě ISO C# /IEC 23270:2003 (1.0/1.2).|

Výchozí jazyková verze závisí na cílové architektuře vaší aplikace a na nainstalované verzi sady SDK nebo sady Visual Studio. Tato pravidla jsou definována v článku [Konfigurace jazykové verze](../configure-language-version.md#defaults) .

## <a name="remarks"></a>Poznámky

Metadata, na která C# odkazuje vaše aplikace, nepodléhají možnosti kompilátoru **-langversion –** .

Vzhledem k tomu, že C# každá verze kompilátoru obsahuje rozšíření jazykové specifikace, **-langversion –** neposkytuje ekvivalentní funkce starší verze kompilátoru.

Kromě toho i C# když se aktualizace verze obecně shodují s hlavními .NET Framework verzemi, Nová syntaxe a funkce nejsou nutně vázané na konkrétní verzi Frameworku. I když nové funkce budou jednoznačně vyžadovat novou aktualizaci kompilátoru, která se také vydává C# společně s revizí, každá konkrétní funkce má své vlastní minimální požadavky na rozhraní .NET API nebo modul CLR (Common Language Runtime), které by mohly umožňovat jeho spuštění v rozhraních se starší verzí, včetně balíčků NuGet nebo jiných knihoven.

Bez ohledu na to, který parametr **-langversion –** použijete, použijte aktuální verzi modulu CLR (Common Language Runtime) k vytvoření souboru. exe nebo. dll. Jedinou výjimkou jsou Friend sestavení a [-moduleassemblyname –C# (možnost kompilátoru)](./moduleassemblyname-compiler-option.md), která funguje v rámci **-langversion –: ISO-1**.

Další způsoby, jak určit C# jazykovou verzi, najdete v článku věnovaném [ C# jazykové verzi](../configure-language-version.md) .

Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

## <a name="c-language-specification"></a>specifikace jazyka C#

|Version|Odkaz|Popis|
|-------|----|-----------|
|C#7,0 a novější||Momentálně není k dispozici|
|C#6,0|[Odkaz](/dotnet/csharp/language-reference/language-specification/introduction)|C#Specifikace jazyka verze 6 – neoficiální koncept: .NET Foundation|
|C#5,0|[Stáhnout PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standard ECMA-334 5. edice|
|C#3,0|[Stáhnout dokument](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Specifikace jazyka verze 3,0: Microsoft Corporation|
|C#2,0|[Stáhnout PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standard ECMA – 334 4. edice|
|C#1,2|[Stáhnout dokument](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C#Specifikace jazyka verze 1,2: Microsoft Corporation|
|C#1,0|[Stáhnout dokument](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C#Specifikace jazyka verze 1,0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Minimální verze sady SDK potřebná pro podporu všech funkcí jazyka

V následující tabulce jsou uvedeny minimální verze sady SDK s C# kompilátorem, který podporuje odpovídající jazykovou verzi:

|C#znění|Minimální verze sady SDK|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/Build Tools 2019, verze 16,3 nebo .NET Core 3,0 SDK |
|C# 7.3| Microsoft Visual Studio/Build Tools 2017, verze 15,7 |
|C# 7.2| Microsoft Visual Studio/Build Tools 2017, verze 15,5 |
|C# 7.1| Microsoft Visual Studio/Build Tools 2017, verze 15,3 |
|C# 7.0| Microsoft Visual Studio/Build Tools 2017 |
|C# 6| Microsoft Visual Studio/Build Tools 2015 |
|C#čl| Microsoft Visual Studio/Build Tools 2012 nebo .NET Framework 4,5 kompilátor |
|C# 4| Microsoft Visual Studio/Build Tools 2010 nebo .NET Framework 4,0 kompilátor |
|C#1| Microsoft Visual Studio/Build Tools 2008 nebo .NET Framework 3,5 kompilátor |
|C#odst| Microsoft Visual Studio/Build Tools 2005 nebo .NET Framework 2,0 kompilátor |
|C#1,0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 nebo kompilátor .NET Framework 1,0 |

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
