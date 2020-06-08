---
title: 'Postupy: Přepsání globálního výběru proxy serveru'
description: Podle tohoto příkladu potlačíte výběr globálního proxy serveru odesláním WebRequest na adresu URL, která přepíše výběr pomocí proxy server.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 91f64775e2f401be9b740fe9e4c41e1087eb9617
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502506"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="03eea-103">Postupy: Přepsání globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="03eea-103">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="03eea-104">Tento příklad pošle **WebRequest** objekt WebRequest `www.contoso.com` , který přepíše výběr globálního proxy serveru pomocí proxy server s názvem `alternateproxy` na portu 80.</span><span class="sxs-lookup"><span data-stu-id="03eea-104">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03eea-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="03eea-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03eea-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="03eea-106">Compiling the Code</span></span>  
 <span data-ttu-id="03eea-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="03eea-107">This example requires:</span></span>  
  
- <span data-ttu-id="03eea-108">[ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) pro obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="03eea-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03eea-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03eea-109">See also</span></span>

- [<span data-ttu-id="03eea-110">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="03eea-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="03eea-111">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="03eea-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
