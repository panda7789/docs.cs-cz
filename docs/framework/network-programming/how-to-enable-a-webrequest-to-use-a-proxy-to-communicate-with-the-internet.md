---
title: 'Postupy: Povolit žádosti WebRequest pro komunikaci s Internetem použití proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d8bcf20831a806694ab40ed7584365d8109e1460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689010"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="1e30c-102">Postupy: Povolit žádosti WebRequest pro komunikaci s Internetem použití proxy serveru</span><span class="sxs-lookup"><span data-stu-id="1e30c-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="1e30c-103">Tento příklad vytvoří instanci globální proxy, které umožní libovolné <xref:System.Net.WebRequest> ke komunikaci s Internetem použití proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="1e30c-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="1e30c-104">Příklad předpokládá, že je název proxy serveru `webproxy` a že komunikaci na portu 80, standardní port HTTP.</span><span class="sxs-lookup"><span data-stu-id="1e30c-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e30c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e30c-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e30c-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1e30c-106">Compiling the Code</span></span>  
 <span data-ttu-id="1e30c-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1e30c-107">This example requires:</span></span>  
  
-   <span data-ttu-id="1e30c-108">A [ `using` směrnice](../../csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e30c-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e30c-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e30c-109">See also</span></span>
- [<span data-ttu-id="1e30c-110">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="1e30c-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="1e30c-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="1e30c-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
