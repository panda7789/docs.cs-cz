---
title: 'Postupy: Povolení žádosti WebRequest, aby se používal proxy server pro komunikaci s internetem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d569603fe22e5d8c8f59d21c2777c7c1bfcd531d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048299"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Postupy: Povolení žádosti WebRequest, aby se používal proxy server pro komunikaci s internetem
Tento příklad vytvoří globální instanci proxy serveru, která <xref:System.Net.WebRequest> umožní použít proxy server ke komunikaci s internetem. V příkladu se předpokládá, že proxy server má `webproxy` název a že komunikuje na portu 80 standardního portu HTTP.  
  
## <a name="example"></a>Příklad  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Direktiva pro obor názvů **System.NET** . [ `using` ](../../csharp/language-reference/keywords/using-directive.md)  
  
## <a name="see-also"></a>Viz také:

- [Použití aplikačních protokolů](using-application-protocols.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
