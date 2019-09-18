---
title: Osvědčené postupy pro třídy System.Net
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
ms.openlocfilehash: c7324dcbc27c95c7d799592700d46c195e7d952b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048897"
---
# <a name="best-practices-for-systemnet-classes"></a>Osvědčené postupy pro třídy System.Net
Následující doporučení vám pomůžou používat třídy obsažené v aplikaci <xref:System.Net> k jejich nejlepší výhodě:  
  
- Doporučené postupy pro TLS (Transport Layer Security) najdete v tématu [osvědčené postupy TLS (Transport Layer Security) s .NET Framework](tls.md).

- Používejte <xref:System.Net.WebRequest> a<xref:System.Net.WebResponse> kdykoli je to možné, namísto přetypování na odvozené třídy. Aplikace, které používají **WebRequest** a **WebResponse** , můžou využívat nové internetové protokoly, aniž by museli provádět rozsáhlé změny kódu.  
  
- Při psaní ASP.NET aplikací, které běží na serveru pomocí tříd **System.NET** , je často lepší, z hlediska výkonu, pro použití asynchronních metod pro <xref:System.Net.WebRequest.GetResponse%2A> a. <xref:System.Net.WebResponse.GetResponseStream%2A>  
  
- Počet připojení otevřených k internetovému prostředku může mít významný dopad na výkon a propustnost sítě. **System.NET** používá ve výchozím nastavení dvě připojení na každou aplikaci na hostitele. <xref:System.Net.ServicePoint.ConnectionLimit%2A> Nastavení vlastnosti<xref:System.Net.ServicePoint> v pro aplikaci může zvýšit toto číslo pro konkrétního hostitele. <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> Nastavení vlastnosti může zvýšit tuto výchozí hodnotu pro všechny hostitele.  
  
- Při psaní protokolů na úrovni soketu se pokuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je <xref:System.Net.Sockets.Socket>to možné, místo psaní přímo do. Tyto dvě klientské třídy zapouzdřují vytváření soketů TCP a UDP bez nutnosti zpracovávat podrobnosti o připojení.  
  
- Při přístupu k lokalitám, které vyžadují přihlašovací <xref:System.Net.CredentialCache> údaje, použijte třídu k vytvoření mezipaměti přihlašovacích údajů místo jejich zadání se všemi požadavky. Třída **CredentialCache** vyhledá v mezipaměti příslušné přihlašovací údaje, které mají být k dispozici s požadavkem, a tím vám zbavuje vytváření a prezentování přihlašovacích údajů na základě adresy URL.  
  
## <a name="see-also"></a>Viz také:

- [Síťové programování v rozhraní .NET Framework](index.md)
