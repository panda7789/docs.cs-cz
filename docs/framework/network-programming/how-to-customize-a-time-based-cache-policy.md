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
ms.openlocfilehash: 5df070bb2cfef42d60247cad39f2a2f76963bae8
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894740"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="557a4-102">Postupy: Přizpůsobení zásad mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="557a4-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="557a4-103">Při vytváření zásad mezipaměti založeného na čase můžete přizpůsobit chování ukládání do mezipaměti zadáním hodnot maximálního stáří, minimální aktuálnosti, maximální zastaralosti nebo data synchronizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="557a4-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="557a4-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Objekt poskytuje několik konstruktorů, které umožňují zadat platné kombinace těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="557a4-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="557a4-105">Vytvoření zásady mezipaměti založené na čase, která používá Datum synchronizace mezipaměti</span><span class="sxs-lookup"><span data-stu-id="557a4-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="557a4-106">Vytvořte zásadu mezipaměti založenou na čase, která používá Datum synchronizace mezipaměti předáním <xref:System.DateTime> objektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="557a4-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
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
  
 <span data-ttu-id="557a4-107">Výstup je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="557a4-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="557a4-108">Vytvoření zásad mezipaměti založené na čase, který je založený na minimální aktuálnosti</span><span class="sxs-lookup"><span data-stu-id="557a4-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="557a4-109">Vytvořte zásady mezipaměti založené na čase, které jsou založeny na minimální <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> aktuálnosti, zadáním `cacheAgeControl` hodnoty <xref:System.TimeSpan> parametru a <xref:System.Net.Cache.HttpRequestCachePolicy> předání objektu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="557a4-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
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
  
 <span data-ttu-id="557a4-110">Pro následující vyvolání:</span><span class="sxs-lookup"><span data-stu-id="557a4-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="557a4-111">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="557a4-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="557a4-112">Vytvoření zásad mezipaměti založeného na čase, který vychází z minimální aktuálnosti a maximálního stáří</span><span class="sxs-lookup"><span data-stu-id="557a4-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="557a4-113">Vytvořte zásadu mezipaměti založenou na čase na základě minimální aktuálnosti a maximálního stáří tím, že <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> zadáte `cacheAgeControl` hodnotu parametru a <xref:System.Net.Cache.HttpRequestCachePolicy> předáte <xref:System.TimeSpan> do konstruktoru dva objekty, jednu pro určení maximálního stáří pro prostředky a sekundy určující minimální aktuálnost povolený pro objekt vrácený z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="557a4-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
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
  
 <span data-ttu-id="557a4-114">Pro následující vyvolání:</span><span class="sxs-lookup"><span data-stu-id="557a4-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="557a4-115">Výstup je:</span><span class="sxs-lookup"><span data-stu-id="557a4-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="557a4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="557a4-116">See also</span></span>

- [<span data-ttu-id="557a4-117">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="557a4-117">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="557a4-118">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="557a4-118">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="557a4-119">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="557a4-119">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="557a4-120">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="557a4-120">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="557a4-121">\<requestCaching – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="557a4-121">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
