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
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="062eb-102">Postupy: Nastavení výchozích zásad mezipaměti na základě času pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="062eb-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="062eb-103">Výchozí zásada mezipaměti založená na čase umožňuje aplikaci, aby její chování mezipaměti bylo definováno záhlavími odeslanými s prostředky uloženými v mezipaměti a chováním mezipaměti definovanými v oddílech 13 a 14 rfc 2616, které jsou k dispozici na webu [IETF (Internet Engineering Task Force).](https://www.ietf.org/)</span><span class="sxs-lookup"><span data-stu-id="062eb-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="062eb-104">Toto je vhodné chování mezipaměti pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="062eb-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="062eb-105">Nastavení výchozí automatické zásady pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="062eb-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="062eb-106">Vytvořte výchozí objekt zásad založený na čase.</span><span class="sxs-lookup"><span data-stu-id="062eb-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="062eb-107">Nastavte objekt zásad jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="062eb-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="062eb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="062eb-108">Example</span></span>  
 <span data-ttu-id="062eb-109">Dva příklady v této části vytvořit stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="062eb-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="062eb-110">Následující příklad vytvoří výchozí zásadu založenou na čase a nastaví ji jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="062eb-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="062eb-111">Můžete také vytvořit výchozí zásady mezipaměti <xref:System.Net.Cache.RequestCachePolicy> založené na čase pomocí třídy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="062eb-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="062eb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="062eb-112">See also</span></span>

- [<span data-ttu-id="062eb-113">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="062eb-113">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="062eb-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="062eb-114">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="062eb-115">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="062eb-115">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="062eb-116">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="062eb-116">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="062eb-117">\<requestCaching> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="062eb-117">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
