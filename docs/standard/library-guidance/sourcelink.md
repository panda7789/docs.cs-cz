---
title: Zdrojový odkaz a knihovny .NET
description: Doporučení osvědčených postupů pro použití odkazu na zdroj ke zlepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 89f9e3b1fd70003c528465f29a143b157468d539
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089288"
---
# <a name="source-link"></a>Odkaz na zdroj

Zdrojový odkaz je technologie, která umožňuje ladění zdrojového kódu ze sestavení .NET z NuGet vývojářů. Zdrojový odkaz se spustí při vytváření balíčku NuGet a vloží metadata správy zdrojového kódu do sestavení a balíčku. Vývojáři, kteří si balíček stáhli a mají povolený odkaz na zdroj v rámci sady Visual Studio, mohou krokovat se svým zdrojovým kódem. Odkaz na zdroj poskytuje metadata správy zdrojového kódu pro vytvoření skvělého prostředí ladění.

## <a name="source-link-demo"></a>Ukázka zdrojového odkazu

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Použití odkazu na zdroj

Pokyny pro použití zdrojového odkazu najdete v úložišti GitHub [/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHubu.

Pomocí [Průzkumníka balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) můžete zkontrolovat, jestli se metadata zdrojového odkazu úspěšně vložila do balíčku. Ověřte, zda jsou metadata `Repository` k dispozici s identifikátorem potvrzení a že jsou umístěny soubory. pdb s každou cílovou knihovnou DLL.

![Odkaz na zdroj v Průzkumníkovi balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Odkaz na zdroj v Průzkumníkovi balíčků NuGet")

**✔️ zvažte** použití odkazu na zdroj k přidání metadat správy zdrojového kódu do sestavení a balíčků NuGet.

> [!TIP]
> Můžete dál vylepšit možnosti ladění vývojářů přidáním atributů ladicího programu do vašich typů.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> může přizpůsobit způsob zobrazení třídy nebo pole v oknech proměnných ladicího programu.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> instruuje ladicí program, aby procházel kód místo krokování s kódem.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> určuje, zda je člen zobrazen v oknech proměnných ladicího programu.

**✔️ zvažte** publikování souborů symbolů (`*.pdb`).

> Pro nejlepší prostředí ladění by knihovna měla publikovat soubory symbolů a také odkaz použít zdroj. Další informace o souborech symbolů a balíčcích symbolů najdete v tématu [balíčky symbolů](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Předchozí](dependencies.md)
>[Další](publish-nuget-package.md)
