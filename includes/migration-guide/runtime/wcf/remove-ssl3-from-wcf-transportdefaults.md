---
ms.openlocfilehash: d75eff2d2a43ab4488577014ec43a9826b2b2924
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237820"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Odebrání ssl3 z wcf transportdefaults

|   |   |
|---|---|
|Podrobnosti|Při použití protokolu NetTcp se zabezpečením přenosu a typem pověření certifikátu již protokol SSL 3 není výchozím protokolem používaným pro vyjednávání zabezpečeného připojení. Ve většině případů by nemělo být žádný dopad na existující aplikace jako TLS 1.0 byla vždy zahrnuta do seznamu protokolů pro NetTcp. Všichni stávající klienti by měli být schopni vyjednat připojení pomocí alespoň TLS1.0.|
|Návrh|Pokud je požadováno Ssl3, použijte jeden z následujících konfiguračních mechanismů přidat Ssl3 do seznamu vyjednaných protokolů.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; &lt;sekce&gt;customBinding ]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
