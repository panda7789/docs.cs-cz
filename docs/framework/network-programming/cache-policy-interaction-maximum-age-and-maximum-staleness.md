---
title: Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4ee2b3a0a97a0526802d6cb4c8f546a5ec4e7b85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392603"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="9caa4-102">Interakce zásad do mezipaměti – maximální stáří a maximální typu Prošlostí</span><span class="sxs-lookup"><span data-stu-id="9caa4-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="9caa4-103">K zajištění, že nejčerstvější obsah se vrátí do klientské aplikace, výsledkem interakce klienta mezipaměti zásad a server opětovné ověření požadavků vždy nejvíce konzervativní zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9caa4-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="9caa4-104">V příkladech v tomto tématu ilustrují zásady ukládání do mezipaměti pro prostředek, který se uloží do mezipaměti na 1. ledna a jeho platnost vyprší v lednu 4.</span><span class="sxs-lookup"><span data-stu-id="9caa4-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="9caa4-105">V následujících příkladech, hodnota maximální typu prošlostí (`maxStale`) se používá ve spojení s maximální stáří (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="9caa4-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="9caa4-106">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 5 dní a neurčuje `maxStale` hodnoty, podle `maxAge` hodnota, obsah je až 6 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="9caa4-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="9caa4-107">V souladu s požadavky opětovné ověření serveru, ale obsah vyprší na leden 4.</span><span class="sxs-lookup"><span data-stu-id="9caa4-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="9caa4-108">Protože datum vypršení platnosti obsahu je více konzervativní (dříve), pak má přednost před `maxAge` zásad.</span><span class="sxs-lookup"><span data-stu-id="9caa4-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="9caa4-109">Obsah, tedy vyprší na leden 4 a musí být obnoveny, i když nedosáhla své maximální stáří.</span><span class="sxs-lookup"><span data-stu-id="9caa4-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="9caa4-110">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 5 dní a `maxStale` = 3 dny, podle požadavků `maxAge` hodnota, obsah je až 6 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="9caa4-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="9caa4-111">Podle požadavků `maxStale` hodnota, obsah je až 7 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="9caa4-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="9caa4-112">Proto získá obsahu obnoveny v lednu 6.</span><span class="sxs-lookup"><span data-stu-id="9caa4-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="9caa4-113">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 5 dní a `maxStale` = 1 den, podle požadavků `maxAge` hodnota, obsah je až 6 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="9caa4-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="9caa4-114">Podle požadavků `maxStale` hodnota, obsah je až 5 leden použitelné.</span><span class="sxs-lookup"><span data-stu-id="9caa4-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="9caa4-115">Proto získá obsahu obnoveny v lednu 5.</span><span class="sxs-lookup"><span data-stu-id="9caa4-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="9caa4-116">Když maximální stáří je menší než datum vypršení platnosti obsahu, mají vždycky přednost více konzervativní chování ukládání do mezipaměti a hodnota typu maximální prošlostí nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="9caa4-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="9caa4-117">Následující příklady ilustrují účinek nastavení maximální typu prošlostí (`maxStale`) hodnotu v případě maximální stáří (`maxAge`) je dosažen předtím, než vyprší platnost obsahu:</span><span class="sxs-lookup"><span data-stu-id="9caa4-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="9caa4-118">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 1 den a neurčuje hodnotu `maxStale` hodnotu, obsah je znovu ověřeny v lednu 2, i když nevypršela platnost.</span><span class="sxs-lookup"><span data-stu-id="9caa4-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="9caa4-119">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 1 den a `maxStale` = 3 dny, obsah je znovu ověřeny v lednu 2 k vynucení více konzervativní nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="9caa4-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="9caa4-120">Pokud je nastaví zásady ukládání do mezipaměti `maxAge` = 1 den a `maxStale` = 1 den, obsah je znovu ověřeny v lednu 2.</span><span class="sxs-lookup"><span data-stu-id="9caa4-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9caa4-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9caa4-121">See Also</span></span>  
 [<span data-ttu-id="9caa4-122">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="9caa4-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="9caa4-123">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9caa4-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="9caa4-124">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="9caa4-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="9caa4-125">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="9caa4-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="9caa4-126">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="9caa4-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="9caa4-127">Interakce zásad mezipaměti – minimální stáří a minimální novost</span><span class="sxs-lookup"><span data-stu-id="9caa4-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
