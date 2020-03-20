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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048843"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="46f87-102">Interakce zásad mezipaměti – maximální stáří a maximální neaktuálnost</span><span class="sxs-lookup"><span data-stu-id="46f87-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="46f87-103">Chcete-li zajistit, že nejčerstvější obsah je vrácena do klientské aplikace, interakce zásad mezipaměti klienta a požadavky na opětovné ověření serveru vždy za následek nejkonzervativnější zásady mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="46f87-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="46f87-104">Všechny příklady v tomto tématu ilustrují zásady mezipaměti pro prostředek, který je uložen do mezipaměti 1.</span><span class="sxs-lookup"><span data-stu-id="46f87-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="46f87-105">V následujících příkladech se používá maximální`maxStale`hodnota neaktuálnosti (`maxAge`) ve spojení s maximálním věkem ( ):</span><span class="sxs-lookup"><span data-stu-id="46f87-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="46f87-106">Pokud sada zásad `maxAge` mezipaměti = 5 `maxStale` dní a neurčuje hodnotu, podle `maxAge` hodnoty je obsah použitelný až do 6.</span><span class="sxs-lookup"><span data-stu-id="46f87-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="46f87-107">Podle požadavků serveru na prodloužení platnosti však platnost obsahu vyprší 4.</span><span class="sxs-lookup"><span data-stu-id="46f87-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="46f87-108">Vzhledem k tomu, že datum vypršení platnosti `maxAge` obsahu je konzervativnější (dříve), má přednost před zásadou.</span><span class="sxs-lookup"><span data-stu-id="46f87-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="46f87-109">Obsah proto vyprší 4.</span><span class="sxs-lookup"><span data-stu-id="46f87-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="46f87-110">Pokud jsou zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 3 dny, podle `maxAge` hodnoty, obsah je použitelný až do 6.</span><span class="sxs-lookup"><span data-stu-id="46f87-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="46f87-111">Podle `maxStale` hodnoty je obsah použitelný až do 7.</span><span class="sxs-lookup"><span data-stu-id="46f87-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="46f87-112">Proto bude obsah obnoven 6.</span><span class="sxs-lookup"><span data-stu-id="46f87-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="46f87-113">Pokud jsou zásady mezipaměti nastaví `maxAge` = 5 dní a `maxStale` = 1 den, podle `maxAge` hodnoty, obsah je použitelný až do 6.</span><span class="sxs-lookup"><span data-stu-id="46f87-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="46f87-114">Podle `maxStale` hodnoty je obsah použitelný až do 5.</span><span class="sxs-lookup"><span data-stu-id="46f87-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="46f87-115">Proto bude obsah obnoven 5.</span><span class="sxs-lookup"><span data-stu-id="46f87-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="46f87-116">Pokud je maximální stáří menší než datum vypršení platnosti obsahu, vždy převládá konzervativnější chování ukládání do mezipaměti a maximální hodnota neaktuálnosti nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="46f87-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="46f87-117">Následující příklady ilustrují účinek nastavení`maxStale`maximální hodnoty neaktuálnosti ( ) při dosažení maximálního stáří (`maxAge`) před vypršením platnosti obsahu:</span><span class="sxs-lookup"><span data-stu-id="46f87-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="46f87-118">Pokud zásady `maxAge` mezipaměti nastaví = 1 `maxStale` den a neurčuje hodnotu pro hodnotu, obsah je obnovena na 2 ledna, i když jeho platnost nevypršela.</span><span class="sxs-lookup"><span data-stu-id="46f87-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="46f87-119">Pokud sady zásad `maxAge` mezipaměti `maxStale` = 1 den a = 3 dny, obsah je obnovena na 2 ledna vynutit konzervativnější nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="46f87-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="46f87-120">Pokud sady zásad `maxAge` mezipaměti `maxStale` = 1 den a = 1 den, obsah je obnovena na 2 ledna.</span><span class="sxs-lookup"><span data-stu-id="46f87-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f87-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="46f87-121">See also</span></span>

- [<span data-ttu-id="46f87-122">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="46f87-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="46f87-123">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="46f87-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="46f87-124">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="46f87-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="46f87-125">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="46f87-125">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="46f87-126">Konfigurace ukládání do mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="46f87-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="46f87-127">Interakce zásad mezipaměti – minimální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="46f87-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
