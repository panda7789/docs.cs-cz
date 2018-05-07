---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db2c42dab15b4282c5474c50f970ffe47a101215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> Třída poskytuje prostřednictvím kódu programu řízené naslouchací proces protokolu HTTP. Naslouchací proces je aktivní po dobu jeho existence <xref:System.Net.HttpListener> objekt a běží v rámci vaší aplikace.  
  
## <a name="httpsys"></a>HTTP. SYS  
 <xref:System.Net.HttpListener> Třída je postavená na HTTP.sys, což je naslouchací proces režimu jádra, která zpracovává veškeré přenosy dat protokolu HTTP pro systém Windows. Ovladač HTTP.sys poskytuje správu připojení, omezení šířky pásma a protokolování webového serveru. Použití `HttpCfg.exe` nástroje pro přidání certifikáty SSL. Další informace najdete v dokumentaci na [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) nástroj v [Server](http://go.microsoft.com/fwlink/?LinkID=178285) dokumentaci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [HTTP Server](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [Vylepšení zabezpečení v Internetové informační](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [Ukázka HttpListener ASPX hostitele aplikace](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [Ukázka HttpListener technologie](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)
