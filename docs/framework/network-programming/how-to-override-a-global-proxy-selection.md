---
title: 'Postupy: Přepsání globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048261"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="49015-102">Postupy: Přepsání globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="49015-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="49015-103">Tento příklad odešle **WebRequest,** `www.contoso.com` který přepíše výběr globálního `alternateproxy` proxy serveru proxy s názvem na portu 80.</span><span class="sxs-lookup"><span data-stu-id="49015-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49015-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="49015-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49015-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="49015-105">Compiling the Code</span></span>  
 <span data-ttu-id="49015-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="49015-106">This example requires:</span></span>  
  
- <span data-ttu-id="49015-107">[ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) pro obor názvů **System.Net.**</span><span class="sxs-lookup"><span data-stu-id="49015-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49015-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="49015-108">See also</span></span>

- [<span data-ttu-id="49015-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="49015-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="49015-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="49015-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
