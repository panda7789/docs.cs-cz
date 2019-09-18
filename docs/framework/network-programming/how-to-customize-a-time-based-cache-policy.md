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
ms.openlocfilehash: c28c6daf9b873a19291b1636112eae6546412be2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048320"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Postupy: Přizpůsobení zásad mezipaměti na základě času
Při vytváření zásad mezipaměti založeného na čase můžete přizpůsobit chování ukládání do mezipaměti zadáním hodnot maximálního stáří, minimální aktuálnosti, maximální zastaralosti nebo data synchronizace mezipaměti. <xref:System.Net.Cache.HttpRequestCachePolicy> Objekt poskytuje několik konstruktorů, které umožňují zadat platné kombinace těchto hodnot.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Vytvoření zásady mezipaměti založené na čase, která používá Datum synchronizace mezipaměti  
  
- Vytvořte zásadu mezipaměti založenou na čase, která používá Datum synchronizace mezipaměti předáním <xref:System.DateTime> objektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktoru.  
  
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
  
 Výstup je podobný následujícímu:  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Vytvoření zásad mezipaměti založené na čase, který je založený na minimální aktuálnosti  
  
- Vytvořte zásady mezipaměti založené na čase, které jsou založeny na minimální <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> aktuálnosti, zadáním `cacheAgeControl` hodnoty <xref:System.TimeSpan> parametru a <xref:System.Net.Cache.HttpRequestCachePolicy> předání objektu konstruktoru.  
  
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
  
 Pro následující vyvolání:  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 Výstup je:
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Vytvoření zásad mezipaměti založeného na čase, který vychází z minimální aktuálnosti a maximálního stáří  
  
- Vytvořte zásadu mezipaměti založenou na čase na základě minimální aktuálnosti a maximálního stáří tím, že <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> zadáte `cacheAgeControl` hodnotu parametru a <xref:System.Net.Cache.HttpRequestCachePolicy> předáte <xref:System.TimeSpan> do konstruktoru dva objekty, jednu pro určení maximálního stáří pro prostředky a sekundy určující minimální aktuálnost povolený pro objekt vrácený z mezipaměti.  
  
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
  
 Pro následující vyvolání:  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Výstup je:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [\<requestCaching – element > (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
