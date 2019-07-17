---
ms.openlocfilehash: d75eff2d2a43ab4488577014ec43a9826b2b2924
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237820"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Odebrání Ssl3 WCF TransportDefaults

|   |   |
|---|---|
|Podrobnosti|Při použití NetTcp se zabezpečením přenosu a přihlašovacích údajů typu certifikátu, protokol SSL 3 je již výchozí protokol použitý pro vyjednávání zabezpečeného připojení. Ve většině případů by měl existovat žádný vliv na stávající aplikace jako TLS 1.0 vždy byla zahrnuta do seznamu protokolů pro NetTcp. Všichni existující klienti měli být schopni vyjednat připojení pomocí na nejnižší protokol TLS 1.0.|
|Doporučení|Ssl3 je potřeba, použijte jednu z následujících mechanismů konfigurace Ssl3 přidat do seznamu vyjednávaný protokolů.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; část &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Scope|Edge|
|Version|4.6.2|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
