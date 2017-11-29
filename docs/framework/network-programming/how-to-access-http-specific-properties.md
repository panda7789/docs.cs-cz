---
title: "Postupy: přístup k vlastnosti specifické pro protokol HTTP"
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
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f277321ab94874970cb392dfe7f84a52a1cc2c40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="ad77a-102">Postupy: přístup k vlastnosti specifické pro protokol HTTP</span><span class="sxs-lookup"><span data-stu-id="ad77a-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="ad77a-103">Tento příklad ukazuje, jak vypnout HTTP **udržování** chování a získání verze protokolu číslo z webového serveru.</span><span class="sxs-lookup"><span data-stu-id="ad77a-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad77a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad77a-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad77a-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ad77a-105">Compiling the Code</span></span>  
 <span data-ttu-id="ad77a-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ad77a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="ad77a-107">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ad77a-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad77a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad77a-108">See Also</span></span>  
 [<span data-ttu-id="ad77a-109">Přístup k Internetu prostřednictvím proxy serveru</span><span class="sxs-lookup"><span data-stu-id="ad77a-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="ad77a-110">Pomocí protokolů aplikací</span><span class="sxs-lookup"><span data-stu-id="ad77a-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="ad77a-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="ad77a-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
