---
title: 'Postupy: přepsání globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 244315b5df4200524685bc5b9fb75a0d7fd9b39e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869101"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="36ccd-102">Postupy: přepsání globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="36ccd-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="36ccd-103">Tento příklad odešle **WebRequest** k `www.contoso.com` globálního výběru proxy serveru, který přepíše s proxy serverem s názvem `alternateproxy` na portu 80.</span><span class="sxs-lookup"><span data-stu-id="36ccd-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36ccd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="36ccd-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="36ccd-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="36ccd-105">Compiling the Code</span></span>  
 <span data-ttu-id="36ccd-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="36ccd-106">This example requires:</span></span>  
  
-   <span data-ttu-id="36ccd-107">A [ `using` směrnice](~/docs/csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="36ccd-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ccd-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="36ccd-108">See Also</span></span>  
 [<span data-ttu-id="36ccd-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="36ccd-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="36ccd-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="36ccd-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
