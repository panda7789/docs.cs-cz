---
title: "Osvědčené postupy pro System.NET – třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 90722abbdb4568be115c0ac77007d5f18984df6f
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2018
---
# <a name="best-practices-for-systemnet-classes"></a>Osvědčené postupy pro System.NET – třídy
Následující doporučení vám pomůže používat třídy součástí <xref:System.Net> využívají doporučené:  
  
-   Osvědčené postupy zabezpečení TLS (Transport Layer), najdete v části [zabezpečení TLS (Transport Layer) osvědčené postupy v rozhraní .NET Framework](tls.md).

-   Použití <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> kdykoli je to možné místo přetypování typu do odvozené třídy. Aplikace, které používají **WebRequest** a **WebResponse** můžete využít výhod nové protokoly Internetu bez nutnosti změny rozsáhlé kódu.  
  
-   Při vytváření aplikací ASP.NET, které běží na serveru pomocí **System.Net** třídy, je často lepší, z hlediska výkonu použít asynchronní metody pro <xref:System.Net.WebRequest.GetResponse%2A> a <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Počet otevřených připojení k internetového zdroji může mít významný dopad na výkon sítě a propustnosti. **System.Net** používá dvě připojení na aplikaci na hostitele ve výchozím nastavení. Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnost <xref:System.Net.ServicePoint> pro aplikaci můžete tento počet zvýšit pro konkrétního hostitele. Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnost může prodloužit toto výchozí nastavení pro všechny hostitele.  
  
-   Při zápisu úrovni soketu protokoly, zkuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je to možné místo přímo na zápis <xref:System.Net.Sockets.Socket>. Tyto dva klientské třídy zapouzdřovat vytvoření TCP a UDP soketů aniž by bylo potřeba zpracovávají údaje o připojení.  
  
-   Při přístupu k webům, které vyžadují přihlašovací údaje, použijte <xref:System.Net.CredentialCache> třídy za účelem vytvoření mezipaměti přihlašovací údaje místo zadávání je s každou žádostí. **CredentialCache** třída vyhledá mezipaměti najít odpovídající přihlašovací údaje k dispozici s žádostí, můžete kerberosu zodpovědnosti při vytváření a prezentování přihlašovací údaje založené na adresu URL.  
  
## <a name="see-also"></a>Viz také  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)
