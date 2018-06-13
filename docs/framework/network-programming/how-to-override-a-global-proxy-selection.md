---
title: 'Postupy: potlačení výběr globální Proxy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c10cff979a18d8e07a1e7089f96157e4c38f040e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393903"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="1eef7-102">Postupy: potlačení výběr globální Proxy</span><span class="sxs-lookup"><span data-stu-id="1eef7-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="1eef7-103">Tento příklad odešle **WebRequest** k www.contoso.com který přepíše výběr globální proxy s proxy serverem s názvem `alternateproxy` na portu 80.</span><span class="sxs-lookup"><span data-stu-id="1eef7-103">This example sends a **WebRequest** to www.contoso.com that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eef7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1eef7-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1eef7-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1eef7-105">Compiling the Code</span></span>  
 <span data-ttu-id="1eef7-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1eef7-106">This example requires:</span></span>  
  
-   <span data-ttu-id="1eef7-107">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1eef7-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eef7-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1eef7-108">See Also</span></span>  
 [<span data-ttu-id="1eef7-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="1eef7-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="1eef7-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="1eef7-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
