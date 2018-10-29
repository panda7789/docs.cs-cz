---
title: Interakce zásad mezipaměti – maximální stáří a minimální novost
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
ms.openlocfilehash: eab50c308441ce73e994313d009588559302671e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199315"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="c611e-102">Interakce zásad mezipaměti – maximální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="c611e-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="c611e-103">K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, interakce vždy klienta mezipaměti zásad serveru opětovné ověření požadavků a výsledkem nejrestriktivnější zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c611e-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="c611e-104">Všechny příklady v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a končí 4. ledna.</span><span class="sxs-lookup"><span data-stu-id="c611e-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="c611e-105">Následující příklady znázorňují zásady ukládání do mezipaměti, která je výsledkem interakce maximální stáří (`maxAge`) a minimální novost (`minFresh`) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c611e-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="c611e-106">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 2 dny a `minFresh` není zadaný obsah je ověřit 3. ledna.</span><span class="sxs-lookup"><span data-stu-id="c611e-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="c611e-107">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 1 den, podle `maxAge`, až do ledna 3 je nový obsah.</span><span class="sxs-lookup"><span data-stu-id="c611e-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="c611e-108">Podle `minFresh`, až do ledna 3 je nový obsah.</span><span class="sxs-lookup"><span data-stu-id="c611e-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="c611e-109">Proto se musí ověřit obsah 3. ledna.</span><span class="sxs-lookup"><span data-stu-id="c611e-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="c611e-110">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 2 dny a `minFresh` = 2 dny podle `maxAge`, až do ledna 3 je nový obsah.</span><span class="sxs-lookup"><span data-stu-id="c611e-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="c611e-111">Podle `minFresh` až do ledna 2 je nový obsah.</span><span class="sxs-lookup"><span data-stu-id="c611e-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="c611e-112">Proto musíte ověřit obsah na 2. ledna.</span><span class="sxs-lookup"><span data-stu-id="c611e-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c611e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c611e-113">See Also</span></span>  
 [<span data-ttu-id="c611e-114">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="c611e-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="c611e-115">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="c611e-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="c611e-116">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="c611e-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="c611e-117">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="c611e-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="c611e-118">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="c611e-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="c611e-119">Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost</span><span class="sxs-lookup"><span data-stu-id="c611e-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
