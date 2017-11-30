---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca0a22ff1d06485658da75a46bd408a12a3a964c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Síťové programování ukázky](../../../docs/framework/network-programming/network-programming-samples.md)
