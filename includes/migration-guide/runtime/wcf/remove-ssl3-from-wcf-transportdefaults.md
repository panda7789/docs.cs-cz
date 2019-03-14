---
ms.openlocfilehash: 37d771305bb0a4a38eeac9713e8667d158962174
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788826"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Odebrání Ssl3 WCF TransportDefaults

|   |   |
|---|---|
|Podrobnosti|Při použití NetTcp se zabezpečením přenosu a přihlašovacích údajů typu certifikátu, protokol SSL 3 je již výchozí protokol použitý pro vyjednávání zabezpečeného připojení. Ve většině případů by měl existovat žádný vliv na stávající aplikace jako TLS 1.0 vždy byla zahrnuta do seznamu protokolů pro NetTcp. Všichni existující klienti měli být schopni vyjednat připojení pomocí na nejnižší protokol TLS 1.0.|
|Doporučení|Ssl3 je potřeba, použijte jednu z následujících mechanismů konfigurace Ssl3 přidat do seznamu vyjednávaný protokolů.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[\<přenos > z \<netTcpBinding >](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; část &lt;customBinding&gt;](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

