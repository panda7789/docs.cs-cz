---
title: Vazby poskytované systémem
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
caps.latest.revision: 60
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ccdab56a90f4114836dd9f0a56cc495657ee9c8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="system-provided-bindings"></a>Vazby poskytované systémem
Vazby zadejte komunikační mechanizmus použít při komunikaci se koncový bod a určují, jak se připojit k koncový bod. Vazba obsahuje následující prvky:  
  
-   V zásobníku protokolů určuje zabezpečení, spolehlivost a kontext toku nastavení pro zprávy, které se odesílají do koncového bodu.  
  
-   Přenos určuje základní přenosový protokol mají použít při odesílání zprávy do koncového bodu, například TCP nebo HTTP.  
  
-   Kódování určuje přenosová kódování použité pro zprávy, které se odesílají do koncového bodu, například, text/XML, binární nebo zpráva přenosu optimalizace mechanismus (MTOM).  
  
 Toto téma představuje všechny poskytované systémem [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] vazby. Pokud žádná z nich splňuje přesný kritéria pro vaši aplikaci, můžete vytvořit vlastní vazby. Další informace o vytváření vlastních vazeb najdete v tématu [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Vazbu zabezpečené a vzájemná spolupráce, který podporuje protokol WS-Federation umožňuje organizacím, které jsou ve federaci efektivní ověřování a autorizaci uživatelů.  
  
> [!IMPORTANT]
>  Vždy vyberte vazbu, která zahrnuje zabezpečení. Ve výchozím nastavení jsou všechny vazby s výjimkou [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element mít povoleno zabezpečení. Pokud nemáte vyberte vazbu zabezpečení nebo zakázat zabezpečení, je nutné chránit vaše data jiným způsobem, jako je například ukládání v centru zabezpečených dat nebo na izolovanou síť.  
  
> [!IMPORTANT]
>  Nikdy nepoužívejte duplexní kontrakty u vazeb, které nepodporují zabezpečení nebo které mají zabezpečení vypnutý, pokud je zabezpečení dat jiným způsobem.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 Následující vazby dodávají spolu s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
|Vazba|Konfigurační Element|Popis|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Vazba, který je vhodný pro komunikaci s profilu WS-Basic vyhovující webové služby, například webových služeb ASP.NET (ASMX) – na základě služby. Tato vazba používá protokol HTTP jako přenosu a text/XML jako výchozí kódování zprávy.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Zabezpečení a vzájemná spolupráce vazby, který je vhodný pro kontraktů služby duplexní režim.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Zabezpečení a vzájemná spolupráce vazby, který je vhodný pro služby duplexní kontrakty nebo komunikaci prostřednictvím protokolu SOAP zprostředkovatelů.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Zabezpečení a vzájemná spolupráce vazbu, podporuje protokol WS-Federation, který umožňuje organizacím, které jsou ve federaci efektivní ověřování a autorizaci uživatelů.|  
|<xref:System.ServiceModel.NetHttpBinding>|\<netHttpBinding >|Vazba určená pro použití protokolu HTTP nebo protokolu WebSocket služeb, která používá binárního kódování ve výchozím nastavení.|  
|<xref:System.ServiceModel.NetHttpsBinding>|\<netHttpsBinding >|Zabezpečené vazby určené pro použití protokolu HTTP nebo protokolu WebSocket služeb, která používá binárního kódování ve výchozím nastavení.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Zabezpečení a optimalizované vazbu vhodný pro komunikaci mezi počítači mezi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<– netNamedPipeBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Bezpečné, spolehlivé a optimalizované vazby, který je vhodný pro-počítače komunikace mezi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<– netMsmqBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Vazbu zařazených do fronty, který je vhodný pro komunikaci mezi počítači mezi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Vazba, která umožňuje zabezpečenou, více komunikace počítače.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding >](../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Vazba, který je vhodný pro komunikaci mezi počítači mezi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace a stávající aplikace služby Řízení front zpráv.|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<Vazba basicHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Vazbu, která je vhodná pro komunikaci s vyhovující profilu WS – základní webové služby umožňující soubory cookie protokolu HTTP, který se použije pro kontext výměny.|  
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Zabezpečení a optimalizované vazbu vhodný pro komunikaci mezi počítači mezi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace, které umožňuje hlavičky SOAP pro kontext výměny.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Vazba použitá ke konfiguraci koncových bodů pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] webové služby, které se zveřejňují přes požadavky HTTP místo protokolu SOAP zprávy.|  
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Zabezpečený a |<xref:System.ServiceModel.UdpBinding>|\<udpBinding >|Vazba pro odesílání shluku jednoduché zpráv velký počet klientů najednou.|  
  
 V následující tabulce jsou uvedené funkce jednotlivých vazby poskytované systémem. Vazby se nacházejí ve sloupcích tabulky; funkce jsou uvedené na řádky a popsané v druhé tabulce. Následující tabulka poskytuje klíč pro zkratky vazby použít. Vyberte vazbu, určete, který sloupec splňuje všechny funkce řádků, které potřebujete.  
  
|Vazba|Interoperabilita|Zabezpečení (výchozí)|Relace<br /><br /> (Výchozí)|Transakce|Duplex|Kódování (výchozí)|streamování<br /><br /> (Výchozí)|  
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(None), přenos zpráv, ve smíšeném|(Žádný)|(Žádný)|není k dispozici|Text, (MTOM)|Ano<br /><br /> (vyrovnávací paměti).|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Ve smíšeném přenosu (zprávy)|(None), spolehlivé relace, relace zabezpečení|Ano (none),|není k dispozici|(Text), MTOM|Ne|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Zprávy), None|(Spolehlivé relace), relace zabezpečení|Ano (none),|Ano|(Text), MTOM|Ne|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Zprávy), ve smíšeném, None|(None), spolehlivé relace, relace zabezpečení|Ano (none),|Ne|(Text), MTOM|Ne|  
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(None), přenosu, zprávu, TransportWithMessageCredential, TransportCredentialOnly|Viz poznámka níže|Žádné|Viz poznámka níže|(Binární), Text, MTOM|Ano (uložená do vyrovnávací paměti)|  
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Přenos), TransportWithMessageCredential|Viz poznámka níže|Žádné|Viz poznámka níže|(Binární), Text, MTOM|Ano (uložená do vyrovnávací paměti)|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Přenos), ve smíšeném zpráva, None,|(Přenos), spolehlivé relace, relace zabezpečení|Ano (none),|Ano|binární|Ano<br /><br /> (vyrovnávací paměti).|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Přenos), None|Žádný (přenos)|Ano (none),|Ano|binární|Ano<br /><br /> (vyrovnávací paměti).|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Zpráva, (přenos), None|(None), přenosu|Žádný (Ano)|Ne|binární|Ne|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|sdílené|(Přenos)|(Žádný)|(Žádný)|Ano||Ne|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Přenos)|(Žádný)|Žádný (Ano)|není k dispozici|není k dispozici|Ne|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(None), přenos zpráv, ve smíšeném|(Žádný)|(Žádný)|není k dispozici|Text, (MTOM)|Ano<br /><br /> (vyrovnávací paměti).|  
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Přenos), ve smíšeném zpráva, None,|(Přenos), spolehlivé relace, relace zabezpečení|Ano (none),|Ano|binární|Ano<br /><br /> (vyrovnávací paměti).|  
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Ve smíšeném přenosu (zprávy)|(None), spolehlivé relace, relace zabezpečení|Ano (none),|není k dispozici|Text, (MTOM)|Ne|  
|<xref:System.ServiceModel.UdpBinding>|Rozhraní .NET **Poznámka:** interoperabilita dosáhnout implementací standardní specifikace protokolu SOAP. přes UDP, která implementuje tuto vazbu.|(Žádný)|(Žádný)|(Žádný)|není k dispozici|(Text)|Ne|  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.NetHttpBinding> používá binární kódování ve výchozím nastavení je vazbu pro využívání služeb HTTP nebo protokolu WebSocket. <xref:System.ServiceModel.NetHttpBinding> rozpozná, jestli se používá s kontraktu požadavku a odpovědi nebo duplexního kontraktu a změnit své chování tak, aby odpovídaly – HTTP se bude používat pro požadavek odpověď a WebSockets pro duplexní režim. Toto chování lze přepsat pomocí <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A>--> `System.ServiceModel.NetHttpBinding.WebSocketTransportUsage` vazby nastavení: dovolené - Toto je výchozí hodnota a chová, jak je popsáno výše. NotAllowed – to zabraňuje objekty WebSockets. Pokus o použití duplexního kontraktu s tímto nastavením bude mít za následek výjimku. Vyžaduje - vynutí objekty WebSockets použije i pro kontraktů požadavek odpověď. NetHttpBinding podporuje spolehlivé relace v HTTP režimu i režimu protokolu WebSocket. V protokolu WebSocket relace režimu jsou poskytovány přenosu.  
  
 Následující tabulka vysvětluje funkcí uvedených v předchozí tabulce.  
  
