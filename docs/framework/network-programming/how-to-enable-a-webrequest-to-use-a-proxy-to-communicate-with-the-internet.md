---
title: "Postupy: povolení WebRequest ke komunikaci s Internetem použití proxy serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 68871505e735485dd73d219b4144d56eabe21e43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Postupy: povolení WebRequest ke komunikaci s Internetem použití proxy serveru
Tento příklad vytvoří instanci globální proxy, která vám umožní žádné <xref:System.Net.WebRequest> ke komunikaci s Internetem použití proxy serveru. Příklad předpokládá, že je název proxy serveru `webproxy` a že komunikaci na portu 80, standardní port HTTP.  
  
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
  
-   Odkazuje na **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
