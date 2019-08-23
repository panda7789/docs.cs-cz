---
title: 'Postupy: Přepsání globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: e5f4dc22ad75dc4d4f7dc30f44e6ae304403ef16
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914532"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="ba1d4-102">Postupy: Přepsání globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="ba1d4-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="ba1d4-103">Tento příklad pošle objekt WebRequest `www.contoso.com` , který přepíše výběr globálního proxy serveru pomocí proxy server s `alternateproxy` názvem na portu 80.</span><span class="sxs-lookup"><span data-stu-id="ba1d4-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba1d4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba1d4-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba1d4-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ba1d4-105">Compiling the Code</span></span>  
 <span data-ttu-id="ba1d4-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ba1d4-106">This example requires:</span></span>  
  
- <span data-ttu-id="ba1d4-107">Direktiva pro obor názvů **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="ba1d4-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1d4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba1d4-108">See also</span></span>

- [<span data-ttu-id="ba1d4-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="ba1d4-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="ba1d4-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="ba1d4-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
