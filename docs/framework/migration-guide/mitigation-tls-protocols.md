---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d37326d0278225146d217624508e7c7738375b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-tls-protocols"></a>Omezení rizik: Protokoly TLS
Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy mohou používat jednu z následujících tří protokolů: Tls1.0, Tls1.1 nebo Tls 1.2. Protokol SSL3.0 a šifrovací algoritmus RC4 nejsou podporovány.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivňuje:  
  
-   Jakékoli aplikaci, která používá protokol SSL, aby komunikoval s serveru HTTPS nebo server soketu pomocí kteréhokoli z následujících typů: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, a <xref:System.Net.Security.SslStream>.  
  
-   Jakékoli serverovou aplikaci, která nejde upgradovat na podporu Tls1.0, Tls1.1 nebo Tls 1.2...  
  
## <a name="mitigation"></a>Zmírnění  
 Doporučené omezení rizik se k upgradu aplikace na straně serveru Tls1.0, Tls1.1 nebo Tls 1.2. Pokud to není možné, nebo pokud klientských aplikací jsou poškozená, <xref:System.AppContext> třídu lze použít pro vyjádření výslovného nesouhlasu tuto funkci v některém ze dvou způsobů:  
  
-   Programově pomocí fragmentu kódu takto:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Protože <xref:System.Net.ServicePointManager> objekt je inicializovat pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace.  
  
-   Přidáním následující řádek [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Upozorňujeme však, že zrušení výchozí chování se nedoporučuje, protože způsobí, že aplikace méně bezpečné.  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
