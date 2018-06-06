---
title: Vazby poskytované systémem
description: Další informace o všech vazby poskytované systémem Windows Communication Foundation (WCF).
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 6730238a73b41faa4409fdfc75af1de36f31d13e
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805643"
---
# <a name="system-provided-bindings"></a>Vazby poskytované systémem

Vazby zadejte komunikační mechanizmus použít při komunikaci se koncový bod a určují, jak se připojit k koncový bod. Vazba obsahuje následující prvky:

- V zásobníku protokolů určuje zabezpečení, spolehlivost a kontext toku nastavení pro zprávy, které se odesílají do koncového bodu.

- Přenos určuje základní přenosový protokol mají použít při odesílání zprávy do koncového bodu, například TCP nebo HTTP.

- Kódování Určuje kódování použité pro zprávy, které se odesílají do koncového bodu sítě. Například: text/XML, binární nebo zpráva přenosu optimalizace mechanismus (MTOM).

 Tento článek představuje všechny vazby poskytované systémem Windows Communication Foundation (WCF). Pokud žádná z těchto vazeb nesplňuje přesná kritéria pro vaši aplikaci, můžete vytvořit vlastní vazby. Další informace o vytváření vlastních vazeb najdete v tématu [vlastní vazby](./extending/custom-bindings.md).

 Vazbu zabezpečené a vzájemná spolupráce, který podporuje protokol WS-Federation umožňuje organizacím, které jsou ve federaci efektivní ověřování a autorizaci uživatelů.

> [!IMPORTANT]
> Vždy vyberte vazbu, která zahrnuje zabezpečení. Ve výchozím nastavení jsou všechny vazby s výjimkou [ \<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) element mít povoleno zabezpečení. Pokud nemáte vyberte vazbu zabezpečení nebo zakázat zabezpečení, je nutné chránit vaše data jiným způsobem, jako je například ukládání v centru zabezpečených dat nebo na izolovanou síť.

> [!IMPORTANT]
> Nikdy nepoužívejte duplexní kontrakty u vazeb, které nepodporují zabezpečení nebo které mají zabezpečení vypnutý, pokud je zabezpečení dat jiným způsobem.

Následující vazby dodávají spolu s WCF:

