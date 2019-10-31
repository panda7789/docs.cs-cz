---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 2a2f95be92ec08185f627e862b0f62e40a1d764b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126138"
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

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6.md)
