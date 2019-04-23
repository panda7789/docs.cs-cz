---
title: Konfigurace vazeb poskytovaných systémem
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: 0dc213c2d25558dc447b49d2b2378f9aa72f80a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172806"
---
# <a name="configuring-system-provided-bindings"></a>Konfigurace vazeb poskytovaných systémem
Vazby zadejte komunikační mechanizmus použít při komunikaci se koncový bod a určují, jak se připojit do koncového bodu. Vazby obsahovat prvky, které definují, jak kanálů Windows Communication Foundation (WCF) jsou rozloženy do vrstev nahoru a zajistit tak funkce požadovanou komunikaci. Vazba obsahuje tři typy prvků:  
  
-   Elementy vazby kanálu protokolu, které určují nastavení zabezpečení, spolehlivost, nastavení toku kontextu nebo uživatelem definované protokolů pro použití s zprávy odeslané do koncového bodu.  
  
-   Kanál elementů přenosové vazby, které určují základní přenos protokol se má použít při odesílání zpráv do koncových bodů, například TCP nebo HTTP.  
  
-   Kódování elementy vazby, které určují při přenosu kódování použité pro zprávy odeslané do koncového bodu, například text/XML, binární, zprávy nebo zprávy přenosu optimalizace mechanismus (MTOM).  
  
 Toto téma představuje všechny vazby poskytované systémem Windows Communication Foundation (WCF). Pokud žádná z nich nesplňuje přesných požadavcích pro vaši aplikaci, můžete vytvořit vazbu pomocí <xref:System.ServiceModel.Channels.CustomBinding> třídy. Další informace o vytváření vlastních vazeb naleznete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Vyberte vazbu s povoleným zabezpečením. Ve výchozím nastavení všechny vazby, s výjimkou <xref:System.ServiceModel.BasicHttpBinding> vazby, mají povoleno zabezpečení. Pokud vyberete bezpečnou vazbu, nebo pokud zakážete, zabezpečení, ujistěte se, že vaše síť výměny jsou chráněné jiným způsobem, jako je například v zabezpečené datovém centru nebo v izolované síti.  
  
> [!IMPORTANT]
>  Nepoužívejte duplexní kontrakty s vazbami, které nepodporují zabezpečení nebo mají zabezpečení zakázán, pokud síť exchange je zabezpečený jiným způsobem.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 Tyto vazby se dodávají s použitím technologie WCF.  
  
|Vazba|Element konfigurace|Popis|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Vazby, který je vhodný pro komunikaci s profilu WS-Basic vyhovující webové služby, například webových služeb ASP.NET (ASMX) – na základě služeb. Tato vazba používá protokol HTTP jako přenosu a text/XML jako výchozí kódování zprávy.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Zabezpečená a interoperabilní vazbu, která je vhodné pro neduplexní servisní smlouvy.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Zabezpečená a interoperabilní vazbu, která poskytuje podporu pro správné verze prvků <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementů vazby.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Zabezpečená a interoperabilní vazbu, která je vhodná pro duplexní kontrakty služeb nebo komunikace prostřednictvím zprostředkovatelů SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Zabezpečená a interoperabilní vazba, která podporuje protokol WS-Federation, umožňujících organizacím, které jsou ve federaci efektivně ověřovat a autorizovat uživatele.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Zabezpečená a interoperabilní vazbu, která je odvozena z <xref:System.ServiceModel.WS2007HttpBinding> a podporuje zabezpečení.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Zabezpečené a optimalizované vazby vhodné pro komunikaci mezi počítači mezi aplikací služby WCF.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Zabezpečená, spolehlivá a optimalizovaná vazby, který je vhodný pro komunikaci na počítači mezi aplikací služby WCF.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Vazbu s frontou, který je vhodný pro komunikaci mezi počítači mezi aplikací služby WCF.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Vazba, která umožňuje zabezpečenou a více počítači komunikaci.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Vazba použitá ke konfiguraci koncových bodů webových služeb WCF, které jsou přístupné přes požadavky HTTP namísto zpráv SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Vazby, který je vhodný pro komunikaci mezi počítači mezi aplikace WCF a stávající služby Řízení front zpráv (MSMQ) aplikace.|  
  
## <a name="binding-features"></a>Vazba funkce  
 V následující tabulce jsou uvedeny některé klíčové funkce všech vazeb poskytovaných systémem, který je k dispozici. Vazby jsou uvedeny v prvním sloupci a informace týkající se funkcí jsou popsány v tabulce. Následující tabulka poskytuje klíč pro zkratky vazba používá. Vyberte vazbu, určete, který sloupec splňuje všechny funkce řádků, které potřebujete.  
  
|Vazba|Interoperabilita|Režim zabezpečení (výchozí)|Relace<br /><br /> (Výchozí)|Transakce|Duplex|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Žádné), přenos zpráv, smíšené|NONE, (None)|(Žádné)|není k dispozici|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|NONE, přenosu, (zpráva), smíšené|(Žádné), přenosu, spolehlivé relace|Ano (žádné)|není k dispozici|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|NONE, přenosu, (zpráva), smíšené|(Žádné), přenosu, spolehlivé relace|Ano (žádné)|není k dispozici|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Žádný (zprávy)|(Stabilní relace)|Ano (žádné)|Ano|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Žádný (zpráva), smíšené|(Žádné), spolehlivé relace|Ano (žádné)|Ne|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Žádný (zpráva), smíšené|(Žádné), spolehlivé relace|Ano (žádné)|Ne|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Žádný (přenos), zprávy,<br /><br /> Smíšené|Spolehlivá relace (přenos)|Ano (žádné)|Ano|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|NONE,<br /><br /> (Přenos)|Žádný (přenos)|Ano (žádné)|Ano|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Žádné, zprávu, (přenos), obojí|(Žádné)|Ano (žádné)|Ne|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Peer|Žádné, zprávu, (přenos), smíšené|(Žádné)|(Žádné)|Ano|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|NONE, přenosu, TransportCredentialOnly|(Žádné)|(Žádné)|není k dispozici|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Žádný (přenos)|(Žádné)|Ano (žádné)|není k dispozici|  
  
 Následující tabulka popisuje možnosti, které najdete v předchozí tabulce.  
  
|Funkce|Popis|  
|-------------|-----------------|  
|Vzájemná funkční spolupráce typu|Název protokolu nebo technologie, pomocí kterého se vazba zajistí vzájemná spolupráce grafického subsystému.|  
|Zabezpečení|Určuje, jak je zabezpečený kanál:<br /><br /> -Žádný: Není zabezpečen zprávu protokolu SOAP a klient není ověřený.<br />-Přenos: V přenosové vrstvě jsou splněny požadavky na zabezpečení.<br />– Zprávy: Ve vrstvě zprávy jsou splněny požadavky na zabezpečení.<br />-Smíšené: Tento režim zabezpečení se označuje jako `TransportWithMessageCredentials`. Zpracovává přihlašovací údaje na úrovni zpráv a integritu a důvěrnost požadavky splněny přenosové vrstvy.<br />-Obojí: Obě úrovně a přenosu zabezpečením úrovně zprávy se používají. Tato možnost je jedinečné pro <xref:System.ServiceModel.NetMsmqBinding>.|  
|Relace|Určuje, zda tato vazba podporuje kontrakty relací.|  
|Transakce|Určuje, zda je povoleno transakce.|  
|Duplex|Určuje, zda jsou podporovány duplexní kontrakty. Všimněte si, že tato funkce vyžaduje podporu pro relace ve vazbě.|  
|Streamování|Určuje, zda je podporováno datové proudy zpráv.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
