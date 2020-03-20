---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457836"
---
# <a name="mitigation-tls-protocols"></a>Omezení rizik: Protokoly TLS
Počínaje rozhraním .NET Framework 4.6 mohou třídy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> používat jeden z následujících tří protokolů: Tls1.0, Tls1.1 nebo Tls 1.2. Protokol SSL3.0 a šifra RC4 nejsou podporovány.  
  
## <a name="impact"></a>Dopad  
 Tato změna má vliv na:  
  
- Libovolná aplikace, která používá protokol SSL k komunikaci se serverem <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest>HTTPS <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient>nebo soketovým serverem pomocí některého z následujících typů: , , , a <xref:System.Net.Security.SslStream>.  
  
- Jakákoli aplikace na straně serveru, kterou nelze upgradovat na podporu Tls1.0, Tls1.1 nebo Tls 1.2..  
  
## <a name="mitigation"></a>Omezení rizik  
 Doporučené zmírnění je upgrade aplikace na straně sever na Tls1.0, Tls1.1 nebo Tls 1.2. Pokud to není možné, nebo pokud klientské <xref:System.AppContext> aplikace jsou rozbité, třídy lze odhlásit z této funkce v jednom ze dvou způsobů:  
  
- Programově pomocí fragmentu kódu, jako je následující:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Vzhledem <xref:System.Net.ServicePointManager> k tomu, že objekt je inicializován pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace provede.  
  
- Přidáním následujícího řádku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Všimněte si však, že odhlášení z výchozí chování se nedoporučuje, protože aplikace méně zabezpečené.  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
