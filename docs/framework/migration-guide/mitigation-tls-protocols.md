---
title: 'Omezení rizik: Protokoly TLS'
description: Přečtěte si o dopadu a zmírnění omezení pro změny protokolu TLS od .NET Framework 4,6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475356"
---
# <a name="mitigation-tls-protocols"></a>Omezení rizik: Protokoly TLS
Počínaje .NET Framework 4,6 mohou <xref:System.Net.ServicePointManager?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy a používat jeden z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1,2. Protokol SSL 3.0 a šifra šifry nejsou podporované.  
  
## <a name="impact"></a>Dopad  
 Tato změna má vliv na:  
  
- Libovolná aplikace, která používá protokol SSL ke komunikaci se serverem HTTPS nebo serverem soketu pomocí některého z následujících typů: <xref:System.Net.Http.HttpClient> , <xref:System.Net.HttpWebRequest> , <xref:System.Net.FtpWebRequest> , <xref:System.Net.Mail.SmtpClient> a <xref:System.Net.Security.SslStream> .  
  
- Všechny aplikace na straně serveru, které nelze upgradovat, aby podporovaly protokol TLS 1.0, TLS 1.1 nebo TLS 1,2..  
  
## <a name="mitigation"></a>Omezení rizik  
 Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1,2. Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, <xref:System.AppContext> můžete tuto funkci použít k odhlášení z těchto funkcí jedním ze dvou způsobů:  
  
- Prostřednictvím kódu programu, který je podobný následujícímu:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Vzhledem k tomu, že se <xref:System.Net.ServicePointManager> objekt inicializuje pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace dělá.  
  
- Přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Upozorňujeme však, že nedoporučujeme výchozí chování, protože aplikace snižuje zabezpečení.  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
