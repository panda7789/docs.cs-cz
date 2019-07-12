---
ms.openlocfilehash: 25060a42b4ff66b1e25881b8c704ae0958e5f245
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804408"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Sestavení souboru Entity Framework EDMX v sadě Visual Studio 2013 může při použití úloh EntityDeploySplit nebo EntityClean selhat s chybou MSB4062

|   |   |
|---|---|
|Podrobnosti|U nástrojů MSBuild 12.0 (zahrnutých v sadě Visual Studio 2013) se změnilo umístění souborů MSBuild, což vede k tomu, že starší soubory cílů Entity Framework jsou neplatné. Úlohy <code>EntityDeploySplit</code> a <code>EntityClean</code> v důsledku toho selhávají, protože nenajdou knihovnu <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. K tomuto narušení vazby nedochází změnou v rozhraní .NET Framework, ale změnou v sadě nástrojů MSBuild / Visual Studio. Projeví se jen při upgradu nástrojů při vývojáře, ne při samotném upgradu rozhraní .NET Framework.|
|Doporučení|Soubory cílů Entity Framework jsou ve verzi .NET Framework 4.6 opraveny tak, aby fungovaly s novým rozložením nástrojů MSBuild. Upgradem na tuto verzi rozhraní Framework se problém vyřeší. Alternativně [toto řešení](https://stackoverflow.com/a/24249247/131944) je možné opravovat soubory cíle přímo.|
|Scope|Hlavní|
|Version|4.5.1|
|type|Změna cílení|

