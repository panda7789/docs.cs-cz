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
# <a name="how-to-override-a-global-proxy-selection"></a>Postupy: Přepsání globálního výběru proxy serveru
Tento příklad pošle objekt WebRequest `www.contoso.com` , který přepíše výběr globálního proxy serveru pomocí proxy server s `alternateproxy` názvem na portu 80.  
  
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
  
- Direktiva pro obor názvů **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)  
  
## <a name="see-also"></a>Viz také:

- [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
- [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
