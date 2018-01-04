---
title: "Postupy: přizpůsobení zásady založené na čase mezipaměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86e56a2caed3ae7644b567c2e4af207689017c63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Postupy: přizpůsobení zásady založené na čase mezipaměti
Při vytváření zásad založené na čase mezipaměti můžete přizpůsobit chování ukládání do mezipaměti zadáním hodnot pro maximální stáří, aktuálnosti minimální, maximální typu prošlostí nebo mezipaměti synchronizace datum. <xref:System.Net.Cache.HttpRequestCachePolicy> Objektu obsahuje několik konstruktorů, které vám umožní zadat platné kombinace tyto hodnoty.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Chcete-li vytvořit zásadu založené na čase mezipaměti, která používá Datum synchronizace mezipaměti  
  
-   Vytvoření zásady založené na čase mezipaměti, která používá Datum synchronizace mezipaměti předáním <xref:System.DateTime> do objektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktor.  
  
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
  
 Výstup bude vypadat takto:  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Chcete-li vytvořit zásady založené na čase mezipaměti, který je založen na minimální aktuálnosti  
  
-   Vytvoření zásady založené na čase mezipaměti, který je založen na minimální aktuálnosti zadáním <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako `cacheAgeControl` hodnotu parametru a předávání <xref:System.TimeSpan> do objektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktor.  
  
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
  
 Následující volání:  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Chcete-li vytvořit zásady založené na čase mezipaměti, který je založen na aktuálnosti minimální a maximální stáří  
  
-   Vytvoření zásady založené na čase mezipaměti, která je na základě aktuálnosti minimální a maximální stáří zadáním <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako `cacheAgeControl` hodnotu parametru a předání dvou <xref:System.TimeSpan> objekty ke <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktor, má-li zadat maximální stáří prostředky a druhý k určení minimální aktuálnosti povolené pro objekt vrácené z mezipaměti.  
  
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
  
 Následující volání:  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
