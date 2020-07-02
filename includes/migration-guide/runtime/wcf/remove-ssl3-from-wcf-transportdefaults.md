---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621085"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Odebrání SSL3 z TransportDefaults WCF

#### <a name="details"></a>Podrobnosti

Pokud používáte NetTcp se zabezpečením přenosu a typem přihlašovacích údajů certifikátu, protokol SSL 3 už není výchozím protokolem používaným pro vyjednávání zabezpečeného připojení. Ve většině případů by nemělo dojít k žádným dopadům na stávající aplikace, protože protokol TLS 1,0 byl vždycky zahrnutý do seznamu protokolů pro NetTcp. Všichni existující klienti by měli být schopni vyjednat připojení pomocí aspoň TLS 1.0.

#### <a name="suggestion"></a>Návrh

Pokud se vyžaduje SSL3, použijte jeden z následujících konfiguračních mechanismů a přidejte SSL3 do seznamu sjednaných protokolů.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[ &lt; &gt; oddíl sslStreamSecurity v &lt; CustomBinding &gt; ] ~/docs/Framework/Configure-Apps/File-Schema/WCF/sslStreamSecurity.MD)</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
