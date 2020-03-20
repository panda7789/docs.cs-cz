---
title: 'Postupy: Přizpůsobení zásad mezipaměti na základě času'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040636"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="b40fe-102">Postupy: Přizpůsobení zásad mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="b40fe-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="b40fe-103">Při vytváření zásad mezipaměti založených na čase můžete přizpůsobit chování ukládání do mezipaměti zadáním hodnot pro maximální stáří, minimální čerstvost, maximální neaktuálnost nebo datum synchronizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b40fe-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="b40fe-104">Objekt <xref:System.Net.Cache.HttpRequestCachePolicy> poskytuje několik konstruktorů, které umožňují určit platné kombinace těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="b40fe-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="b40fe-105">Vytvoření zásady mezipaměti založené na čase, která používá datum synchronizace mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b40fe-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="b40fe-106">Vytvořte zásadu mezipaměti založenou na čase, <xref:System.DateTime> která používá <xref:System.Net.Cache.HttpRequestCachePolicy> datum synchronizace mezipaměti předáním objektu konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="b40fe-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
    Console.WriteLine("When: {0}", when);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy([when])
    Console.WriteLine("When: {0}", [when])
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="b40fe-107">Výstup je podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="b40fe-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="b40fe-108">Vytvoření zásady mezipaměti založené na čase, která je založena na minimální čerstvosti</span><span class="sxs-lookup"><span data-stu-id="b40fe-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="b40fe-109">Vytvořte zásadu mezipaměti založenou na čase, <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> která `cacheAgeControl` je založena na <xref:System.TimeSpan> minimální <xref:System.Net.Cache.HttpRequestCachePolicy> čerstvosti zadáním hodnoty parametru a předáním objektu konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="b40fe-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="b40fe-110">Pro následující vyvolání:</span><span class="sxs-lookup"><span data-stu-id="b40fe-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="b40fe-111">Výstup bude následující:</span><span class="sxs-lookup"><span data-stu-id="b40fe-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="b40fe-112">Vytvoření zásady mezipaměti založené na čase, která je založena na minimální čerstvosti a maximálním stáří</span><span class="sxs-lookup"><span data-stu-id="b40fe-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="b40fe-113">Vytvořte zásadu mezipaměti založenou na čase, která je <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> založena `cacheAgeControl` na minimální <xref:System.TimeSpan> čerstvosti <xref:System.Net.Cache.HttpRequestCachePolicy> a maximálním stáří, zadáním hodnoty parametru a předáním dvou objektů konstruktoru, jeden pro určení maximálního stáří prostředků a druhý pro určení minimální čerstvosti povolené pro objekt vrácený z mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="b40fe-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="b40fe-114">Pro následující vyvolání:</span><span class="sxs-lookup"><span data-stu-id="b40fe-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="b40fe-115">Výstup bude následující:</span><span class="sxs-lookup"><span data-stu-id="b40fe-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="b40fe-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b40fe-116">See also</span></span>

- [<span data-ttu-id="b40fe-117">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="b40fe-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="b40fe-118">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="b40fe-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="b40fe-119">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="b40fe-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="b40fe-120">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="b40fe-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="b40fe-121">\<requestCaching> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b40fe-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
