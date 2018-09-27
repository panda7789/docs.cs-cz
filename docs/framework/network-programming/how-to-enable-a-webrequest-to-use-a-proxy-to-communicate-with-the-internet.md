---
title: 'Postupy: povolení WebRequest ke komunikaci s Internetem použití proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 86bf21580db9bc6d9890f0935e283b653ba2e0b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397787"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="ff722-102">Postupy: povolení WebRequest ke komunikaci s Internetem použití proxy serveru</span><span class="sxs-lookup"><span data-stu-id="ff722-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="ff722-103">Tento příklad vytvoří instanci globální proxy, které umožní libovolné <xref:System.Net.WebRequest> ke komunikaci s Internetem použití proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="ff722-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="ff722-104">Příklad předpokládá, že je název proxy serveru `webproxy` a že komunikaci na portu 80, standardní port HTTP.</span><span class="sxs-lookup"><span data-stu-id="ff722-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff722-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff722-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff722-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ff722-106">Compiling the Code</span></span>  
 <span data-ttu-id="ff722-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ff722-107">This example requires:</span></span>  
  
-   <span data-ttu-id="ff722-108">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ff722-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff722-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff722-109">See Also</span></span>  
 [<span data-ttu-id="ff722-110">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="ff722-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="ff722-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="ff722-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
