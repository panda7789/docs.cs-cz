---
title: Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: 18a73a46bc4b463d0a5f5690afe6d1109e06171c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207133"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="d058b-102">Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost</span><span class="sxs-lookup"><span data-stu-id="d058b-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="d058b-103">K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, interakce vždy klienta mezipaměti zásad serveru opětovné ověření požadavků a výsledkem nejrestriktivnější zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d058b-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="d058b-104">Všechny příklady v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a končí 4. ledna.</span><span class="sxs-lookup"><span data-stu-id="d058b-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="d058b-105">V následujících příkladech hodnota maximální neaktuálnost (`maxStale`) se používá ve spojení s maximální stáří (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="d058b-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="d058b-106">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 5 dní a nemá `maxStale` hodnoty, podle `maxAge` hodnotu, je obsah použitelné až do ledna 6.</span><span class="sxs-lookup"><span data-stu-id="d058b-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="d058b-107">Nicméně podle požadavků na opětovné ověření serveru, platnost obsahu vyprší dne od 4.</span><span class="sxs-lookup"><span data-stu-id="d058b-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="d058b-108">Protože datum vypršení platnosti obsahu je konzervativnější (dřív), má přednost před `maxAge` zásad.</span><span class="sxs-lookup"><span data-stu-id="d058b-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="d058b-109">Proto obsahu vyprší dne 4 a musí ověřit, i když nedosáhla své maximální stáří.</span><span class="sxs-lookup"><span data-stu-id="d058b-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="d058b-110">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 3 dny, podle `maxAge` hodnotu, je obsah použitelné až do ledna 6.</span><span class="sxs-lookup"><span data-stu-id="d058b-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="d058b-111">Podle `maxStale` hodnotu, je obsah použitelné až do ledna 7.</span><span class="sxs-lookup"><span data-stu-id="d058b-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="d058b-112">Proto získá obsah ověřit v lednu 6.</span><span class="sxs-lookup"><span data-stu-id="d058b-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="d058b-113">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 1 den, podle `maxAge` hodnotu, je obsah použitelné až do ledna 6.</span><span class="sxs-lookup"><span data-stu-id="d058b-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="d058b-114">Podle `maxStale` hodnotu, je obsah použitelné až do ledna 5.</span><span class="sxs-lookup"><span data-stu-id="d058b-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="d058b-115">Proto získá ověřit obsah na 5. ledna.</span><span class="sxs-lookup"><span data-stu-id="d058b-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="d058b-116">Při maximální stáří je menší než datum vypršení platnosti obsahu, vždycky existuje konzervativnější chování ukládání do mezipaměti a maximální neaktuálnost hodnota nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="d058b-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="d058b-117">Následující příklady znázorňují účinek nastavení maximální neaktuálnost (`maxStale`) hodnotu v případě maximální stáří (`maxAge`) je dosažen předtím, než vyprší platnost obsahu:</span><span class="sxs-lookup"><span data-stu-id="d058b-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="d058b-118">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 1 den a nemá hodnotu `maxStale` hodnotu, obsah je ověřit na 2. ledna i v případě, že nevypršela jeho platnost.</span><span class="sxs-lookup"><span data-stu-id="d058b-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="d058b-119">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 1 den a `maxStale` = 3 dny, obsah je ověřit na 2. ledna konzervativnější nastavení zásad vynucovat.</span><span class="sxs-lookup"><span data-stu-id="d058b-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="d058b-120">Pokud zásady ukládání do mezipaměti nastaví `maxAge` = 1 den a `maxStale` = 1 den, obsah je ověřit na 2. ledna.</span><span class="sxs-lookup"><span data-stu-id="d058b-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d058b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d058b-121">See also</span></span>

- [<span data-ttu-id="d058b-122">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="d058b-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="d058b-123">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="d058b-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="d058b-124">Zásady mezipaměti na základě umístění</span><span class="sxs-lookup"><span data-stu-id="d058b-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="d058b-125">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="d058b-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="d058b-126">Konfigurace ukládání do mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="d058b-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [<span data-ttu-id="d058b-127">Interakce zásad mezipaměti – minimální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="d058b-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
