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
ms.openlocfilehash: e21cfc28407ba67afdce8d72e5e52c12ab359059
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048843"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="b5e70-102">Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost</span><span class="sxs-lookup"><span data-stu-id="b5e70-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="b5e70-103">Aby bylo zajištěno, že se obsah vrátí do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na revalidy serveru vždy vede k nejzávažnějším zásadám mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5e70-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="b5e70-104">Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen v mezipaměti od 1. ledna do 4. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="b5e70-105">V následujících příkladech je maximální hodnota neaktuálnosti (`maxStale`) použita ve spojení s maximálním stářím (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="b5e70-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="b5e70-106">Pokud zásada cache nastaví `maxAge` = 5 dní a `maxStale` neurčuje `maxAge` hodnotu podle hodnoty, bude obsah použitelný až do 6. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="b5e70-107">V souladu s požadavky na revalidy serveru ale platnost obsahu vyprší 4. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="b5e70-108">Vzhledem k tomu, že datum vypršení platnosti obsahu je více konzervativní (dřív), `maxAge` má přednost před zásadou.</span><span class="sxs-lookup"><span data-stu-id="b5e70-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="b5e70-109">Platnost obsahu proto vyprší 4. ledna a musí se znovu ověřit, i když jeho maximální stáří nebylo dosaženo.</span><span class="sxs-lookup"><span data-stu-id="b5e70-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="b5e70-110">Pokud zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 3 `maxAge` dny, podle hodnoty, bude obsah použitelný až do 6. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="b5e70-111">`maxStale` Podle hodnoty je možné obsah použít až do 7. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="b5e70-112">Proto se obsah znovu ověří 6. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="b5e70-113">Pokud zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 1 `maxAge` den, podle hodnoty, bude obsah použitelný až do 6. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="b5e70-114">`maxStale` Podle hodnoty je možné obsah použít do 5. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="b5e70-115">Proto se obsah znovu ověří 5. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="b5e70-116">Pokud je maximální stáří menší než datum vypršení platnosti obsahu, podrobnější chování při ukládání do mezipaměti je vždycky stejné a maximální hodnota zastaralosti nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="b5e70-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="b5e70-117">Následující příklady ilustrují efekt nastavení maximální hodnoty neaktuálnosti (`maxStale`), pokud je dosaženo maximálního stáří (`maxAge`), než vyprší platnost obsahu:</span><span class="sxs-lookup"><span data-stu-id="b5e70-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="b5e70-118">Pokud zásady mezipaměti nastaví `maxAge` 1 den a neurčuje hodnotu pro `maxStale` hodnotu, bude se obsah znovu ověřit 2. ledna, i když nevypršela jeho platnost.</span><span class="sxs-lookup"><span data-stu-id="b5e70-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="b5e70-119">Pokud zásady mezipaměti nastaví `maxAge` hodnotu 1 den a `maxStale` = 3 dny, dojde k jejímu ověření znovu v lednu 2, aby se vynutilo více konzervativních zásad.</span><span class="sxs-lookup"><span data-stu-id="b5e70-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="b5e70-120">Pokud jsou zásady mezipaměti nastaveny `maxAge` na 1 den a `maxStale` = 1 den, obsah se znovu ověří 2. ledna.</span><span class="sxs-lookup"><span data-stu-id="b5e70-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e70-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5e70-121">See also</span></span>

- [<span data-ttu-id="b5e70-122">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="b5e70-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="b5e70-123">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b5e70-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="b5e70-124">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="b5e70-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="b5e70-125">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="b5e70-125">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="b5e70-126">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="b5e70-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="b5e70-127">Interakce zásad mezipaměti – minimální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="b5e70-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
