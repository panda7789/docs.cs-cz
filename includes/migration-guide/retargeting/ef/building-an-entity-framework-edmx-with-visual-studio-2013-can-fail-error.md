---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615689"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a><span data-ttu-id="ea9da-101">Sestavení souboru Entity Framework EDMX v sadě Visual Studio 2013 může při použití úloh EntityDeploySplit nebo EntityClean selhat s chybou MSB4062</span><span class="sxs-lookup"><span data-stu-id="ea9da-101">Building an Entity Framework edmx with Visual Studio 2013 can fail with error MSB4062 if using the EntityDeploySplit or EntityClean tasks</span></span>

#### <a name="details"></a><span data-ttu-id="ea9da-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ea9da-102">Details</span></span>

<span data-ttu-id="ea9da-103">U nástrojů MSBuild 12.0 (zahrnutých v sadě Visual Studio 2013) se změnilo umístění souborů MSBuild, což vede k tomu, že starší soubory cílů Entity Framework jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="ea9da-103">MSBuild 12.0 tools (included in Visual Studio 2013) changed MSBuild file locations, causing older Entity Framework targets files to be invalid.</span></span> <span data-ttu-id="ea9da-104">Úlohy `EntityDeploySplit` a `EntityClean` v důsledku toho selhávají, protože nenajdou knihovnu `Microsoft.Data.Entity.Build.Tasks.dll`.</span><span class="sxs-lookup"><span data-stu-id="ea9da-104">The result is that `EntityDeploySplit` and `EntityClean` tasks fail because they are unable to find `Microsoft.Data.Entity.Build.Tasks.dll`.</span></span> <span data-ttu-id="ea9da-105">K tomuto narušení vazby nedochází změnou v rozhraní .NET Framework, ale změnou v sadě nástrojů MSBuild / Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ea9da-105">Note that this break is because of a toolset (MSBuild/VS) change, not because of a .NET Framework change.</span></span> <span data-ttu-id="ea9da-106">Projeví se jen při upgradu nástrojů při vývojáře, ne při samotném upgradu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ea9da-106">It will only occur when upgrading developer tools, not when merely upgrading the .NET Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ea9da-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="ea9da-107">Suggestion</span></span>

<span data-ttu-id="ea9da-108">Soubory cílů Entity Framework jsou ve verzi .NET Framework 4.6 opraveny tak, aby fungovaly s novým rozložením nástrojů MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ea9da-108">Entity Framework targets files are fixed to work with the new MSBuild layout beginning in the .NET Framework 4.6.</span></span> <span data-ttu-id="ea9da-109">Upgradem na tuto verzi rozhraní Framework se problém vyřeší.</span><span class="sxs-lookup"><span data-stu-id="ea9da-109">Upgrading to that version of the Framework will fix this issue.</span></span> <span data-ttu-id="ea9da-110">Alternativně lze [Toto alternativní řešení](https://stackoverflow.com/a/24249247/131944) použít k opravě souborů cílů přímo.</span><span class="sxs-lookup"><span data-stu-id="ea9da-110">Alternatively, [this workaround](https://stackoverflow.com/a/24249247/131944) can be used to patch the targets files directly.</span></span>

| <span data-ttu-id="ea9da-111">Name</span><span class="sxs-lookup"><span data-stu-id="ea9da-111">Name</span></span>    | <span data-ttu-id="ea9da-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ea9da-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ea9da-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ea9da-113">Scope</span></span>   | <span data-ttu-id="ea9da-114">Hlavní</span><span class="sxs-lookup"><span data-stu-id="ea9da-114">Major</span></span>       |
| <span data-ttu-id="ea9da-115">Verze</span><span class="sxs-lookup"><span data-stu-id="ea9da-115">Version</span></span> | <span data-ttu-id="ea9da-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ea9da-116">4.5.1</span></span>       |
| <span data-ttu-id="ea9da-117">Typ</span><span class="sxs-lookup"><span data-stu-id="ea9da-117">Type</span></span>    | <span data-ttu-id="ea9da-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="ea9da-118">Retargeting</span></span> |
