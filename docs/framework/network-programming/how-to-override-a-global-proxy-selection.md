---
title: 'Postupy: Přepsat globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 6973503f12e0e60ee139c5cd7da09ab319d70218
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592121"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="b8948-102">Postupy: Přepsat globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="b8948-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="b8948-103">Tento příklad odešle **WebRequest** k `www.contoso.com` globálního výběru proxy serveru, který přepíše s proxy serverem s názvem `alternateproxy` na portu 80.</span><span class="sxs-lookup"><span data-stu-id="b8948-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8948-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8948-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8948-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b8948-105">Compiling the Code</span></span>  
 <span data-ttu-id="b8948-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b8948-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b8948-107">A [ `using` směrnice](~/docs/csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b8948-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8948-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8948-108">See also</span></span>
- [<span data-ttu-id="b8948-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="b8948-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="b8948-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="b8948-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
