---
title: 'Postupy: Nastavení výchozích zásad mezipaměti na základě času pro aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 0aaa26f67ef1ef191060e682690fa14de328b812
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048093"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Postupy: Nastavení výchozích zásad mezipaměti na základě času pro aplikaci
Výchozí zásada mezipaměti založená na čase umožňuje aplikaci, aby její chování mezipaměti bylo definováno záhlavími odeslanými s prostředky uloženými v mezipaměti a chováním mezipaměti definovanými v oddílech 13 a 14 rfc 2616, které jsou k dispozici na webu [IETF (Internet Engineering Task Force).](https://www.ietf.org/) Toto je vhodné chování mezipaměti pro většinu aplikací.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Nastavení výchozí automatické zásady pro aplikaci  
  
1. Vytvořte výchozí objekt zásad založený na čase.  
  
2. Nastavte objekt zásad jako výchozí pro doménu aplikace.  
  
## <a name="example"></a>Příklad  
 Dva příklady v této části vytvořit stejné zásady.  
  
 Následující příklad vytvoří výchozí zásadu založenou na čase a nastaví ji jako výchozí pro doménu aplikace.  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 Můžete také vytvořit výchozí zásady mezipaměti <xref:System.Net.Cache.RequestCachePolicy> založené na čase pomocí třídy, jak je znázorněno v následujícím příkladu:  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [\<requestCaching> Element (Nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
