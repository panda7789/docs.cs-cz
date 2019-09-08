---
title: Zmírnění Protokoly TLS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e98b447028ef9fa96233a71133aa82184d83cec8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779165"
---
# <a name="mitigation-tls-protocols"></a>Zmírnění Protokoly TLS
Počínaje .NET Framework 4,6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> mohou třídy a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> používat jeden z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1,2. Protokol SSL 3.0 a šifra šifry nejsou podporované.  
  
## <a name="impact"></a>Dopad  
 Tato změna má vliv na:  
  
- Libovolná aplikace, která používá protokol SSL ke komunikaci se serverem HTTPS nebo serverem soketu pomocí některého z následujících typů <xref:System.Net.Http.HttpClient>: <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, a <xref:System.Net.Security.SslStream>.  
  
- Všechny aplikace na straně serveru, které nelze upgradovat, aby podporovaly protokol TLS 1.0, TLS 1.1 nebo TLS 1,2..  
  
## <a name="mitigation"></a>Zmírnění  
 Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1,2. Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, <xref:System.AppContext> můžete tuto funkci použít k odhlášení z těchto funkcí jedním ze dvou způsobů:  
  
- Prostřednictvím kódu programu, který je podobný následujícímu:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Vzhledem k tomu, že se objektinicializujepouzejednou,definovánítěchtonastaveníkompatibilitymusíbýtprvnívěc,kterouaplikacedělá.<xref:System.Net.ServicePointManager>  
  
- Přidáním následujícího řádku do [ \<části > modulu runtime](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Upozorňujeme však, že nedoporučujeme výchozí chování, protože aplikace snižuje zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6.md)
