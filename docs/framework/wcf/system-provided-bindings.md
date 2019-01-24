---
title: vazby poskytované systémem
description: Přečtěte si o všech vazeb poskytovaných systémem Windows Communication Foundation (WCF).
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 3c6c6b628d208aede8c547dcfa66fc189a26ae01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569599"
---
# <a name="system-provided-bindings"></a>vazby poskytované systémem

Vazby zadejte komunikační mechanizmus použít při komunikaci se koncový bod a určují, jak se připojit do koncového bodu. Vazba obsahuje následující prvky:

- Zásobník protokolu Určuje zabezpečení, spolehlivost a nastavení toku kontext pro zprávy, které se odesílají do koncového bodu.

- Určuje přenos podkladový přenosový protokol pro použití při odesílání zpráv do koncových bodů, například TCP nebo HTTP.

- Kódování určuje přenosu kódování použité pro zprávy odeslané do koncového bodu. Například text/XML, binární soubor nebo zpráv přenosu optimalizace mechanismus (MTOM).

 Tento článek představuje všechny vazby poskytované systémem Windows Communication Foundation (WCF). Pokud žádná z těchto vazeb nesplňuje přesné kritéria pro zařazení aplikace, můžete vytvořit vlastní vazby. Další informace o vytváření vlastních vazeb naleznete v tématu [vlastních vazeb](./extending/custom-bindings.md).

 Zabezpečená a interoperabilní vazbu, která podporuje protokol WS-Federation umožňuje organizacím, které jsou ve federaci efektivně ověřovat a autorizovat uživatele.

> [!IMPORTANT]
> Vždy vyberte vazbu, která zahrnuje zabezpečení. Ve výchozím nastavení všechny vazby s výjimkou [ \<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) element mít povoleno zabezpečení. Pokud nemáte zabezpečené vazby nebo zakázání zabezpečení, je potřeba chránit vaše data jiným způsobem, jako je ukládání v zabezpečené datovém centru nebo v izolované síti.

> [!IMPORTANT]
> Nikdy nepoužívejte duplexní kontrakty s vazbami, které nepodporují zabezpečení nebo obsahujících zabezpečení zakázáno, pokud je zabezpečení dat jiným způsobem.

Následující příjemce vazby s použitím technologie WCF:

|Vazba|Element konfigurace|Popis|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)|Vazby, který je vhodný pro komunikaci s profilu WS Basic-splňující podmínky webové služby, například webových služeb ASP.NET (ASMX) – na základě služeb. Tato vazba používá protokol HTTP jako přenosu a text/XML jako výchozí kódování zprávy.|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|Zabezpečená a interoperabilní vazbu, která je vhodné pro neduplexní servisní smlouvy.|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Zabezpečená a interoperabilní vazbu, která je vhodná pro duplexní kontrakty služeb nebo komunikace prostřednictvím zprostředkovatelů SOAP.|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Zabezpečená a interoperabilní vazba, která podporuje protokol WS-Federation, který umožňuje organizacím, které jsou ve federaci efektivně ověřovat a autorizovat uživatele.|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding>](../configure-apps/file-schema/wcf/nethttpbinding.md)|Vazba určená pro použití protokolu HTTP nebo objektu websocket na straně služby, která používá binární kódování ve výchozím nastavení.|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding>](../configure-apps/file-schema/wcf/nethttpsbinding.md)|Zabezpečené vazby pro používání protokolu HTTP nebo objektu websocket na straně služby, která používá binární kódování ve výchozím nastavení.|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|Zabezpečené a optimalizované vazby vhodné pro komunikaci mezi počítači mezi aplikací služby WCF.|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Zabezpečená, spolehlivá a optimalizovaná vazby, který je vhodný pro komunikaci na počítači mezi aplikací služby WCF.|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../configure-apps/file-schema/wcf/netmsmqbinding.md)|Vazbu s frontou, který je vhodný pro komunikaci mezi počítači mezi aplikací služby WCF.|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Vazbu, která umožňuje zabezpečenou, více počítačů komunikace.|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Vazba, která je vhodná pro komunikaci mezi počítači mezi aplikací WCF a existující front aplikací.|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding>](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Vhodný pro komunikaci s webovými službami profilu WS-Basic vyhovující vazbu, která umožňuje soubory cookie protokolu HTTP, který se má použít pro kontext výměny.|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding>](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Zabezpečené a optimalizované vazba vhodný pro komunikaci mezi počítači mezi aplikací služby WCF, která umožňuje hlavičky SOAP pro kontext výměny.|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../configure-apps/file-schema/wcf/webhttpbinding.md)|Vazba použitá ke konfiguraci koncových bodů webových služeb WCF, které jsou přístupné přes požadavky HTTP namísto zpráv SOAP.|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding>](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Zabezpečená a interoperabilní vazby vhodné pro neduplexní servisní smlouvy, která umožňuje hlavičky SOAP pro kontext výměny.|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding>](../configure-apps/file-schema/wcf/udpbinding.md)|Vazby pro použití při odesílání zřízeno jednoduché zpráv na velké množství klientů současně.|

 Následující tabulka uvádí funkce všech vazeb poskytovaných systémem. Tyto vazby se nacházejí ve sloupcích tabulky; funkce jsou uvedené v řádcích, jsou popsané v druhé tabulce. Následující tabulka poskytuje klíč pro zkratky vazba používá. Vyberte vazbu, určete, který sloupec splňuje všechny funkce řádků, které potřebujete.

