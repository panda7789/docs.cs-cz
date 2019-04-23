---
title: 'Postupy: Povolení žádosti WebRequest, aby se používal proxy server pro komunikaci s internetem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: a2179e767a0556f5223f2f4c1cc91708133120a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103698"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="66f3b-102">Postupy: Povolení žádosti WebRequest, aby se používal proxy server pro komunikaci s internetem</span><span class="sxs-lookup"><span data-stu-id="66f3b-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="66f3b-103">Tento příklad vytvoří instanci globální proxy, které umožní libovolné <xref:System.Net.WebRequest> ke komunikaci s Internetem použití proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="66f3b-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="66f3b-104">Příklad předpokládá, že je název proxy serveru `webproxy` a že komunikaci na portu 80, standardní port HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f3b-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66f3b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="66f3b-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66f3b-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="66f3b-106">Compiling the Code</span></span>  
 <span data-ttu-id="66f3b-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="66f3b-107">This example requires:</span></span>  
  
-   <span data-ttu-id="66f3b-108">A [ `using` směrnice](../../csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="66f3b-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f3b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66f3b-109">See also</span></span>

- [<span data-ttu-id="66f3b-110">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="66f3b-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="66f3b-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="66f3b-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
