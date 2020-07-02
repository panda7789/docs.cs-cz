---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619939"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="54640-101">Sdílení stavu relace s Asp.Net StateServer vyžaduje, aby všechny servery ve webové farmě používaly stejnou verzi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54640-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="54640-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="54640-102">Details</span></span>

<span data-ttu-id="54640-103">Při povolování <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> stavu relace musí všechny servery v dané webové farmě používat stejnou verzi .NET Framework, aby bylo možné stav správně sdílet.</span><span class="sxs-lookup"><span data-stu-id="54640-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="54640-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="54640-104">Suggestion</span></span>

<span data-ttu-id="54640-105">Ujistěte se, že upgradujete .NET Framework verze na webových serverech, které sdílejí stav ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="54640-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="54640-106">Name</span><span class="sxs-lookup"><span data-stu-id="54640-106">Name</span></span>    | <span data-ttu-id="54640-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="54640-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="54640-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="54640-108">Scope</span></span>   |<span data-ttu-id="54640-109">Edge</span><span class="sxs-lookup"><span data-stu-id="54640-109">Edge</span></span>|
|<span data-ttu-id="54640-110">Verze</span><span class="sxs-lookup"><span data-stu-id="54640-110">Version</span></span>|<span data-ttu-id="54640-111">4.5</span><span class="sxs-lookup"><span data-stu-id="54640-111">4.5</span></span>|
|<span data-ttu-id="54640-112">Typ</span><span class="sxs-lookup"><span data-stu-id="54640-112">Type</span></span>|<span data-ttu-id="54640-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="54640-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="54640-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="54640-114">Affected APIs</span></span>

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
