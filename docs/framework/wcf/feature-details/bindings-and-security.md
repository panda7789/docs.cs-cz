---
title: Vazby a zabezpečení
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
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: 42
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 5eb1019694f6228edbe3656849b85dfa7611ef18
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="bindings-and-security"></a>Vazby a zabezpečení
Vazby poskytované systémem, který je součástí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] nabízejí rychlý způsob, jak program [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. S jednou výjimkou mít všechny vazby výchozí schéma zabezpečení povoleno. Toto téma vám pomůže vybrat správné vazba pro potřebné požadavky na zabezpečení.  
  
 Přehled [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení, najdete v části [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] programování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí vazby, najdete v tématu [programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Pokud jste již vybrali vazbu, najdete další informace o běhu chování, které jsou přidruženy zabezpečení v [chování zabezpečení](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Některé funkce zabezpečení nejsou programovatelný pomocí vazby poskytované systémem. Použití vlastní vazby další ovládací prvek, najdete v části [možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Funkce zabezpečení vazeb  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje několik vazeb poskytovaných systémem, které splňují většinu potřeb. Pokud konkrétní vazba není stačí, můžete také vytvořit vlastní vazby. Seznam vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] vlastní vazby, najdete v části [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Každé vazby v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] má dvě formy: jako rozhraní API a jako element XML, který je použit v konfiguračním souboru. Například `WSHttpBinding` (API) má protějšek v [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 V následující části jsou uvedeny oba formuláře pro každou vazbu a shrnuje funkce zabezpečení.  
  
### <a name="basichttp"></a>BasicHttp  
 V kódu pomocí <xref:System.ServiceModel.BasicHttpBinding> třídy, v konfiguraci, pomocí [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Tato vazba je určen k použití s rozsahem existujících technologií, včetně následujících:  
  
-   ASP.NET – webové služby (ASMX), verze 1.  
  
-   Webové aplikace služby vylepšení (WSE).  
  
-   Basic profilu, jak jsou definovány v Interoperability webové služby (WS-I) specifikace ([http://go.microsoft.com/fwlink/?LinkId=38955](http://go.microsoft.com/fwlink/?LinkId=38955)).  
  
-   Profil základní zabezpečení, jak jsou definovány v WS-I.  
  
 Ve výchozím nastavení není tato vazba zabezpečený. Je určený pro spolupráci s ASMX služby. Pokud je povoleno zabezpečení, vazba je určená pro bezproblémové vzájemná spolupráce s mechanismy zabezpečení Internetové informační služby (IIS), například základní ověřování, ověřování algoritmem digest a integrované zabezpečení systému Windows. Další informace najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Tato vazba podporuje následující funkce:  
  
-   Zabezpečení přenosu HTTPS.  
  
-   Základní ověřování protokolu HTTP.  
  
-   WS-zabezpečení.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, a <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 V kódu pomocí <xref:System.ServiceModel.WSHttpBinding> třídy, v konfiguraci, pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Ve výchozím nastavení, tuto vazbu implementuje specifikace WS-zabezpečení a poskytuje vzájemnou funkční spolupráci s službami, které implementují WS-* specifikace. Podporuje následující:  
  
-   Zabezpečení přenosu HTTPS.  
  
-   WS-zabezpečení.  
  
-   HTTPS přenosu ochrany pomocí protokolu SOAP zprávy pověření zabezpečení pro ověřování volající.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, a <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>– WSDualHttpBinding  
 V kódu pomocí <xref:System.ServiceModel.WSDualHttpBinding> třídy, v konfiguraci, pomocí [ \<– wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Tato vazba je navržených k povolení aplikace duplexní služby. Tato vazba implementuje specifikace WS-zabezpečení pro zabezpečení na základě zpráv přenosu. Zabezpečení přenosu není k dispozici. Ve výchozím nastavení poskytuje následující funkce:  
  
-   Implementuje WS-spolehlivé zasílání zpráv pro spolehlivost.  
  
-   Implementuje WS-zabezpečení pro zabezpečení přenosu a ověřování.  
  
-   Využívá protokol HTTP pro doručování zpráv.  
  
-   Používá, text/XML kódování zprávy.  
  
 Vazba pomocí protokolu WS-zabezpečení (zpráva layer security), umožňuje nakonfigurovat následující parametry:  
  
-   Sada algoritmů zabezpečení k určení kryptografického algoritmu.  
  
-   Vazba možnosti pro následující:  
  
    -   Poskytování služby přihlašovací údaje k dispozici out-of-band na straně klienta.  
  
    -   Poskytování pověření služby vyjednal ze služby jako součást instalace kanálu.  
  
 Další informace naleznete v tématu <xref:System.ServiceModel.WSDualHttpSecurity> a <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 V kódu pomocí <xref:System.ServiceModel.NetTcpBinding> třídy, v konfiguraci, pomocí [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Tato vazba je optimalizovaná pro komunikaci mezi počítači. Ve výchozím nastavení má následující vlastnosti:  
  
-   Implementuje přenosové vrstvy zabezpečení.  
  
-   Využívá zabezpečení systému Windows pro přenos zabezpečení a ověřování.  
  
-   TCP používá pro přenos.  
  
-   Implementuje zprávy v binární kódování.  
  
-   Implementuje WS-spolehlivé zasílání zpráv.  
  
 Mezi možnosti patří následující:  
  
-   Zabezpečení zpráv vrstvy (pomocí protokolu WS-Security).  
  
-   Přenosu zabezpečení s pověřením zpráv – utajení a integrity poskytuje podle zabezpečení TLS (Transport Layer) přes TCP a přihlašovací údaje pro autorizaci poskytované WS-zabezpečení.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, a <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 V kódu pomocí <xref:System.ServiceModel.NetNamedPipeBinding> třídy, v konfiguraci, pomocí [ \<– netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Tato vazba je optimalizovaná pro komunikaci mezi procesy (obvykle ve stejném počítači). Ve výchozím nastavení tato vazba má následující vlastnosti:  
  
-   Používá přenosu zabezpečení pro přenos zpráv a ověřování.  
  
-   Využívá pojmenované kanály pro doručování zpráv.  
  
-   Implementuje zprávy v binární kódování.  
  
-   Šifrování a podepisování zpráv.  
  
 Mezi možnosti patří následující:  
  
-   Ověřování pomocí zabezpečení systému Windows.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, a <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 V kódu pomocí <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy; v konfiguraci, použijte [ \<– msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Tato vazba je optimalizovaný pro vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů a služeb, které spolupracovat s jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncové body Microsoft služby Řízení front zpráv (MSMQ).  
  
 Ve výchozím nastavení tato vazba používá zabezpečení přenosu a poskytuje následující vlastnosti zabezpečení:  
  
-   Zabezpečení může být zakázán (žádný).  
  
-   Zabezpečení přenosu služby MSMQ (přenos).  
  
 Další informace naleznete v tématu <xref:System.ServiceModel.NetMsmqSecurity> a <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>– NetMsmqBinding  
 V kódu pomocí <xref:System.ServiceModel.NetMsmqBinding> třídy, v konfiguraci, pomocí [ \<– netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 Tato vazba je určena pro použití při vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které vyžadují služby MSMQ Podpora zpráv zařazených do fronty.  
  
 Ve výchozím nastavení tato vazba používá zabezpečení přenosu a poskytuje následující vlastnosti zabezpečení:  
  
-   Zabezpečení může být zakázán (žádný).  
  
-   Zabezpečení přenosu služby MSMQ (přenos).  
  
-   Zabezpečení zpráv založený na protokolu SOAP (zprávy).  
  
-   Souběžné přenosu zpráv zabezpečení a (oba).  
  
-   Podporované typy pověření klienta: None, Windows, uživatelské jméno, certifikát, IssuedToken.  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> Přihlašovacích údajů je podporována pouze v případě, že režim zabezpečení je nastaven na hodnotu <xref:System.ServiceModel.NetMsmqSecurityMode.Both> nebo <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 Další informace naleznete v tématu <xref:System.ServiceModel.MessageSecurityOverMsmq> a <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>– WSFederationHttpBinding  
 V kódu pomocí <xref:System.ServiceModel.WSFederationHttpBinding> třídy, v konfiguraci, pomocí [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Ve výchozím nastavení používá tuto vazbu WS-zabezpečení (zpráva layer security).  
  
 Další informace najdete v tématu [Federation](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, a <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Pokud žádná z vazby poskytované systémem splňuje požadavky, můžete vytvořit vlastní vazby s elementem vazba vlastní zabezpečení. Další informace najdete v tématu [možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Možnosti vázání  
 Následující tabulka shrnuje funkce služeb v nastavení režimu zabezpečení, to znamená, zobrazí se seznam funkcí dostupných režim zabezpečení je nastavena na `Transport`, `Message`, nebo `TransportWithMessageCredential`. Pomocí této tabulky a umožňují najít funkce zabezpečení, které vaše aplikace vyžaduje.  
  
|Nastavení|Funkce|  
|-------------|--------------|  
|Přenos|Ověření serveru<br /><br /> Ověření klienta<br /><br /> Zabezpečení typu Point-to-Point<br /><br /> Interoperabilita<br /><br /> Hardwarová akcelerace<br /><br /> Vysoká propustnost<br /><br /> Zabezpečení brány firewall<br /><br /> Aplikace s vysokou latencí<br /><br /> Znova šifrovat mezi několik segmentů směrování|  
|Zpráva|Ověření serveru<br /><br /> Ověření klienta<br /><br /> Koncové zabezpečení<br /><br /> Interoperabilita<br /><br /> Deklarace identity formátováním<br /><br /> Federace<br /><br /> Vícefaktorové ověřování<br /><br /> Vlastní tokeny<br /><br /> Služba notář/časové razítko<br /><br /> Aplikace s vysokou latencí<br /><br /> Trvalost podpisy zpráv|  
|TransportWithMessageCredential|Ověření serveru<br /><br /> Ověření klienta<br /><br /> Zabezpečení typu Point-to-Point<br /><br /> Interoperabilita<br /><br /> Hardwarová akcelerace<br /><br /> Vysoká propustnost<br /><br /> Deklarace identity plně funkčního klienta<br /><br /> Federace<br /><br /> Vícefaktorové ověřování<br /><br /> Vlastní tokeny<br /><br /> Zabezpečení brány firewall<br /><br /> Aplikace s vysokou latencí<br /><br /> Znova šifrovat mezi několik segmentů směrování|  
  
 Následující tabulka uvádí vazby, které podporují různé nastavení režimu. Vyberte vazbu tabulku, kterou chcete použít k vytvoření vašeho koncového bodu služby.  
  
|Vazba|Podpora režimu přenosu|Podpora režimu zpráv|Podpora TransportWithMessageCredential|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|Ano|Ano|Ano|  
|`WSHttpBinding`|Ano|Ano|Ano|  
|`WSDualHttpBinding`|Ne|Ano|Ne|  
|`NetTcpBinding`|Ano|Ano|Ano|  
|`NetNamedPipeBinding`|Ano|Ne|Ne|  
|`NetMsmqBinding`|Ano|Ano|Ne|  
|`MsmqIntegrationBinding`|Ano|Ne|Ne|  
|`wsFederationHttpBinding`|Ne|Ano|Ano|  
  
## <a name="transport-credentials-in-bindings"></a>Přihlašovací údaje přenosu v vazby  
 Následující tabulka uvádí typy přihlašovacích údajů klienta, která je k dispozici při použití buď `BasicHttpBinding` nebo `WSHttpBinding` v režimu zabezpečení přenosu.  
  
|Typ|Popis|  
|----------|-----------------|  
|Žádné|Určuje, že klient nemusí k dispozici žádné pověření. Výsledkem anonymním klientem.|  
|Základní|Základní ověřování. Další informace najdete v tématu RFC 2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest, k dispozici na [ http://go.microsoft.com/fwlink/?LinkId=84023 ](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|Ověřování algoritmem Digest|Ověřování hodnotou hash. Další informace najdete v tématu RFC 2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest, k dispozici na [ http://go.microsoft.com/fwlink/?LinkId=84023 ](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|NTLM|Ověřování NT LAN Manager (NTLM).|  
|Windows|Ověřování systému Windows.|  
|certifikát|Ověřování se provádí pomocí certifikátu.|  
|IssuedToken|Umožňuje službě vyžadují, ověření klienta pomocí tokenem vydaným službou tokenů zabezpečení nebo pomocí [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Další informace najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Zpráva pověření klienta v vazby  
 Následující tabulka uvádí typy přihlašovacích údajů klienta, která je k dispozici při použití vazby v režimu zabezpečení zpráv.  
  
|Typ|Popis|  
|----------|-----------------|  
|Žádné|Umožňuje pracovat s anonymní klienty služby.|  
|Windows|Umožňuje výměny zpráv protokolu SOAP podle pro ověřený kontext pověření systému Windows.|  
|UserName|Umožňuje službě vyžadují, ověření klienta pomocí pověření uživatele název. Všimněte si, že když režim zabezpečení je nastavený na `TransportWithMessageCredential`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepodporuje odesílání heslo hodnotou hash nebo odvozování klíče pomocí hesla a použití tyto klíče pro režim zabezpečení zpráv. Jako takový [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vynutí, že při použití přihlašovací údaje uživatele název zabezpečené přenosu.|  
|certifikát|Umožňuje službě vyžadují, ověření klienta pomocí certifikátu.|  
|IssuedToken|Umožňuje zadat vlastní token pomocí služby tokenů zabezpečení služby.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Výběr typu přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Chování zabezpečení](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
