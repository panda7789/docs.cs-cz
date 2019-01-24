---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abfbea052072f0b90c9d018b520b67878d235701
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506807"
---
# <a name="mitigation-tls-protocols"></a>Omezení rizik: Protokoly TLS
Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy mohou používat jednu z těchto tří protokolů: Protokol TLS 1.0, Tls1.1 nebo Tls 1.2. SSL3.0 protokolu a šifer RC4 nejsou podporovány.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní:  
  
-   Jakékoli aplikaci, která používá protokol SSL na serveru HTTPS nebo server websocket pomocí kteréhokoli z následujících typů: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, a <xref:System.Net.Security.SslStream>.  
  
-   Libovolné aplikace na straně serveru, který nelze upgradovat pro podporu protokolu Tls 1.2, protokol TLS 1.0 nebo Tls1.1...  
  
## <a name="mitigation"></a>Zmírnění  
 Doporučené omezení rizik je upgrade aplikace straně serveru pro protokol TLS 1.0, Tls1.1 nebo Tls 1.2. Pokud to není proveditelné, nebo pokud jsou přerušená, klientské aplikace <xref:System.AppContext> třídy lze tuto funkci v některém ze dvou způsobů:  
  
-   Programově pomocí fragmentu kódu, jako je následující:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Vzhledem k tomu, <xref:System.Net.ServicePointManager> objekt je inicializován pouze jednou, definuje tato nastavení kompatibility musí být první věc, kterou aplikace dělá.  
  
-   Přidejte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Všimněte si však, že přestanete používat výchozí chování se nedoporučuje, protože je méně zabezpečené aplikace.  
  
## <a name="see-also"></a>Viz také:
- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
