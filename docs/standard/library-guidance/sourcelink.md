---
title: Zdrojový odkaz a knihovny .NET
description: Doporučení osvědčených postupů pro použití odkazu na zdroj ke zlepšení ladění pro knihovny .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 5dee2a6b1f77daa641351e02c1dd3e0a38f66550
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201972"
---
# <a name="source-link"></a>Odkaz na zdroj

Zdrojový odkaz je technologie, která umožňuje ladění zdrojového kódu ze sestavení .NET z NuGet vývojářů. Zdrojový odkaz se spustí při vytváření balíčku NuGet a vloží metadata správy zdrojového kódu do sestavení a balíčku. Vývojáři, kteří si balíček stáhli a mají povolený odkaz na zdroj v rámci sady Visual Studio, mohou krokovat se svým zdrojovým kódem. Odkaz na zdroj poskytuje metadata správy zdrojového kódu pro vytvoření skvělého prostředí ladění.

## <a name="source-link-demo"></a>Ukázka zdrojového odkazu

<!--markdownlint-disable MD034 -->
> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Použití odkazu na zdroj

Pokyny pro použití zdrojového odkazu najdete v úložišti GitHub [/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHubu.

Pomocí [Průzkumníka balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) můžete zkontrolovat, jestli se metadata zdrojového odkazu úspěšně vložila do balíčku. Ověřte, že `Repository` metadata jsou k dispozici s identifikátorem potvrzení a že jsou umístěny soubory. pdb s každou cílovou knihovnou DLL.

![Odkaz na zdroj v Průzkumníkovi balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Odkaz na zdroj v Průzkumníkovi balíčků NuGet")

✔️ Zvažte použití odkazu na zdroj k přidání metadat správy zdrojového kódu do sestavení a balíčků NuGet.

> [!TIP]
> Můžete dál vylepšit možnosti ladění vývojářů přidáním atributů ladicího programu do vašich typů.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>může přizpůsobit způsob zobrazení třídy nebo pole v oknech proměnných ladicího programu.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje ladicí program, aby procházel kód místo krokování s kódem.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>Určuje, zda je člen zobrazen v oknech proměnných ladicího programu.

✔️ Zvažte publikování souborů symbolů ( `*.pdb` ).

> Pro nejlepší prostředí ladění by knihovna měla publikovat soubory symbolů a také odkaz použít zdroj. Další informace o souborech symbolů a balíčcích symbolů najdete v tématu [balíčky symbolů](./nuget.md#symbol-packages).

✔️ Zvažte povolení deterministického sestavení.

> Deterministické sestavení umožňují ověření, že výsledný binární soubor byl sestaven ze zadaného zdroje a poskytuje sledovatelnost. Další informace o deterministické sestavení a pokyny pro jejich povolení naleznete v tématu [deterministické sestavení](https://github.com/clairernovotny/DeterministicBuilds).

>[!div class="step-by-step"]
>[Předchozí](dependencies.md) 
> [Další](publish-nuget-package.md)
