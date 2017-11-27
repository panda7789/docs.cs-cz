---
title: "Postupy: povolení WebRequest ke komunikaci s Internetem použití proxy serveru"
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
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 937f4ac06ef4788c42b364fe03226e32a55572f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="e1e11-102">Postupy: povolení WebRequest ke komunikaci s Internetem použití proxy serveru</span><span class="sxs-lookup"><span data-stu-id="e1e11-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="e1e11-103">Tento příklad vytvoří instanci globální proxy, která vám umožní žádné <xref:System.Net.WebRequest> ke komunikaci s Internetem použití proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e1e11-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="e1e11-104">Příklad předpokládá, že je název proxy serveru `webproxy` a že komunikaci na portu 80, standardní port HTTP.</span><span class="sxs-lookup"><span data-stu-id="e1e11-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e11-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1e11-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1e11-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e1e11-106">Compiling the Code</span></span>  
 <span data-ttu-id="e1e11-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e1e11-107">This example requires:</span></span>  
  
-   <span data-ttu-id="e1e11-108">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e1e11-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e11-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1e11-109">See Also</span></span>  
 [<span data-ttu-id="e1e11-110">Pomocí protokolů aplikací</span><span class="sxs-lookup"><span data-stu-id="e1e11-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="e1e11-111">Přístup k Internetu prostřednictvím proxy serveru</span><span class="sxs-lookup"><span data-stu-id="e1e11-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