|Vazba|Interoperabilita|Zabezpečení (výchozí)|Relace<br />(Výchozí)|Transakce|Duplex|Kódování (výchozí)|Streamování<br />(Výchozí)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Žádné), přenos zpráv, smíšené|(Žádné)|(Žádné)|není k dispozici|Text, (MTOM)|Ano<br />(ukládány do vyrovnávací paměti)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|Smíšené přenosu (zprávy)|(Žádné), stabilní relace, relace zabezpečení|Ano (žádné)|není k dispozici|(Text), MTOM|Ne|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Zpráva), žádná|(Stabilní relace), relace zabezpečení|Ano (žádné)|Ano|(Text), MTOM|Ne|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Zpráva), ve smíšeném, None|(Žádné), stabilní relace, relace zabezpečení|Ano (žádné)|Ne|(Text), MTOM|Ne|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Žádné), přenosu, zprávy, TransportWithMessageCredential, TransportCredentialOnly|Viz poznámka níže|Žádná|Viz poznámka níže|(Binary), Text, MTOM|Ano (uložená do vyrovnávací paměti)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Přenos), TransportWithMessageCredential|Viz poznámka níže|Žádná|Viz poznámka níže|(Binary), Text, MTOM|Ano<br />(ukládány do vyrovnávací paměti)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Přenos), zpráv, None, smíšené|(Přenos), stabilní relace, relace zabezpečení|Ano (žádné)|Ano|binární|Ano<br />(ukládány do vyrovnávací paměti)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Přenos), žádná|Žádný (přenos)|Ano (žádné)|Ano|binární|Ano<br />(ukládány do vyrovnávací paměti)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Zpráva (přenos), žádná|(Žádné), přenosu|Žádný (Ano)|Ne|binární|Ne|
|<xref:System.ServiceModel.NetPeerTcpBinding>|Peer|(Přenos)|(Žádné)|(Žádné)|Ano||Ne|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Přenos)|(Žádné)|Žádný (Ano)|není k dispozici|není k dispozici|Ne|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(Žádné), přenos zpráv, smíšené|(Žádné)|(Žádné)|není k dispozici|Text, (MTOM)|Ano<br />(ukládány do vyrovnávací paměti)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Přenos), zpráv, None, smíšené|(Přenos), stabilní relace, relace zabezpečení|Ano (žádné)|Ano|binární|Ano<br />(ukládány do vyrovnávací paměti)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Smíšené přenosu (zprávy)|(Žádné), stabilní relace, relace zabezpečení|Ano (žádné)|není k dispozici|Text, (MTOM)|Ne|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **Poznámka:**  Vzájemná funkční spolupráce jde dosáhnout implementací standardní specifikace SOAP-over-UDP, který implementuje tuto vazbu.|.NET|(Žádné)|(Žádné)|(Žádné)|není k dispozici|(Text)|Ne|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> Vazba určená pro použití protokolu HTTP nebo objektu websocket na straně služby a používá binární kódování ve výchozím nastavení. <xref:System.ServiceModel.NetHttpBinding> zjistí, jestli se používá s kontraktů požadavek odpověď nebo duplexní kontrakt a změní své chování tak, aby odpovídaly; používá protokol HTTP pro žádost odpověď a protokoly Websocket pro duplexní režim. Toto chování lze přepsat pomocí <xref:System.ServiceModel.Channels.WebSocketTransportUsage> vazby nastavení: WhenDuplex – to je výchozí hodnota a chová se, jak je popsáno výše. Nikdy – to zabraňuje objekty Websocket. Pokus o použití duplexního kontraktu s výsledkem nastavení výjimku. Vždy – to přinutí WebSockets se použije i pro kontraktů požadavek odpověď. NetHttpBinding podporuje spolehlivé relace v režimu HTTP a WebSocket režimu. V objektu websocket na straně relace režimu jsou poskytovány přenos.

 Následující tabulka vysvětluje funkcí uvedených v předchozí tabulce.

|Funkce|Popis|
|-------------|-----------------|
|Vzájemná funkční spolupráce typu|Název protokolu nebo technologie, pomocí kterého se vazba zajistí vzájemná spolupráce grafického subsystému.|
|Zabezpečení|Určuje, jak je zabezpečený kanál:<br />-Žádný: Není zabezpečen zprávu protokolu SOAP a klient není ověřený.<br />-Přenos: V přenosové vrstvě jsou splněny požadavky na zabezpečení.<br />– Zprávy: Ve vrstvě zprávy jsou splněny požadavky na zabezpečení.<br />-Smíšené: Deklarace přenášejí v zprávy. integritu a důvěrnost požadavky splněny přenosové vrstvy.|
|Relace|Určuje, zda tato vazba podporuje kontrakty relací.|
|Transakce|Určuje, zda je povoleno transakce.|
|Duplex|Určuje, zda jsou podporovány duplexní kontrakty. Všimněte si, že tato funkce vyžaduje podporu pro relace ve vazbě.|
|Kódování|Určuje formát při přenosu zprávy. Povolené hodnoty:<br />-Text: například UTF-8.<br />-Binární<br />-Optimalizace mechanismus přenosu zprávu (MTOM): Metoda pro efektivní kódování binární XML elementů v rámci kontextové obálku protokolu SOAP.|
|Streamování|Určuje, zda datový proud je podporováno pro příchozí a odchozí zprávy. Použití `TransferMode` vlastnost pro vazbu k nastavení hodnoty. Povolené hodnoty:<br />- <xref:System.ServiceModel.TransferMode.Buffered>: Zprávy požadavků a odpovědí jsou obě ukládány do vyrovnávací paměti.<br />- <xref:System.ServiceModel.TransferMode.Streamed>: Je Streamovat zprávy požadavků a odpovědí.<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: Zprávy s požadavkem je streamování a zprávy s odpovědí do vyrovnávací paměti.<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: Zpráva požadavku do vyrovnávací paměti a Streamovat zprávy s odpovědí.|

## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Základní programování WCF](basic-wcf-programming.md)
