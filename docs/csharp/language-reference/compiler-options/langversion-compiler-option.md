---
title: -langversion – (možnosti kompilátoru C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: fd05802008a20267fea54f14bae4c8deb0e21c65
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656203"
---
# <a name="-langversion-c-compiler-options"></a>-langversion – (možnosti kompilátoru C#)

Způsobí, že kompilátor přijme pouze syntaxi, která je obsažena ve zvolené specifikaci jazyka C#.

## <a name="syntax"></a>Syntaxe

```console
-langversion:option
```

## <a name="arguments"></a>Argumenty

`option`

Platné jsou následující hodnoty:

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

Výchozí jazyková verze závisí na cílové architektuře vaší aplikace a na nainstalované verzi sady SDK nebo sady Visual Studio. Tato pravidla jsou definována v článku [Konfigurace jazykové verze](../configure-language-version.md#defaults) .

## <a name="remarks"></a>Poznámky

Metadata, na která odkazuje vaše aplikace v jazyce C#, nejsou předmětem možnosti kompilátoru **langversion –** .

Vzhledem k tomu, že každá verze kompilátoru jazyka C# obsahuje rozšíření jazykové specifikace, **-langversion –** neposkytuje ekvivalentní funkce starší verze kompilátoru.

I když se aktualizace verze C# obecně shodují s hlavními .NET Framework verzemi, Nová syntaxe a funkce nejsou nutně vázané na konkrétní verzi Frameworku. I když nové funkce budou jednoznačně vyžadovat novou aktualizaci kompilátoru, která se také vydává společně s revizí v jazyce C#, každá konkrétní funkce má své vlastní minimální požadavky rozhraní .NET API nebo modulu CLR (Common Language Runtime), které by mohly umožňovat jeho spuštění v rámci architektury nižší verze, včetně balíčků NuGet nebo jiných knihoven.

Bez ohledu na to, který parametr **-langversion –** použijete, použijte aktuální verzi modulu CLR (Common Language Runtime) k vytvoření souboru. exe nebo. dll. Jedinou výjimkou jsou Friend sestavení a [-moduleassemblyname – (možnost kompilátoru C#)](./moduleassemblyname-compiler-option.md), která funguje v rámci **-langversion –: ISO-1**.

Další způsoby určení verze jazyka C# naleznete v článku o jazykové verzi jazyka [c#](../configure-language-version.md) .

Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> .

## <a name="c-language-specification"></a>specifikace jazyka C#

| Verze          | Odkaz                       | Popis                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| C# 7,0 a novější |                            | Momentálně není k dispozici                                                 |
| C# 6,0           | [Odkaz][csharp-6]           | Specifikace jazyka C# verze 6 – neoficiální koncept: .NET Foundation |
| C# 5,0           | [Stáhnout PDF][csharp-5]   | Standard ECMA-334 5. edice                                           |
| C# 3,0           | [Stáhnout dokument][csharp-3]   | Specifikace jazyka C# verze 3,0: Microsoft Corporation            |
| C# 2,0           | [Stáhnout PDF][csharp-2]   | Standard ECMA – 334 4. edice                                           |
| C# 1,2           | [Stáhnout dokument][csharp-1.2] | Specifikace jazyka C# verze 1,2: Microsoft Corporation            |
| C# 1,0           | [Stáhnout dokument][csharp-1]   | Specifikace jazyka C# verze 1,0: Microsoft Corporation            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Minimální verze sady SDK potřebná pro podporu všech funkcí jazyka

V následující tabulce je uveden minimální počet verzí sady SDK s kompilátorem jazyka C#, který podporuje odpovídající jazykovou verzi:

| Verze C# | Minimální verze sady SDK                                                                  |
|------------|--------------------------------------------------------------------------------------|
| C# 8.0     | Microsoft Visual Studio/Build Tools 2019, verze 16,3 nebo .NET Core 3,0 SDK         |
| C# 7.3     | Microsoft Visual Studio/Build Tools 2017, verze 15,7                               |
| C# 7.2     | Microsoft Visual Studio/Build Tools 2017, verze 15,5                               |
| C# 7.1     | Microsoft Visual Studio/Build Tools 2017, verze 15,3                               |
| C# 7.0     | Microsoft Visual Studio/Build Tools 2017                                             |
| C# 6       | Microsoft Visual Studio/Build Tools 2015                                             |
| C# 5       | Microsoft Visual Studio/Build Tools 2012 nebo .NET Framework 4,5 kompilátor      |
| C# 4       | Microsoft Visual Studio/Build Tools 2010 nebo .NET Framework 4,0 kompilátor      |
| C# 3       | Microsoft Visual Studio/Build Tools 2008 nebo .NET Framework 3,5 kompilátor      |
| C# 2       | Microsoft Visual Studio/Build Tools 2005 nebo .NET Framework 2,0 kompilátor      |
| C# 1.0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 nebo kompilátor .NET Framework 1,0 |

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
