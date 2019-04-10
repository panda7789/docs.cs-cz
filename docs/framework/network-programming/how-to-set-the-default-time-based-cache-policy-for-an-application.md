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
ms.openlocfilehash: 99f9905109a4deabe3cfb2e3616913e84f565cb7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299121"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="44351-102">Postupy: Nastavení výchozích zásad mezipaměti na základě času pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="44351-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="44351-103">Umožňuje aplikaci mít své mezipaměti chování definované hlavičky posílané s prostředkem v mezipaměti a chování mezipaměti definované v části 13 a 14 k dispozici v dokumentu RFC 2616 výchozích zásad mezipaměti na základě času [(Internet Engineering Task Force Sdružení IETF)](https://www.ietf.org/) webu.</span><span class="sxs-lookup"><span data-stu-id="44351-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="44351-104">Toto je chování mezipaměti vhodné pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="44351-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="44351-105">Chcete-li nastavit automatické výchozí zásady pro aplikace</span><span class="sxs-lookup"><span data-stu-id="44351-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="44351-106">Vytvořte objekt výchozí zásady založené na čase.</span><span class="sxs-lookup"><span data-stu-id="44351-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="44351-107">Nastavte jako výchozí pro doménu aplikace objektu zásad.</span><span class="sxs-lookup"><span data-stu-id="44351-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44351-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="44351-108">Example</span></span>  
 <span data-ttu-id="44351-109">Tyto dva příklady v této části vytvořit identickými zásadami.</span><span class="sxs-lookup"><span data-stu-id="44351-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="44351-110">Následující příklad vytvoří výchozí zásady založené na čase a nastaví jej jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="44351-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="44351-111">Můžete také vytvořit pomocí zásad mezipaměti na základě času výchozí <xref:System.Net.Cache.RequestCachePolicy> třídy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="44351-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44351-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44351-112">See also</span></span>

- [<span data-ttu-id="44351-113">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="44351-113">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="44351-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="44351-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="44351-115">Zásady mezipaměti na základě umístění</span><span class="sxs-lookup"><span data-stu-id="44351-115">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="44351-116">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="44351-116">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="44351-117">\<requestCaching – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="44351-117">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
