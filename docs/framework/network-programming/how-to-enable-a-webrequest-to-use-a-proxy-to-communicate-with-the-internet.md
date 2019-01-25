---
title: 'Postupy: Povolit žádosti WebRequest pro komunikaci s Internetem použití proxy serveru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d8bcf20831a806694ab40ed7584365d8109e1460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689010"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Postupy: Povolit žádosti WebRequest pro komunikaci s Internetem použití proxy serveru
Tento příklad vytvoří instanci globální proxy, které umožní libovolné <xref:System.Net.WebRequest> ke komunikaci s Internetem použití proxy serveru. Příklad předpokládá, že je název proxy serveru `webproxy` a že komunikaci na portu 80, standardní port HTTP.  
  
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
  
-   A [ `using` směrnice](../../csharp/language-reference/keywords/using-directive.md) pro **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
- [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
