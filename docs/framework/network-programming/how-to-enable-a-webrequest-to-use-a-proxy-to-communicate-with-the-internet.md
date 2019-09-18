---
title: 'Postupy: Povolení žádosti WebRequest, aby se používal proxy server pro komunikaci s internetem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d569603fe22e5d8c8f59d21c2777c7c1bfcd531d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048299"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="ae0ed-102">Postupy: Povolení žádosti WebRequest, aby se používal proxy server pro komunikaci s internetem</span><span class="sxs-lookup"><span data-stu-id="ae0ed-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="ae0ed-103">Tento příklad vytvoří globální instanci proxy serveru, která <xref:System.Net.WebRequest> umožní použít proxy server ke komunikaci s internetem.</span><span class="sxs-lookup"><span data-stu-id="ae0ed-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="ae0ed-104">V příkladu se předpokládá, že proxy server má `webproxy` název a že komunikuje na portu 80 standardního portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae0ed-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae0ed-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae0ed-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae0ed-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ae0ed-106">Compiling the Code</span></span>  
 <span data-ttu-id="ae0ed-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ae0ed-107">This example requires:</span></span>  
  
- <span data-ttu-id="ae0ed-108">Direktiva pro obor názvů **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="ae0ed-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0ed-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae0ed-109">See also</span></span>

- [<span data-ttu-id="ae0ed-110">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="ae0ed-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="ae0ed-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="ae0ed-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
