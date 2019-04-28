---
title: 'Postupy: Přepsání globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: f822aa18b6eecaa1b1302ad6cc6b94f0b016e330
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642578"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="450cc-102">Postupy: Přepsání globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="450cc-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="450cc-103">Tento příklad odešle **WebRequest** k `www.contoso.com` globálního výběru proxy serveru, který přepíše s proxy serverem s názvem `alternateproxy` na portu 80.</span><span class="sxs-lookup"><span data-stu-id="450cc-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="450cc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="450cc-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="450cc-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="450cc-105">Compiling the Code</span></span>  
 <span data-ttu-id="450cc-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="450cc-106">This example requires:</span></span>  
  
- <span data-ttu-id="450cc-107">A [ `using` směrnice](~/docs/csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="450cc-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="450cc-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="450cc-108">See also</span></span>

- [<span data-ttu-id="450cc-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="450cc-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="450cc-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="450cc-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
