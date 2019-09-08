---
title: Vlastní vazby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: a4b3abfe9be25c9080a362eb4a6e4c7b070528f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797233"
---
# <a name="custom-bindings"></a>Vlastní vazby

Třídu můžete použít, <xref:System.ServiceModel.Channels.CustomBinding> když jedna z vazeb poskytnutých systémem nesplňuje požadavky vaší služby. Všechny vazby jsou zhotoveny z seřazené sady prvků vazby. Vlastní vazby mohou být sestaveny ze sady prvků vazby poskytovaných systémem nebo mohou zahrnovat uživatelsky definované vlastní prvky vazby. Můžete použít vlastní prvky vazby, například k povolení použití nových přenosů nebo kodérů na koncovém bodu služby. Pracovní příklady najdete v tématu [vlastní ukázky vazeb](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)). Další informace najdete v tématu [ \<CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md).

## <a name="construction-of-a-custom-binding"></a>Konstrukce vlastní vazby

Vlastní vazba je vytvořena pomocí <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktoru z kolekce prvků vazby, které jsou "skládané" v určitém pořadí:

- V horní části je volitelná <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> třída, která umožňuje přesměrovat transakce.

- Další je volitelná <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> třída, která poskytuje mechanismy pro relaci a řazení, jak je definováno ve specifikaci WS-ReliableMessaging. Relace může vzájemně přenášet zprostředkovatele SOAP a přenosu.

- Další je volitelná <xref:System.ServiceModel.Channels.SecurityBindingElement> třída, která poskytuje funkce zabezpečení, jako je například autorizace, ověřování, ochrana a důvěrnost.

- Další je volitelná <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> třída, která umožňuje obousměrnou duplexní komunikaci s transportním protokolem, který nativně nepodporuje duplexní komunikaci, jako je například http.

- Další je volitelná <xref:System.ServiceModel.Channels.OneWayBindingElement>třída, která poskytuje jednosměrnou komunikaci.

- Další je volitelný element vazby zabezpečení datového proudu, který může být jeden z následujících.

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Další je povinný element vazby kódování zprávy. Můžete použít svůj vlastní kodér zpráv nebo jednu ze tří vazeb kódování zpráv:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

V dolní části je požadovaný transportní prvek. Můžete použít vlastní přenos nebo jeden z následujících elementů transportních vazeb Windows Communication Foundation (WCF) poskytuje:

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

Následující tabulka shrnuje možnosti pro každou vrstvu.

|Vrstva|Možnosti|Požadováno|
|-----------|-------------|--------------|
|Transakce|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Ne|
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Ne|
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement>|Ne|
|Kódování|Text, binární, mechanizmus pro optimalizaci přenosu zpráv (MTOM), vlastní|Ano|
|Přepravu|TCP, HTTP, HTTPS, pojmenované kanály (označované také jako IPC), peer-to-peer (P2P), řízení front zpráv (označované také jako MSMQ), vlastní|Ano|

Kromě toho můžete definovat vlastní prvky vazby a vkládat je mezi kteroukoli z předchozích definovaných vrstev.

## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](../endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../using-bindings-to-configure-services-and-clients.md)
- [Vazby poskytované systémem](../system-provided-bindings.md)
- [Postupy: Přizpůsobení systémem poskytované vazby](how-to-customize-a-system-provided-binding.md)
- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
- [Vlastní vazba](../samples/custom-binding.md)
