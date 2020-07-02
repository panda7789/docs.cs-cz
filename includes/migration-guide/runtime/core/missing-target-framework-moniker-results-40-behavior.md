---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619984"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="00522-101">Chybějící zástupný název rozhraní Target Framework má za následek 4,0 chování.</span><span class="sxs-lookup"><span data-stu-id="00522-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="00522-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="00522-102">Details</span></span>

<span data-ttu-id="00522-103">Aplikace bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> použití na úrovni sestavení se automaticky spustí pomocí sémantiky (adaptivní) .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="00522-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="00522-104">Aby se zajistila vysoká kvalita, doporučujeme, aby všechny binární soubory byly explicitně přiděleny s <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> označením verze .NET Framework, se kterou byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="00522-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="00522-105">Všimněte si, že použití monikeru cílového rozhraní v souboru projektu způsobí, že nástroj MSBuild automaticky použije <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="00522-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00522-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="00522-106">Suggestion</span></span>

<span data-ttu-id="00522-107"><xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Měla by být zadána buď prostřednictvím přidání atributu přímo do sestavení, nebo zadáním cílové architektury v [souboru projektu nebo pomocí grafického uživatelského rozhraní Visual Studio vlastností projektu](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span><span class="sxs-lookup"><span data-stu-id="00522-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="00522-108">Name</span><span class="sxs-lookup"><span data-stu-id="00522-108">Name</span></span>    | <span data-ttu-id="00522-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="00522-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00522-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="00522-110">Scope</span></span>   |<span data-ttu-id="00522-111">Hlavní</span><span class="sxs-lookup"><span data-stu-id="00522-111">Major</span></span>|
|<span data-ttu-id="00522-112">Verze</span><span class="sxs-lookup"><span data-stu-id="00522-112">Version</span></span>|<span data-ttu-id="00522-113">4.5</span><span class="sxs-lookup"><span data-stu-id="00522-113">4.5</span></span>|
|<span data-ttu-id="00522-114">Typ</span><span class="sxs-lookup"><span data-stu-id="00522-114">Type</span></span>|<span data-ttu-id="00522-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="00522-115">Runtime</span></span>|
