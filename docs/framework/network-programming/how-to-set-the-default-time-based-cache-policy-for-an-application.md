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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048093"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="1c799-102">Postupy: Nastavení výchozích zásad mezipaměti na základě času pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="1c799-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="1c799-103">Výchozí zásady mezipaměti založené na čase umožňují aplikaci, aby její chování mezipaměti bylo definované pomocí hlaviček odeslaných s prostředkem uloženým v mezipaměti, a chování mezipaměti definované v oddílech 13 a 14 RFC 2616, které jsou k dispozici v [IETF (Internet Engineering Task Force)](https://www.ietf.org/) . webu.</span><span class="sxs-lookup"><span data-stu-id="1c799-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="1c799-104">Toto je vhodné chování mezipaměti pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="1c799-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="1c799-105">Nastavení výchozích automatických zásad pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="1c799-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="1c799-106">Vytvoří výchozí objekt zásad založený na čase.</span><span class="sxs-lookup"><span data-stu-id="1c799-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="1c799-107">Nastavte objekt zásad jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c799-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c799-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c799-108">Example</span></span>  
 <span data-ttu-id="1c799-109">Dva příklady v této části poskytují stejné zásady.</span><span class="sxs-lookup"><span data-stu-id="1c799-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="1c799-110">Následující příklad vytvoří výchozí zásadu založenou na čase a nastaví ji jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c799-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="1c799-111">Můžete také vytvořit výchozí zásadu mezipaměti založenou na čase pomocí <xref:System.Net.Cache.RequestCachePolicy> třídy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1c799-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c799-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c799-112">See also</span></span>

- [<span data-ttu-id="1c799-113">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="1c799-113">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="1c799-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="1c799-114">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="1c799-115">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="1c799-115">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="1c799-116">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="1c799-116">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="1c799-117">\<requestCaching – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1c799-117">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
