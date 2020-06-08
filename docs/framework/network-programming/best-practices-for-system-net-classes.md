---
title: Osvědčené postupy pro třídy System.Net
description: Pomocí těchto doporučení můžete použít třídy obsažené v System.Net k jejich nejlepší výhodě při .NET Framework programování.
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
ms.openlocfilehash: 583fa5e57c7c4d60252dddfd425596e7acad7c0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502675"
---
# <a name="best-practices-for-systemnet-classes"></a>Osvědčené postupy pro třídy System.Net
Následující doporučení vám pomůžou používat třídy obsažené v aplikaci <xref:System.Net> k jejich nejlepší výhodě:  
  
- Doporučené postupy pro TLS (Transport Layer Security) najdete v tématu [osvědčené postupy TLS (Transport Layer Security) s .NET Framework](tls.md).

- Používejte <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> kdykoli je to možné, namísto přetypování na odvozené třídy. Aplikace, které používají **WebRequest** a **WebResponse** , můžou využívat nové internetové protokoly, aniž by museli provádět rozsáhlé změny kódu.  
  
- Při psaní ASP.NET aplikací, které běží na serveru pomocí tříd **System.NET** , je často lepší, z hlediska výkonu, pro použití asynchronních metod pro <xref:System.Net.WebRequest.GetResponse%2A> a <xref:System.Net.WebResponse.GetResponseStream%2A> .  
  
- Počet připojení otevřených k internetovému prostředku může mít významný dopad na výkon a propustnost sítě. **System.NET** používá ve výchozím nastavení dvě připojení na každou aplikaci na hostitele. Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnosti v <xref:System.Net.ServicePoint> pro aplikaci může zvýšit toto číslo pro konkrétního hostitele. Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnosti může zvýšit tuto výchozí hodnotu pro všechny hostitele.  
  
- Při psaní protokolů na úrovni soketu se pokuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je to možné, místo psaní přímo do <xref:System.Net.Sockets.Socket> . Tyto dvě klientské třídy zapouzdřují vytváření soketů TCP a UDP bez nutnosti zpracovávat podrobnosti o připojení.  
  
- Při přístupu k lokalitám, které vyžadují přihlašovací údaje, použijte <xref:System.Net.CredentialCache> třídu k vytvoření mezipaměti přihlašovacích údajů místo jejich zadání se všemi požadavky. Třída **CredentialCache** vyhledá v mezipaměti příslušné přihlašovací údaje, které mají být k dispozici s požadavkem, a tím vám zbavuje vytváření a prezentování přihlašovacích údajů na základě adresy URL.  
  
## <a name="see-also"></a>Viz také:

- [Síťové programování v rozhraní .NET Framework](index.md)
