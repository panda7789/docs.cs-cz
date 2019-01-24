---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: 70a40ea79a7f8993005607b0dd5a05f43597b003
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714016"
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
