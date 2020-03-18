---
title: -langversion (Možnosti kompilátoru Jazyka C#)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 007b10f6f27233c43caad4c1910e3d1158682950
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920370"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (Možnosti kompilátoru Jazyka C#)

Způsobí, že kompilátor přijmout pouze syntaxe, která je zahrnuta ve zvolené specifikaci jazyka C#.

## <a name="syntax"></a>Syntaxe

```console
-langversion:option
```

## <a name="arguments"></a>Argumenty

`option`

Následující hodnoty jsou platné:

|Možnost|Význam|
|------------|-------------|
|Náhled|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze preview, kterou může podporovat.|
|nejnovější|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější verze (včetně dílčích verzí), které může podporovat.|
|nejnovějšíMajor|Kompilátor přijímá všechny platné syntaxe jazyka z nejnovější hlavní verze, kterou může podporovat.|
|8.0|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 8.0 nebo nižší.|
|7.3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.3 nebo nižší.|
|7.2|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.2 nebo nižší.|
|7.1|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.1 nebo nižší.|
|7|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.0 nebo nižší.|
|6|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší.|
|5|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší.|
|4|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší.|
|3|Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 3.0 nebo nižší.|
|ISO-2|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270:2006 C# (2.0).|
|ISO-1|Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270:2003 C# (1.0/1.2).|

Výchozí jazyková verze závisí na cílovém rozhraní pro vaši aplikaci a na nainstalované verzi sady SDK nebo sady Visual Studio. Tato pravidla jsou definována v [článku konfigurace jazykové verze.](../configure-language-version.md#defaults)

## <a name="remarks"></a>Poznámky

Metadata odkazovaná aplikací Jazyka C# nepodléhají možnosti kompilátoru **-langversion.**

Vzhledem k tomu, že každá verze kompilátoru Jazyka C# obsahuje rozšíření specifikace jazyka, **-langversion** neposkytuje ekvivalentní funkce starší verze kompilátoru.

Navíc zatímco aktualizace verze jazyka C# se obvykle shodují s hlavními verzemi rozhraní .NET Framework, nová syntaxe a funkce nejsou nutně vázány na tuto konkrétní verzi rozhraní. Zatímco nové funkce rozhodně vyžadují novou aktualizaci kompilátoru, která je také vydána vedle revize Jazyka C#, každá konkrétní funkce má své vlastní minimální rozhraní .NET API nebo požadavky na běžný běh v jazyce common language, které mohou umožnit spuštění na downlevel frameworkech zahrnutím balíčků NuGet nebo jiných knihoven.

Bez ohledu na to, které nastavení **-langversion** používáte, použijte aktuální verzi prostředí COMMON Language runtime k vytvoření souboru .exe nebo .dll. Jednou výjimkou je friend assemblyies a [-moduleassemblyname (C# Compiler Option),](./moduleassemblyname-compiler-option.md)které pracují pod **-langversion:ISO-1**.

Další způsoby určení jazykové verze jazyka C# naleznete v článku [Vyberte jazykovou verzi jazyka C#.](../configure-language-version.md)

Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>kompilátoru programově, naleznete v tématu .

## <a name="c-language-specification"></a>specifikace jazyka C#

|Version|Odkaz|Popis|
|-------|----|-----------|
|C# 7.0 a novější||není v současné době k dispozici|
|C# 6.0|[Odkaz](/dotnet/csharp/language-reference/language-specification/introduction)|C# Specifikace jazyka verze 6 - Neoficiální návrh: .NET Foundation|
|C# 5.0|[Stáhnout PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standardní ECMA-334 5th Edition|
|C# 3.0|[Stáhnout DOC](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# Jazyk specifikace verze 3.0: Microsoft Corporation|
|C# 2.0|[Stáhnout PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standardní ECMA-334 4th Edition|
|C# 1.2|[Stáhnout DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C# Jazyková specifikace verze 1.2: Microsoft Corporation|
|C# 1.0|[Stáhnout DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C# Specifikace jazyka verze 1.0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Minimální verze sady SDK potřebná pro podporu všech jazykových funkcí

V následující tabulce jsou uvedeny minimální verze sady SDK s kompilátorem jazyka C#, který podporuje odpovídající jazykovou verzi:

|Verze jazyka C#|Minimální verze sady SDK|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/Build Tools 2019, verze 16.3 nebo .NET Core 3.0 SDK |
|C# 7.3| Microsoft Visual Studio/Nástroje pro sestavení 2017, verze 15.7 |
|C# 7.2| Microsoft Visual Studio/Build Tools 2017, verze 15.5 |
|C# 7.1| Microsoft Visual Studio/Nástroje pro sestavení 2017, verze 15.3 |
|C# 7.0| Microsoft Visual Studio/Nástroje pro sestavení 2017 |
|C# 6| Microsoft Visual Studio/Nástroje pro sestavení 2015 |
|C# 5| Microsoft Visual Studio/Build Tools 2012 nebo přivázaný kompilátor rozhraní .NET Framework 4.5 |
|C# 4| Kompilátor Microsoft Visual Studio/Build Tools 2010 nebo v balíčku .NET Framework 4.0 |
|C# 3| Kompilátor Microsoft Visual Studio/Build Tools 2008 nebo svázaný kompilátor rozhraní .NET Framework 3.5 |
|C# 2| Kompilátor Microsoft Visual Studio/Build Tools 2005 nebo v balíčku .NET Framework 2.0 |
|C# 1.0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 nebo balíček .NET Framework 1.0 kompilátor |

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
