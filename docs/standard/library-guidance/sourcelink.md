---
title: Zdrojové propojení a knihovny .NET
description: Doporučení osvědčených postupů pro použití zdrojového odkazu ke zlepšení ladění knihoven .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744550"
---
# <a name="source-link"></a>Odkaz na zdroj

Zdrojový odkaz je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z NuGet vývojáři. Zdrojový odkaz se spustí při vytváření balíčku NuGet a vloží metadata správy zdrojového kódu uvnitř sestavení a balíček. Vývojáři, kteří si stáhnou balíček a mají povolenou zdrojovou vazbu v sadě Visual Studio, mohou vstoupit do jeho zdrojového kódu. Zdrojový odkaz poskytuje metadata správy zdrojového kódu k vytvoření skvělého prostředí ladění.

## <a name="source-link-demo"></a>Ukázka zdrojového odkazu

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Použití zdrojového odkazu

Pokyny pro použití zdrojového odkazu naleznete v úložišti [GitHub dotnet/sourcelink.](https://github.com/dotnet/sourcelink/blob/master/README.md)

Pomocí [aplikace NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) můžete potvrdit, že metadata zdrojového odkazu byla úspěšně vložena do balíčku. Zkontrolujte, `Repository` zda jsou metadata vybavena identifikátorem potvrzení a že soubory PDB jsou umístěny s dll každého cíle.

![Zdrojový odkaz v Průzkumníku balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Zdrojový odkaz v Průzkumníku balíčků NuGet")

✔️ zvažte použití zdrojového odkazu k přidání metadat správy zdrojového kódu do sestavení a balíčků NuGet.

> [!TIP]
> Můžete dále vylepšit vývojáře ladění prostředí přidáním ladicí atributy do typů.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>můžete přizpůsobit způsob zobrazení třídy nebo pole v oknech proměnných ladicího programu.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje ladicí program krokovat kód namísto krokování do kódu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>určuje, zda je člen zobrazen v oknech proměnných ladicího programu.

✔️ ZVAŽTe publikování`*.pdb`souborů symbolů ( ).

> Pro nejlepší ladění prostředí knihovna by měla publikovat soubory symbolů, stejně jako použít zdrojový odkaz. Další informace o souborech symbolů a balíčcích symbolů naleznete v [tématu Balíčky symbolů](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)
