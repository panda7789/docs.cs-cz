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
ms.openlocfilehash: ae864b5f22f469d9a60b9faba90a5a66c65e8172
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="e6462-102">Postupy: nastavení výchozích zásad založené na čase mezipaměti pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="e6462-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="e6462-103">Výchozí zásady založené na čase mezipaměti umožňuje aplikaci tak, aby měl své mezipaměti chování definované hlavičky odeslané s uložené v mezipaměti prostředků a chování mezipaměti definované v části 13 a 14 k dispozici v dokumentu RFC 2616 [http://www.ietf.org](http://www.ietf.org/). To je vhodné mezipaměti chování pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="e6462-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="e6462-104">Chcete-li nastavit automatické výchozí zásady pro aplikace</span><span class="sxs-lookup"><span data-stu-id="e6462-104">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="e6462-105">Vytvořte objekt výchozí zásady založené na čase.</span><span class="sxs-lookup"><span data-stu-id="e6462-105">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="e6462-106">Objekt zásad nastavte jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6462-106">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6462-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6462-107">Example</span></span>  
 <span data-ttu-id="e6462-108">Dva příklady v této části vytvořit identickými zásadami.</span><span class="sxs-lookup"><span data-stu-id="e6462-108">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="e6462-109">Následující příklad vytvoří výchozí zásady založené na čase a nastaví jej jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6462-109">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="e6462-110">Můžete taky vytvořit zásady založené na čase mezipaměti výchozí pomocí <xref:System.Net.Cache.RequestCachePolicy> třídy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e6462-110">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6462-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6462-111">See Also</span></span>  
 [<span data-ttu-id="e6462-112">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="e6462-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="e6462-113">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e6462-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="e6462-114">Na základě umístění mezipaměti zásad</span><span class="sxs-lookup"><span data-stu-id="e6462-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="e6462-115">Zásady založené na čase mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e6462-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="e6462-116">\<requestCaching – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e6462-116">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
