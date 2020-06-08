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
# <a name="how-to-override-a-global-proxy-selection"></a>Postupy: Přepsání globálního výběru proxy serveru
Tento příklad pošle **WebRequest** objekt WebRequest `www.contoso.com` , který přepíše výběr globálního proxy serveru pomocí proxy server s názvem `alternateproxy` na portu 80.  
  
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
  
- [ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) pro obor názvů **System.NET** .  
  
## <a name="see-also"></a>Viz také:

- [Použití aplikačních protokolů](using-application-protocols.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