|Funkce|Popis|  
|-------------|-----------------|  
|Typ interoperability|Název protokolu nebo technologii, se kterým zajišťuje vazby vzájemná spolupráce.|  
|Zabezpečení|Určuje, jak jsou zabezpečená kanál:<br /><br /> -None: Není zabezpečené zprávu protokolu SOAP a klient není ověřen.<br />-Přenos: V přenosové vrstvě jsou splněné požadavky na zabezpečení.<br />-Zpráva: Ve vrstvě zprávy jsou splněny požadavky na zabezpečení.<br />-Ve smíšeném: Deklarace identity se přenášejí ve zprávě; Přenosová vrstva jsou splněny požadavky integrity a důvěrnosti.|  
|Relace|Určuje, jestli tato vazba podporuje kontrakty relace.|  
|Transakce|Určuje, zda je povoleno transakce.|  
|Duplex|Určuje, zda jsou podporovány duplexní kontrakty. Všimněte si, že tato funkce vyžaduje podporu pro relace vazba.|  
|Kódování|Určuje přenosový formát zprávy. Povolené hodnoty:<br /><br /> -Text: pro příklad UTF-8.<br />-Binární<br />-Zpráva přenosu optimalizace mechanismus (MTOM): Metodu pro efektivní kódování binární elementů XML v rámci obálky protokolu SOAP.|  
|streamování|Určuje, zda streamování je podporováno pro příchozí a odchozí zprávy. Použití `TransferMode` vlastnost vazby k nastavení hodnoty. Povolené hodnoty:<br /><br /> -   <xref:System.ServiceModel.TransferMode.Buffered>: Zprávy požadavku a odpovědi jsou obě do vyrovnávací paměti.<br />-   <xref:System.ServiceModel.TransferMode.Streamed>Je streamování: zprávy požadavku a odpovědi.<br />-   <xref:System.ServiceModel.TransferMode.StreamedRequest>: Je streamování zprávu požadavku a zprávu odpovědi do vyrovnávací paměti.<br />-   <xref:System.ServiceModel.TransferMode.StreamedResponse>: Zprávu požadavku do vyrovnávací paměti a je streamování zprávu odpovědi.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
