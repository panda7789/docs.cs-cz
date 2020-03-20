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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048897"
---
# <a name="best-practices-for-systemnet-classes"></a>Osvědčené postupy pro třídy System.Net
Následující doporučení vám pomohou použít třídy obsažené v <xref:System.Net> jejich nejlepší výhodě:  
  
- Doporučené postupy zabezpečení transportní vrstvy (TLS) naleznete v [doporučených postupech zabezpečení transportní vrstvy (TLS) pomocí rozhraní .NET Framework](tls.md).

- Použití <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> a kdykoli je to možné místo typu odlévání do tříd potomků. Aplikace, které používají **WebRequest** a **WebResponse** můžete využít nové internetové protokoly bez nutnosti rozsáhlé změny kódu.  
  
- Při psaní ASP.NET aplikací, které běží na serveru pomocí **tříd System.Net,** je často lepší, z hlediska <xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebResponse.GetResponseStream%2A>výkonu, používat asynchronní metody pro a .  
  
- Počet připojení otevřených k prostředku Sítě Internet může mít významný dopad na výkon sítě a propustnost. **System.Net** ve výchozím nastavení používá dvě připojení na aplikaci na hostitele. Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnosti <xref:System.Net.ServicePoint> pro vaši aplikaci může zvýšit toto číslo pro konkrétního hostitele. Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnosti může zvýšit toto výchozí nastavení pro všechny hostitele.  
  
- Při psaní protokolů na úrovni <xref:System.Net.Sockets.TcpClient> soketu zkuste použít <xref:System.Net.Sockets.UdpClient> nebo <xref:System.Net.Sockets.Socket>kdykoli je to možné namísto zápisu přímo do . Tyto dvě třídy klienta zapouzdřují vytvoření soketů TCP a UDP bez nutnosti zpracování podrobností o připojení.  
  
- Při přístupu k webům, <xref:System.Net.CredentialCache> které vyžadují pověření, použijte třídu k vytvoření mezipaměti pověření, nikoli k jejich poskytování s každým požadavkem. Třída **CredentialCache** prohledá mezipaměť a vyhledá příslušné přihlašovací údaje, které bude prezentovat s požadavkem, a zmírní odpovědnost za vytváření a prezentaci přihlašovacích údajů na základě adresy URL.  
  
## <a name="see-also"></a>Viz také

- [Síťové programování v rozhraní .NET Framework](index.md)
