---
title: Knihovny SourceLink a .NET
description: Doporučené osvědčené postupy pro používání SourceLink k vylepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123873"
---
# <a name="sourcelink"></a>SourceLink

SourceLink je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z Nugetu vývojáři. SourceLink provede při vytváření balíčku NuGet a vloží zdrojová metadata ovládací prvek uvnitř sestavení a balíček. Vývojáři, kteří Stáhnout balíček a SourceLink povolené v sadě Visual Studio můžete krokovat s vnořením jeho zdrojový kód. SourceLink poskytuje metadata ovládací prvek zdroje k vytvoření skvělé možnosti ladění.

## <a name="sourcelink-demo"></a>Ukázka SourceLink

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>Pomocí SourceLink

Pokyny k používání SourceLink můžete najít na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) úložiště GitHub.

Můžete použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) potvrďte, že SourceLink metadata úspěšně vloženy do balíčku. Zkontrolujte `Repository` metadata jsou k dispozici s identifikátorem komentář a soubory PDB se nachází na každém cíli .dll.

![V Průzkumníku balíčků NuGet SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink v Průzkumníku balíčků NuGet")

**✔️ ZVAŽTE** pomocí SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.

**✔️ ZVAŽTE** včetně soubory PDB v balíčku NuGet.

>[!div class="step-by-step"]
[Předchozí](./dependencies.md)
[další](./publish-nuget-package.md)
