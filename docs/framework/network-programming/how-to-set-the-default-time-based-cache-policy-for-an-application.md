---
title: "Postupy: nastavení výchozích zásad založené na čase mezipaměti pro aplikaci"
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
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d5166090a0682b71f74565e666c96ddadb7c6c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Postupy: nastavení výchozích zásad založené na čase mezipaměti pro aplikaci
Výchozí zásady založené na čase mezipaměti umožňuje aplikaci tak, aby měl své mezipaměti chování definované hlavičky odeslané s uložené v mezipaměti prostředků a chování mezipaměti definované v části 13 a 14 k dispozici v dokumentu RFC 2616 [http://www.ietf.org](http://www.ietf.org/). To je vhodné mezipaměti chování pro většinu aplikací.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Chcete-li nastavit automatické výchozí zásady pro aplikace  
  
1.  Vytvořte objekt výchozí zásady založené na čase.  
  
2.  Objekt zásad nastavte jako výchozí pro doménu aplikace.  
  
## <a name="example"></a>Příklad  
 Dva příklady v této části vytvořit identickými zásadami.  
  
 Následující příklad vytvoří výchozí zásady založené na čase a nastaví jej jako výchozí pro doménu aplikace.  
  
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
  
 Můžete taky vytvořit zásady založené na čase mezipaměti výchozí pomocí <xref:System.Net.Cache.RequestCachePolicy> třídy, jak je znázorněno v následujícím příkladu:  
  
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
 [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)  
 [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching – > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
