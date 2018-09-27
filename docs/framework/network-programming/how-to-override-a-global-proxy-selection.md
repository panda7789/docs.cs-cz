---
title: 'Postupy: přepsání globálního výběru proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2be271123e34f155a79269d3b810c50fe24a40c6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235934"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Postupy: přepsání globálního výběru proxy serveru
Tento příklad odešle **WebRequest** k `www.contoso.com` globálního výběru proxy serveru, který přepíše s proxy serverem s názvem `alternateproxy` na portu 80.  
  
## <a name="example"></a>Příklad  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A [ `using` směrnice](~/docs/csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
