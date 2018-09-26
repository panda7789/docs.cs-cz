---
title: 'Postupy: nastavení výchozích zásad mezipaměti na základě času pro aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e08026f8d1ec8b39f7ef3c2c34efad9e51b8fe9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074885"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="a9c1d-102">Postupy: nastavení výchozích zásad mezipaměti na základě času pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="a9c1d-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="a9c1d-103">Umožňuje aplikaci mít své mezipaměti chování definované hlavičky posílané s prostředkem v mezipaměti a chování mezipaměti definované v části 13 a 14 k dispozici v dokumentu RFC 2616 výchozích zásad mezipaměti na základě času [ http://www.ietf.org ](http://www.ietf.org/). Toto je chování mezipaměti vhodné pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="a9c1d-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="a9c1d-104">Chcete-li nastavit automatické výchozí zásady pro aplikace</span><span class="sxs-lookup"><span data-stu-id="a9c1d-104">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="a9c1d-105">Vytvořte objekt výchozí zásady založené na čase.</span><span class="sxs-lookup"><span data-stu-id="a9c1d-105">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="a9c1d-106">Nastavte jako výchozí pro doménu aplikace objektu zásad.</span><span class="sxs-lookup"><span data-stu-id="a9c1d-106">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c1d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9c1d-107">Example</span></span>  
 <span data-ttu-id="a9c1d-108">Tyto dva příklady v této části vytvořit identickými zásadami.</span><span class="sxs-lookup"><span data-stu-id="a9c1d-108">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="a9c1d-109">Následující příklad vytvoří výchozí zásady založené na čase a nastaví jej jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9c1d-109">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="a9c1d-110">Můžete také vytvořit pomocí zásad mezipaměti na základě času výchozí <xref:System.Net.Cache.RequestCachePolicy> třídy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a9c1d-110">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9c1d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9c1d-111">See Also</span></span>  
 [<span data-ttu-id="a9c1d-112">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="a9c1d-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="a9c1d-113">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="a9c1d-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="a9c1d-114">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="a9c1d-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="a9c1d-115">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="a9c1d-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="a9c1d-116">\<requestCaching – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="a9c1d-116">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
