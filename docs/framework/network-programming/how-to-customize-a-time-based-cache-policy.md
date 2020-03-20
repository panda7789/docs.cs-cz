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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Postupy: Přizpůsobení zásad mezipaměti na základě času

Při vytváření zásad mezipaměti založených na čase můžete přizpůsobit chování ukládání do mezipaměti zadáním hodnot pro maximální stáří, minimální čerstvost, maximální neaktuálnost nebo datum synchronizace mezipaměti. Objekt <xref:System.Net.Cache.HttpRequestCachePolicy> poskytuje několik konstruktorů, které umožňují určit platné kombinace těchto hodnot.

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Vytvoření zásady mezipaměti založené na čase, která používá datum synchronizace mezipaměti

Vytvořte zásadu mezipaměti založenou na čase, <xref:System.DateTime> která používá <xref:System.Net.Cache.HttpRequestCachePolicy> datum synchronizace mezipaměti předáním objektu konstruktoru:

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

Výstup je podobný tomuto:

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Vytvoření zásady mezipaměti založené na čase, která je založena na minimální čerstvosti

Vytvořte zásadu mezipaměti založenou na čase, <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> která `cacheAgeControl` je založena na <xref:System.TimeSpan> minimální <xref:System.Net.Cache.HttpRequestCachePolicy> čerstvosti zadáním hodnoty parametru a předáním objektu konstruktoru:

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

Pro následující vyvolání:

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

Výstup bude následující:

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Vytvoření zásady mezipaměti založené na čase, která je založena na minimální čerstvosti a maximálním stáří

Vytvořte zásadu mezipaměti založenou na čase, která je <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> založena `cacheAgeControl` na minimální <xref:System.TimeSpan> čerstvosti <xref:System.Net.Cache.HttpRequestCachePolicy> a maximálním stáří, zadáním hodnoty parametru a předáním dvou objektů konstruktoru, jeden pro určení maximálního stáří prostředků a druhý pro určení minimální čerstvosti povolené pro objekt vrácený z mezipaměti:

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

Pro následující vyvolání:
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Výstup bude následující:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [\<requestCaching> Element (Nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
