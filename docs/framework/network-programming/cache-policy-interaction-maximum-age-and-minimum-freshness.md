---
title: Interakce zásad mezipaměti – minimální stáří a minimální novost
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: 2ec958cc035ac62086cdd3e2844811accc181d47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048815"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="ad86e-102">Interakce zásad mezipaměti – minimální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="ad86e-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="ad86e-103">Chcete-li zajistit, že nejčerstvější obsah je vrácena do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na opětovné ověření serveru vždy za následek nejkonzervativnější zásady mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ad86e-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="ad86e-104">Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen do mezipaměti 1.</span><span class="sxs-lookup"><span data-stu-id="ad86e-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="ad86e-105">Následující příklady ilustrují zásady mezipaměti, které`maxAge`jsou výsledkem`minFresh`interakce maximálního stáří ( ) a minimální čerstvosti ( ).</span><span class="sxs-lookup"><span data-stu-id="ad86e-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="ad86e-106">Pokud sady zásad `maxAge` mezipaměti `minFresh` = 2 dny a není zadán, obsah je obnovena na 3.ledna.</span><span class="sxs-lookup"><span data-stu-id="ad86e-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="ad86e-107">Pokud jsou zásady mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 1 den, podle `maxAge`, obsah je čerstvé až do 3.ledna.</span><span class="sxs-lookup"><span data-stu-id="ad86e-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="ad86e-108">Podle `minFresh`, obsah je čerstvý až do 3.ledna.</span><span class="sxs-lookup"><span data-stu-id="ad86e-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="ad86e-109">Proto musí být obsah obnoven a 3.</span><span class="sxs-lookup"><span data-stu-id="ad86e-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="ad86e-110">Pokud jsou zásady mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 2 dny, podle `maxAge`, obsah je čerstvé až do 3.ledna.</span><span class="sxs-lookup"><span data-stu-id="ad86e-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="ad86e-111">Podle `minFresh` obsahu je čerstvé až do 2.ledna.</span><span class="sxs-lookup"><span data-stu-id="ad86e-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="ad86e-112">Proto musí být obsah obnoven a 2.</span><span class="sxs-lookup"><span data-stu-id="ad86e-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad86e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad86e-113">See also</span></span>

- [<span data-ttu-id="ad86e-114">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="ad86e-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="ad86e-115">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ad86e-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="ad86e-116">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="ad86e-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="ad86e-117">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="ad86e-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="ad86e-118">Konfigurace ukládání do mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="ad86e-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="ad86e-119">Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost</span><span class="sxs-lookup"><span data-stu-id="ad86e-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