|Vazba|Konfigurační Element|Popis|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)|Vazba, který je vhodný pro komunikaci s WS – základní profil vyhovující webové služby, například webových služeb ASP.NET (ASMX) – na základě služby. Tato vazba používá protokol HTTP jako přenosu a text/XML jako výchozí kódování zprávy.|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|Zabezpečení a vzájemná spolupráce vazby, který je vhodný pro kontraktů služby duplexní režim.|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Zabezpečení a vzájemná spolupráce vazby, který je vhodný pro služby duplexní kontrakty nebo komunikaci prostřednictvím protokolu SOAP zprostředkovatelů.|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Zabezpečení a vzájemná spolupráce vazbu, podporuje protokol WS-Federation, který umožňuje organizacím, které jsou ve federaci efektivní ověřování a autorizaci uživatelů.|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding >](../configure-apps/file-schema/wcf/nethttpbinding.md)|Vazba určená pro použití protokolu HTTP nebo protokolu WebSocket služeb, která používá binárního kódování ve výchozím nastavení.|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding >](../configure-apps/file-schema/wcf/nethttpsbinding.md)|Zabezpečené vazby určené pro použití protokolu HTTP nebo protokolu WebSocket služeb, která používá binárního kódování ve výchozím nastavení.|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../configure-apps/file-schema/wcf/nettcpbinding.md)|Zabezpečení a optimalizované vazbu vhodný pro komunikaci mezi počítači mezi aplikací služby WCF.|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<– netNamedPipeBinding >](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Bezpečné, spolehlivé a optimalizované vazby, který je vhodný pro-počítače komunikace mezi aplikací služby WCF.|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<– netMsmqBinding >](../configure-apps/file-schema/wcf/netmsmqbinding.md)|Vazba zařazených do fronty, který je vhodný pro komunikaci mezi počítači mezi aplikací služby WCF.|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Vazba, která umožňuje zabezpečenou, více komunikace počítače.|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding >](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Vazba, který je vhodný pro komunikaci mezi počítači mezi aplikace WCF a stávající zprávy služby Řízení front aplikace.|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<Vazba basicHttpContextBinding >](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Vhodné pro komunikaci s webovými službami profilu WS-Basic vyhovující vazbu, která umožňuje soubory cookie protokolu HTTP, který se použije pro kontext výměny.|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Zabezpečení a optimalizované vazbu vhodný pro komunikaci mezi počítači mezi aplikací služby WCF, který umožňuje hlavičky SOAP pro kontext výměny.|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../configure-apps/file-schema/wcf/webhttpbinding.md)|Vazba použitá ke konfiguraci koncových bodů WCF webové služby, které jsou přístupné přes požadavky HTTP místo protokolu SOAP zprávy.|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Zabezpečení a vzájemná spolupráce vazbu vhodný pro kontraktů služby duplexní režim umožňující hlavičky SOAP pro kontext výměny.|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding >](../configure-apps/file-schema/wcf/udpbinding.md)|Vazba pro odesílání shluku jednoduché zpráv velký počet klientů najednou.|

 V následující tabulce jsou uvedené funkce jednotlivých vazby poskytované systémem. Vazby se nacházejí ve sloupcích tabulky; funkce jsou uvedené na řádky a popsané v druhé tabulce. Následující tabulka poskytuje klíč pro zkratky vazby použít. Vyberte vazbu, určete, který sloupec splňuje všechny funkce řádků, které potřebujete.

|Vazba|Interoperabilita|Zabezpečení (výchozí)|Relace<br />(Výchozí)|Transakce|Duplex|Kódování (výchozí)|streamování<br />(Výchozí)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(None), přenos zpráv, ve smíšeném|(Žádný)|(Žádný)|není k dispozici|Text, (MTOM)|Ano<br />(vyrovnávací paměti).|
|<xref:System.ServiceModel.WSHttpBinding>|WS|Ve smíšeném přenosu (zprávy)|(None), spolehlivé relace, relace zabezpečení|Ano (none),|není k dispozici|(Text), MTOM|Ne|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Zprávy), None|(Spolehlivé relace), relace zabezpečení|Ano (none),|Ano|(Text), MTOM|Ne|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Zprávy), ve smíšeném, None|(None), spolehlivé relace, relace zabezpečení|Ano (none),|Ne|(Text), MTOM|Ne|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(None), přenosu, zprávu, TransportWithMessageCredential, TransportCredentialOnly|Viz poznámka níže|Žádné|Viz poznámka níže|(Binární), Text, MTOM|Ano (uložená do vyrovnávací paměti)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Přenos), TransportWithMessageCredential|Viz poznámka níže|Žádné|Viz poznámka níže|(Binární), Text, MTOM|Ano<br />(vyrovnávací paměti).|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Přenos), ve smíšeném zpráva, None,|(Přenos), spolehlivé relace, relace zabezpečení|Ano (none),|Ano|binární|Ano<br />(vyrovnávací paměti).|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Přenos), None|Žádný (přenos)|Ano (none),|Ano|binární|Ano<br />(vyrovnávací paměti).|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Zpráva, (přenos), None|(None), přenosu|Žádný (Ano)|Ne|binární|Ne|
|<xref:System.ServiceModel.NetPeerTcpBinding>|sdílené|(Přenos)|(Žádný)|(Žádný)|Ano||Ne|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Přenos)|(Žádný)|Žádný (Ano)|není k dispozici|není k dispozici|Ne|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(None), přenos zpráv, ve smíšeném|(Žádný)|(Žádný)|není k dispozici|Text, (MTOM)|Ano<br />(vyrovnávací paměti).|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Přenos), ve smíšeném zpráva, None,|(Přenos), spolehlivé relace, relace zabezpečení|Ano (none),|Ano|binární|Ano<br />(vyrovnávací paměti).|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Ve smíšeném přenosu (zprávy)|(None), spolehlivé relace, relace zabezpečení|Ano (none),|není k dispozici|Text, (MTOM)|Ne|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **Poznámka:** interoperabilita dosáhnout implementací standardní specifikace protokolu SOAP. přes UDP, která implementuje tuto vazbu.|.NET|(Žádný)|(Žádný)|(Žádný)|není k dispozici|(Text)|Ne|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> používá binární kódování ve výchozím nastavení je vazbu pro využívání služeb HTTP nebo protokolu WebSocket. <xref:System.ServiceModel.NetHttpBinding> zjistí, zda se používá s kontraktu požadavku a odpovědi nebo duplexního kontraktu a změní své chování tak, aby odpovídaly; využívá protokol HTTP pro požadavek odpověď a WebSockets pro duplexní režim. Toto chování lze přepsat pomocí <xref:System.ServiceModel.Channels.WebSocketTransportUsage> vazby nastavení: WhenDuplex - Toto je výchozí hodnota a chová, jak je popsáno výše. Nikdy – to zabraňuje objekty WebSockets. Pokus o použití duplexního kontraktu s výsledkem nastavení výjimku. Vždy - vynutí objekty WebSockets použije i pro kontraktů požadavek odpověď. NetHttpBinding podporuje spolehlivé relace v HTTP režimu i režimu protokolu WebSocket. V protokolu WebSocket relace režimu jsou poskytovány přenosu.

 Následující tabulka vysvětluje funkcí uvedených v předchozí tabulce.

