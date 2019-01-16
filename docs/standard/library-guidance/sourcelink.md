---
title: Knihovny SourceLink a .NET
description: Doporučené osvědčené postupy pro používání SourceLink k vylepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: be97f868e2fcfc6c45e4bbac45b033f8914f4d99
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333535"
---
# <a name="sourcelink"></a>SourceLink

SourceLink je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z Nugetu vývojáři. SourceLink provede při vytváření balíčku NuGet a vloží zdrojová metadata ovládací prvek uvnitř sestavení a balíček. Vývojáři, kteří Stáhnout balíček a SourceLink povolené v sadě Visual Studio můžete krokovat s vnořením jeho zdrojový kód. SourceLink poskytuje metadata ovládací prvek zdroje k vytvoření skvělé možnosti ladění.

## <a name="sourcelink-demo"></a>Ukázka SourceLink

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>Pomocí SourceLink

Pokyny k používání SourceLink můžete najít na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) úložiště GitHub.

Můžete použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) potvrďte, že SourceLink metadata úspěšně vloženy do balíčku. Zkontrolujte `Repository` metadata jsou k dispozici s identifikátorem komentář a soubory PDB se nachází na každém cíli .dll.

![V Průzkumníku balíčků NuGet SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink v Průzkumníku balíčků NuGet")

**✔️ ZVAŽTE** pomocí SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíčky NuGet.

> [!TIP]
> Přidáním atributů ladicího programu na daný typ můžete dále vylepšit možnosti ladění pro vývojáře.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> můžete přizpůsobit, jak třídy nebo pole se zobrazí v oknech proměnných ladicího programu.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> Dává pokyn ladicímu programu vstup do kódu místo krokování s vnořením do kódu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> Určuje, zda člen je zobrazeno v oknech proměnných ladicího programu.

**✔️ ZVAŽTE** publikování souborů symbolů (`*.pdb`).

> Další informace o soubory symbolů a balíčky symbolů, naleznete v tématu [Symbol balíčky](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)
