---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615689"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Sestavení souboru Entity Framework EDMX v sadě Visual Studio 2013 může při použití úloh EntityDeploySplit nebo EntityClean selhat s chybou MSB4062

#### <a name="details"></a>Podrobnosti

U nástrojů MSBuild 12.0 (zahrnutých v sadě Visual Studio 2013) se změnilo umístění souborů MSBuild, což vede k tomu, že starší soubory cílů Entity Framework jsou neplatné. Úlohy `EntityDeploySplit` a `EntityClean` v důsledku toho selhávají, protože nenajdou knihovnu `Microsoft.Data.Entity.Build.Tasks.dll`. K tomuto narušení vazby nedochází změnou v rozhraní .NET Framework, ale změnou v sadě nástrojů MSBuild / Visual Studio. Projeví se jen při upgradu nástrojů při vývojáře, ne při samotném upgradu rozhraní .NET Framework.

#### <a name="suggestion"></a>Návrh

Soubory cílů Entity Framework jsou ve verzi .NET Framework 4.6 opraveny tak, aby fungovaly s novým rozložením nástrojů MSBuild. Upgradem na tuto verzi rozhraní Framework se problém vyřeší. Alternativně lze [Toto alternativní řešení](https://stackoverflow.com/a/24249247/131944) použít k opravě souborů cílů přímo.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.5.1       |
| Typ    | Změna cílení |
