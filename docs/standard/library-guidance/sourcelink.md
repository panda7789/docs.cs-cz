---
title: Knihovny odkazu na zdroj a .NET
description: Doporučené osvědčené postupy pro vylepšení ladění pro knihovny .NET pomocí odkazu na zdroj.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9d3e2b0b3aedbab150072bf6eebff4acb5f8a0b7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211676"
---
# <a name="source-link"></a>Odkaz na zdroj

Odkaz na zdroj je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z Nugetu vývojáři. Odkaz na zdroj provede při vytváření balíčku NuGet a vloží zdrojová metadata ovládací prvek uvnitř sestavení a balíček. Vývojáři, kteří Stáhnout balíček a odkaz na zdroj povolené v sadě Visual Studio můžete krokovat s vnořením jeho zdrojový kód. Zdrojový odkaz poskytuje metadata ovládací prvek zdroje k vytvoření skvělé možnosti ladění.

## <a name="source-link-demo"></a>Ukázka odkaz zdroje

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Pomocí zdrojového odkazu

Pokyny, jak pomocí zdrojového odkazu můžete najít na [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) úložiště GitHub.

Můžete použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) potvrďte, že odkaz na zdroj metadat úspěšně vloženy do balíčku. Zkontrolujte `Repository` metadata jsou k dispozici s identifikátorem komentář a soubory PDB se nachází na každém cíli .dll.

![Zdrojový odkaz v Průzkumníku balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "zdrojový odkaz v Průzkumníku balíčků NuGet")

**✔️ ZVAŽTE** pomocí zdrojového odkazu pro přidání metadata ovládací prvek zdroje k sestavení a balíčky NuGet.

> [!TIP]
> Přidáním atributů ladicího programu na daný typ můžete dále vylepšit možnosti ladění pro vývojáře.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> můžete přizpůsobit, jak třídy nebo pole se zobrazí v oknech proměnných ladicího programu.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> Dává pokyn ladicímu programu vstup do kódu místo krokování s vnořením do kódu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> Určuje, zda člen je zobrazeno v oknech proměnných ladicího programu.

**✔️ ZVAŽTE** publikování souborů symbolů (`*.pdb`).

> Pro nejlepší možnosti ladění knihovny by měl publikovat soubory symbolů také pomocí odkazu na zdroj. Další informace o soubory symbolů a balíčky symbolů, naleznete v tématu [Symbol balíčky](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)
