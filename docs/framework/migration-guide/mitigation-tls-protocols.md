---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457836"
---
# <a name="mitigation-tls-protocols"></a>Omezení rizik: Protokoly TLS
Počínaje .NET Framework 4,6 třídy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> mohou používat jeden z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1,2. Protokol SSL 3.0 a šifra šifry nejsou podporované.  
  
## <a name="impact"></a>Dopad  
 Tato změna má vliv na:  
  
- Libovolná aplikace, která používá protokol SSL ke komunikaci se serverem HTTPS nebo serverem soketu pomocí některého z následujících typů: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>a <xref:System.Net.Security.SslStream>.  
  
- Všechny aplikace na straně serveru, které nelze upgradovat, aby podporovaly protokol TLS 1.0, TLS 1.1 nebo TLS 1,2..  
  
## <a name="mitigation"></a>Zmírnění  
 Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1,2. Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, lze třídu <xref:System.AppContext> použít k odhlášení z této funkce jedním ze dvou způsobů:  
  
- Prostřednictvím kódu programu, který je podobný následujícímu:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Vzhledem k tomu, že se objekt <xref:System.Net.ServicePointManager> inicializuje pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace dělá.  
  
- Přidáním následujícího řádku do oddílu [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Upozorňujeme však, že nedoporučujeme výchozí chování, protože aplikace snižuje zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
