---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d3fecb9fe78ca54f68d3c5a97dae5d5dd9fbb28d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642370"
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> Třída poskytuje programově řízené naslouchací proces protokolu HTTP. Naslouchací proces je aktivní po dobu životnosti <xref:System.Net.HttpListener> objektu a běží v rámci vaší aplikace.  
  
## <a name="httpsys"></a>HTTP. SYS  
 <xref:System.Net.HttpListener> Třídy je založená na základě ovladače HTTP.sys, což je režim jádra naslouchací proces, který zpracovává všechen provoz protokolu HTTP pro Windows. Ovladač HTTP.sys poskytuje správu připojení, omezení šířky pásma a protokolování webového serveru. Použití `HttpCfg.exe` nástroj přidat certifikáty SSL. Další informace najdete v dokumentaci na [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) nástroj v [Server](https://go.microsoft.com/fwlink/?LinkID=178285) dokumentaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [HTTP Server](https://go.microsoft.com/fwlink/?LinkID=178285)
- [Vylepšení zabezpečení v Internetové informační](https://go.microsoft.com/fwlink/?LinkID=178286)
- [Ukázkové aplikace hostitele HttpListener ASPX](https://go.microsoft.com/fwlink/?LinkID=179560)
- [Ukázka technologie HttpListener](https://go.microsoft.com/fwlink/?LinkID=179558)
- [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)
