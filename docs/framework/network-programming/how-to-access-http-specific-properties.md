---
title: 'Postupy: Přístup k vlastnostem specifickým pro HTTP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: 107e57ca947012f5e2f65835d684f5e6068b3681
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176589"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="604ed-102">Postupy: Přístup k vlastnostem specifickým pro HTTP</span><span class="sxs-lookup"><span data-stu-id="604ed-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="604ed-103">Tento příklad ukazuje, jak chcete-li vypnout HTTP **Keep-alive** chování a získejte verzi protokolu číslo z webového serveru.</span><span class="sxs-lookup"><span data-stu-id="604ed-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="604ed-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="604ed-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =   
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="604ed-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="604ed-105">Compiling the Code</span></span>  
 <span data-ttu-id="604ed-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="604ed-106">This example requires:</span></span>  
  
-   <span data-ttu-id="604ed-107">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="604ed-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604ed-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="604ed-108">See also</span></span>

- [<span data-ttu-id="604ed-109">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="604ed-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="604ed-110">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="604ed-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="604ed-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="604ed-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
