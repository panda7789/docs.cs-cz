---
title: Konfigurace vazeb poskytovaných systémem
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: c2c1f468fba404768fe01e84260125843964fea0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949628"
---
# <a name="configuring-system-provided-bindings"></a>Konfigurace vazeb poskytovaných systémem
Vazby určují komunikační mechanismus, který se má použít při komunikaci s koncovým bodem, a označuje, jak se připojit ke koncovému bodu. Vazby se skládají z prvků, které definují, jak jsou kanály Windows Communication Foundation (WCF) vrstveny, aby poskytovaly požadované funkce komunikace. Vazba obsahuje tři typy prvků:  
  
- Prvky vazby kanálu, které určují zabezpečení, spolehlivost, nastavení toku kontextu nebo uživatelsky definované protokoly pro použití se zprávami odesílanými do koncového bodu.  
  
- Prvky vazby přenosového kanálu, které určují podkladový transportní protokol, který se má použít při odesílání zpráv do koncového bodu, například TCP nebo HTTP.  
  
- Prvky vazby kódování zpráv, které určují kódování přenosů, které se mají použít pro zprávy odesílané do koncového bodu, například text/XML, binární nebo mechanismus optimalizace přenosu zpráv (MTOM).  
  
 V tomto tématu jsou uvedeny všechny vazby Windows Communication Foundation poskytované systémem (WCF). Pokud žádný z těchto kroků nesplňuje přesné požadavky vaší aplikace, můžete vytvořit vazbu pomocí <xref:System.ServiceModel.Channels.CustomBinding> třídy. Další informace o vytváření vlastních vazeb najdete v tématu [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
> Vyberte vazbu s povoleným zabezpečením. Ve výchozím nastavení mají všechny vazby s výjimkou <xref:System.ServiceModel.BasicHttpBinding> vazby zapnuté zabezpečení. Pokud nevyberete zabezpečenou vazbu nebo pokud zakážete zabezpečení, ujistěte se, že jsou vaše síťové výměny chráněny jiným způsobem, například v zabezpečeném datovém centru nebo v izolované síti.  
  
> [!IMPORTANT]
> Nepoužívejte oboustranné smlouvy s vazbami, které nepodporují zabezpečení, nebo které mají zakázané zabezpečení, pokud není síť zabezpečená jiným způsobem.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 Následující vazby jsou dodávány pomocí WCF.  
  
|Vazba|Konfigurační element|Popis|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Vazba, která je vhodná pro komunikaci s profilem WS-Basic, který splňuje webové služby, například služby založené na ASP.NET Web Services (ASMX). Tato vazba používá jako výchozí kódování zprávy HTTP jako Transport a text/XML.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Zabezpečená a interoperabilní vazba, která je vhodná pro neduplexní kontrakty služeb.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Zabezpečená a interoperabilní vazba, která poskytuje podporu pro správné verze <xref:System.ServiceModel.WSHttpBinding.Security%2A>prvků, <xref:System.ServiceModel.ReliableSession>a <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> vazby.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Zabezpečená a interoperabilní vazba, která je vhodná pro duplexní kontrakty služeb nebo komunikace prostřednictvím zprostředkovatelů SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Zabezpečená a interoperabilní vazba, která podporuje protokol WS-Federation umožňující organizacím ve federaci efektivně ověřovat a autorizovat uživatele.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Zabezpečená a interoperabilní vazba, která je odvozena <xref:System.ServiceModel.WS2007HttpBinding> z a podporuje federované zabezpečení.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Zabezpečená a optimalizovaná vazba vhodná pro komunikaci mezi počítači mezi aplikacemi WCF.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Zabezpečená, spolehlivá a optimalizovaná vazba, která je vhodná pro komunikaci na počítači mezi aplikacemi WCF.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Vazba zařazená do fronty, která je vhodná pro komunikaci mezi počítači mezi aplikacemi WCF.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Vazba, která umožňuje zabezpečenou komunikaci s více počítači.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Vazba používaná ke konfiguraci koncových bodů pro webové služby WCF, které jsou vystaveny prostřednictvím požadavků HTTP namísto zpráv SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Vazba, která je vhodná pro komunikaci mezi počítači mezi aplikací WCF a stávajícími službami řízení front zpráv (označované také jako MSMQ).|  
  
## <a name="binding-features"></a>Funkce vazby  
 V následující tabulce jsou uvedeny některé klíčové funkce pro každou ze zadaných vazeb poskytovaných systémem. Vazby jsou uvedeny v prvním sloupci a informace týkající se funkcí jsou popsány v tabulce. Následující tabulka poskytuje klíč pro použité zkratky vazby. Pokud chcete vybrat vazbu, určete, který sloupec bude vyhovovat všem funkcím řádku, které potřebujete.  
  
|Vazba|Interoperabilita|Režim zabezpečení (výchozí)|Relace<br /><br /> (Výchozí)|Transakce|Duplex|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Základní profil 1,1|(Žádné), přenos, zpráva, smíšená|Žádné, (žádné)|NTato|není k dispozici|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Žádná, přenosová, (zpráva), smíšená|(Žádné), přenos, Spolehlivá relace|(Žádné), ano|není k dispozici|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|Žádná, přenosová, (zpráva), smíšená|(Žádné), přenos, Spolehlivá relace|(Žádné), ano|není k dispozici|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Žádné, (zpráva)|(Spolehlivá relace)|(Žádné), ano|Ano|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Žádná, (zpráva), smíšená|(Žádné), Spolehlivá relace|(Žádné), ano|Ne|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Žádná, (zpráva), smíšená|(Žádné), Spolehlivá relace|(Žádné), ano|Ne|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Žádné, (Transport), zpráva,<br /><br /> Smíšený|Spolehlivá relace, (přenos)|(Žádné), ano|Ano|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|NTato<br /><br /> Přepravu|Žádné, (Transport)|(Žádné), ano|Ano|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Žádná, zpráva, (Transport), obojí|NTato|(Žádné), ano|Ne|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Zařízeními|Žádná, zpráva, (Transport), smíšené|NTato|NTato|Ano|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|Žádný, přenos, TransportCredentialOnly|NTato|NTato|není k dispozici|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Žádné, (Transport)|NTato|(Žádné), ano|není k dispozici|  
  
 V následující tabulce jsou vysvětleny funkce, které najdete v předchozí tabulce.  
  
|Funkce|Popis|  
|-------------|-----------------|  
|Typ interoperability|Pojmenuje protokol nebo technologii, se kterými vazba zajišťuje meziprovozu.|  
|Zabezpečení|Určuje, jak je kanál zabezpečený:<br /><br /> NTato Zpráva SOAP není zabezpečená a klient není ověřen.<br />Přepravu Požadavky na zabezpečení jsou splněné na transportní vrstvě.<br />Zpráva Požadavky na zabezpečení jsou splněné ve vrstvě zpráv.<br />Smíšený Tento režim zabezpečení je známý jako `TransportWithMessageCredentials`. Zpracovává přihlašovací údaje na úrovni zprávy a požadavky na integritu a důvěrnost jsou splněné přenosovou vrstvou.<br />Protokoly Je použita úroveň zprávy i zabezpečení na úrovni přenosu. Tato možnost je jedinečná pro <xref:System.ServiceModel.NetMsmqBinding>.|  
|Relace|Určuje, zda tato vazba podporuje kontrakty relace.|  
|Transakce|Určuje, zda jsou povoleny transakce.|  
|Duplex|Určuje, zda jsou podporovány duplexní kontrakty. Poznámka: Tato funkce vyžaduje podporu pro relace ve vazbě.|  
|Streamování|Určuje, jestli je podporované streamování zpráv.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
