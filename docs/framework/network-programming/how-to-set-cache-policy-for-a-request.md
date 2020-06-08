---
title: 'Postupy: Nastavení zásad mezipaměti pro žádost'
description: Přečtěte si, jak nastavit zásady mezipaměti pro požadavek v .NET Framework. Tyto zásady mezipaměti umožňují použít prostředek z mezipaměti až do dne.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- request cache policies
ms.assetid: 39c15e40-586b-4ac9-9cce-146f74b7e545
ms.openlocfilehash: 248cbdd0921564898c5d3459cffa304793e85584
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502428"
---
# <a name="how-to-set-cache-policy-for-a-request"></a><span data-ttu-id="1bf3d-104">Postupy: Nastavení zásad mezipaměti pro žádost</span><span class="sxs-lookup"><span data-stu-id="1bf3d-104">How to: Set Cache Policy for a Request</span></span>
<span data-ttu-id="1bf3d-105">Následující příklad ukazuje nastavení zásad mezipaměti pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="1bf3d-105">The following example demonstrates setting a cache policy for a request.</span></span> <span data-ttu-id="1bf3d-106">Vzorový vstup je identifikátor URI, jako je například `http://www.contoso.com/` .</span><span class="sxs-lookup"><span data-stu-id="1bf3d-106">The example input is a URI such as `http://www.contoso.com/`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf3d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bf3d-107">Example</span></span>  
 <span data-ttu-id="1bf3d-108">Následující příklad kódu vytvoří zásadu mezipaměti, která umožňuje, aby byl požadovaný prostředek použit z mezipaměti, pokud nebyl v mezipaměti déle než jeden den.</span><span class="sxs-lookup"><span data-stu-id="1bf3d-108">The following code example creates a cache policy that allows the requested resource to be used from the cache if it has not been in the cache for longer than one day.</span></span> <span data-ttu-id="1bf3d-109">V příkladu se zobrazí zpráva, která označuje, zda byl prostředek použit z mezipaměti, například `"The response was retrieved from the cache : False."` – a poté zobrazí prostředek.</span><span class="sxs-lookup"><span data-stu-id="1bf3d-109">The example displays a message that indicates whether the resource was used from the cache—for example, `"The response was retrieved from the cache : False."`—and then displays the resource.</span></span> <span data-ttu-id="1bf3d-110">Požadavek může být vyplněn libovolnou mezipamětí mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="1bf3d-110">A request can be fulfilled by any cache between the client and server.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Cache;  
using System.IO;  
  
namespace Examples.System.Net.Cache  
{  
    public class CacheExample  
    {
        public static void UseCacheForOneDay(Uri resource)  
        {  
            // Create a policy that allows items in the cache  
            // to be used if they have been cached one day or less.  
            HttpRequestCachePolicy requestPolicy =
                new HttpRequestCachePolicy (HttpCacheAgeControl.MaxAge,  
                TimeSpan.FromDays(1));  
  
            WebRequest request = WebRequest.Create (resource);  
            // Set the policy for this request only.  
            request.CachePolicy = requestPolicy;  
            HttpWebResponse response = (HttpWebResponse)request.GetResponse();  
            // Determine whether the response was retrieved from the cache.  
            Console.WriteLine ("The response was retrieved from the cache : {0}.",  
               response.IsFromCache);  
            Stream s = response.GetResponseStream ();  
            StreamReader reader = new StreamReader (s);  
            // Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd());  
            reader.Close ();  
            s.Close();  
            response.Close();  
        }  
        public static void Main(string[] args)  
        {  
            if (args == null || args.Length != 1)  
            {  
                Console.WriteLine ("You must specify the URI to retrieve.");  
                return;  
            }  
            UseCacheForOneDay (new Uri(args[0]));  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Cache  
Imports System.IO  
Namespace Examples.System.Net.Cache  
    Public Class CacheExample  
        Public Shared Sub UseCacheForOneDay(ByVal resource As Uri)  
            ' Create a policy that allows items in the cache  
            ' to be used if they have been cached one day or less.  
            Dim requestPolicy As New HttpRequestCachePolicy _  
                  (HttpCacheAgeControl.MaxAge, TimeSpan.FromDays(1))  
            Dim request As WebRequest = WebRequest.Create(resource)  
            ' Set the policy for this request only.  
            request.CachePolicy = requestPolicy  
            Dim response As HttpWebResponse = _  
             CType(request.GetResponse(), HttpWebResponse)  
            ' Determine whether the response was retrieved from the cache.  
            Console.WriteLine("The response was retrieved from the cache : {0}.", _  
                response.IsFromCache)  
            Dim s As Stream = response.GetResponseStream()  
            Dim reader As New StreamReader(s)  
            ' Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd())  
            reader.Close()  
            s.Close()  
            response.Close()  
        End Sub  
        Public Shared Sub Main(ByVal args() As String)  
            If args Is Nothing OrElse args.Length <> 1 Then  
                Console.WriteLine("You must specify the URI to retrieve.")  
                Return  
            End If  
            UseCacheForOneDay(New Uri(args(0)))  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bf3d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bf3d-111">See also</span></span>

- [<span data-ttu-id="1bf3d-112">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="1bf3d-112">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="1bf3d-113">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="1bf3d-113">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="1bf3d-114">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="1bf3d-114">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="1bf3d-115">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="1bf3d-115">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="1bf3d-116">\<requestCaching>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1bf3d-116">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
