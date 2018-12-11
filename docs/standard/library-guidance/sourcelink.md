---
title: Knihovny SourceLink a .NET
description: Doporučené osvědčené postupy pro používání SourceLink k vylepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 3bc72e158a5773b656095f9ce58b442469f91e67
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128922"
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

**✔️ ZVAŽTE** včetně soubory symbolů (`*.pdb`) v balíčku NuGet.

> Obvykle bude publikována soubory se symboly v [balíček symbolů](./nuget.md#symbol-packages). V současné době hlavní veřejný hostitel pro balíčky symbolů nepodporuje soubory portable symbolů (`*.pdb`) vytvořené projekty založenými na sadě SDK a symbol balíčky nejsou uloženy užitečné.

>[!div class="step-by-step"]
>[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)