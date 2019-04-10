---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235290"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="eef4a-101">Sdílení stavu relace s Asp.Net StateServer vyžaduje všechny servery ve webové farmě, aby používal stejnou verzi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="eef4a-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="eef4a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="eef4a-102">Details</span></span>|<span data-ttu-id="eef4a-103">Při povolování <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stavu relace, všechny servery v dané webové farmě musí používat stejnou verzi rozhraní .NET Framework v pořadí pro stav tak, aby správně sdílené.</span><span class="sxs-lookup"><span data-stu-id="eef4a-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="eef4a-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="eef4a-104">Suggestion</span></span>|<span data-ttu-id="eef4a-105">Ujistěte se, že upgrade verze rozhraní .NET Framework na webových serverech, které sdílejí stavu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="eef4a-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="eef4a-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="eef4a-106">Scope</span></span>|<span data-ttu-id="eef4a-107">Edge</span><span class="sxs-lookup"><span data-stu-id="eef4a-107">Edge</span></span>|
|<span data-ttu-id="eef4a-108">Version</span><span class="sxs-lookup"><span data-stu-id="eef4a-108">Version</span></span>|<span data-ttu-id="eef4a-109">4.5</span><span class="sxs-lookup"><span data-stu-id="eef4a-109">4.5</span></span>|
|<span data-ttu-id="eef4a-110">Type</span><span class="sxs-lookup"><span data-stu-id="eef4a-110">Type</span></span>|<span data-ttu-id="eef4a-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="eef4a-111">Runtime</span></span>|
|<span data-ttu-id="eef4a-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eef4a-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
