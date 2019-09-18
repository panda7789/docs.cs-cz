---
title: 'Postupy: Přepsání globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048261"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="fed7b-102">Postupy: Přepsání globálního výběru proxy serveru</span><span class="sxs-lookup"><span data-stu-id="fed7b-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="fed7b-103">Tento příklad pošle objekt WebRequest `www.contoso.com` , který přepíše výběr globálního proxy serveru pomocí proxy server s `alternateproxy` názvem na portu 80.</span><span class="sxs-lookup"><span data-stu-id="fed7b-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fed7b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fed7b-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fed7b-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fed7b-105">Compiling the Code</span></span>  
 <span data-ttu-id="fed7b-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="fed7b-106">This example requires:</span></span>  
  
- <span data-ttu-id="fed7b-107">Direktiva pro obor názvů **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="fed7b-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed7b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fed7b-108">See also</span></span>

- [<span data-ttu-id="fed7b-109">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="fed7b-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="fed7b-110">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="fed7b-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