|Funkce|Popis|
|-------------|-----------------|
|Typ interoperability|Název protokolu nebo technologii, se kterým zajišťuje vazby vzájemná spolupráce.|
|Zabezpečení|Určuje, jak jsou zabezpečená kanál:<br />-None: Není zabezpečené zprávu protokolu SOAP a klient není ověřen.<br />-Přenos: V přenosové vrstvě jsou splněné požadavky na zabezpečení.<br />-Zpráva: Ve vrstvě zprávy jsou splněny požadavky na zabezpečení.<br />-Ve smíšeném: Deklarace identity se přenášejí ve zprávě; Přenosová vrstva jsou splněny požadavky integrity a důvěrnosti.|
|Relace|Určuje, jestli tato vazba podporuje kontrakty relace.|
|Transakce|Určuje, zda je povoleno transakce.|
|Duplex|Určuje, zda jsou podporovány duplexní kontrakty. Všimněte si, že tato funkce vyžaduje podporu pro relace vazba.|
|Kódování|Určuje přenosový formát zprávy. Povolené hodnoty:<br />-Text: pro příklad UTF-8.<br />-Binární<br />-Zpráva přenosu optimalizace mechanismus (MTOM): Metodu pro efektivní kódování binární elementů XML v rámci obálky protokolu SOAP.|
|streamování|Určuje, zda streamování je podporováno pro příchozí a odchozí zprávy. Použití `TransferMode` vlastnost vazby k nastavení hodnoty. Povolené hodnoty:<br />- <xref:System.ServiceModel.TransferMode.Buffered>: Zprávy požadavku a odpovědi jsou obě do vyrovnávací paměti.<br />- <xref:System.ServiceModel.TransferMode.Streamed>Je streamování: zprávy požadavku a odpovědi.<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: Je streamování zprávu požadavku a zprávu odpovědi do vyrovnávací paměti.<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: Zprávu požadavku do vyrovnávací paměti a je streamování zprávu odpovědi.|

## <a name="see-also"></a>Viz také:

[Přehled vytváření koncových bodů](endpoint-creation-overview.md)  
[Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)  
[Základní programování WCF](basic-wcf-programming.md)  
