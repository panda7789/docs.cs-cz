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
ms.openlocfilehash: d4a35882d99a87ca5bf22fb386a87158e3c2d664
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154567"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="eaa3a-102">Postupy: Přizpůsobení zásad mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="eaa3a-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="eaa3a-103">Při vytváření zásad mezipaměti na základě času, můžete přizpůsobit chování ukládání do mezipaměti tak, že zadáte hodnoty pro maximální stáří, minimální novost, maximální neaktuálnost nebo datum synchronizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="eaa3a-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="eaa3a-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Objekt, který poskytuje několik konstruktorů, které vám umožňují určit platné kombinace těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="eaa3a-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="eaa3a-105">Vytvoření zásad mezipaměti na základě času, který používá data synchronizaci mezipaměti</span><span class="sxs-lookup"><span data-stu-id="eaa3a-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
-   <span data-ttu-id="eaa3a-106">Vytvoření zásady mezipaměti na základě času, který používá data synchronizaci mezipaměti předáním <xref:System.DateTime> objektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="eaa3a-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="eaa3a-107">Výstup je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="eaa3a-107">The output is similar to the following:</span></span>  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="eaa3a-108">Vytvoření zásad mezipaměti na základě času, který je založen na minimální novost</span><span class="sxs-lookup"><span data-stu-id="eaa3a-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
-   <span data-ttu-id="eaa3a-109">Vytvoření zásady mezipaměti na základě času, který je založen na minimální novost zadáním <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako `cacheAgeControl` hodnotu parametru a předávání <xref:System.TimeSpan> objektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="eaa3a-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="eaa3a-110">Následující volání:</span><span class="sxs-lookup"><span data-stu-id="eaa3a-110">For the following invocation:</span></span>  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="eaa3a-111">Vytvoření zásad mezipaměti na základě času, který je založen na aktuálnosti minimální a maximální stáří</span><span class="sxs-lookup"><span data-stu-id="eaa3a-111">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
-   <span data-ttu-id="eaa3a-112">Vytvoření zásady mezipaměti na základě času, který je založen na aktuálnosti minimální a maximální stáří zadáním <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako `cacheAgeControl` hodnotu parametru a předání dvou <xref:System.TimeSpan> objektů <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktor, chcete-li určit maximální stáří prostředky a druhý k určení minimální novost povolené pro objekt vrácený z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="eaa3a-112">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
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
  
 <span data-ttu-id="eaa3a-113">Následující volání:</span><span class="sxs-lookup"><span data-stu-id="eaa3a-113">For the following invocation:</span></span>  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaa3a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaa3a-114">See also</span></span>

- [<span data-ttu-id="eaa3a-115">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="eaa3a-115">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="eaa3a-116">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="eaa3a-116">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="eaa3a-117">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="eaa3a-117">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="eaa3a-118">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="eaa3a-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="eaa3a-119">\<requestCaching – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="eaa3a-119">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
