---
title: Vazby a zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 5e3a8bc58d0828f50feb7752eb438d41695460fa
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611901"
---
# <a name="bindings-and-security"></a>Vazby a zabezpečení
Vazby poskytované systémem zahrnuté Windows Communication Foundation (WCF) nabízí rychlý způsob, jak programovat aplikace WCF. S jednou výjimkou mají všechny vazby výchozí schéma zabezpečení povoleno. Toto téma vám pomůže vybrat správné vazba pro vaše požadavky na zabezpečení.  
  
 Přehled zabezpečení WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o programování WCF pomocí vazby najdete v tématu [programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Pokud jste již vybrali vazbu, najdete další informace o chování za běhu, které souvisejí se zabezpečením v [chování zabezpečení](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Některé funkce zabezpečení nejsou programovatelný pomocí vazeb poskytovaných systémem. Použití vlastní vazby větší kontrolu, naleznete v tématu [možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Funkce zabezpečení vazeb  
 WCF obsahuje několik vazeb poskytovaných systémem, které většině potřeb. Pokud konkrétní vazbu není stačit, můžete také vytvořit vlastní vazby. Seznam vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md). Další informace o vlastních vazeb naleznete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Každá vazba ve službě WCF má dvě formy: jako rozhraní API a jako XML prvku použitého v konfiguračním souboru. Například `WSHttpBinding` (API) má protějšek [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Následující část uvádí obě formy pro každou vazbu a shrnuje funkce zabezpečení.  
  
### <a name="basichttp"></a>BasicHttp  
 V kódu, použijte <xref:System.ServiceModel.BasicHttpBinding> třídy; v konfiguraci, použijte [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Tato vazba je určen pro použití s celou řadu existujících technologií, včetně následujících:  
  
-   ASP.NET Web services (ASMX), verze 1.  
  
-   Webové aplikace služby vylepšení (Najít).  
  
-   Basic Profile jak jsou definovány v Interoperability webové služby (WS-I) specifikace (<https://go.microsoft.com/fwlink/?LinkId=38955>).  
  
-   Profil základní zabezpečení, jak jsou definovány v WS-I.  
  
 Ve výchozím nastavení tato vazba není zabezpečený. Je určená pro spolupráci se službami ASMX. Když je povolené zabezpečení, vazby je navržená pro bezproblémovou spolupráci s mechanismy zabezpečení Internetové informační služby (IIS), jako je například základní ověřování hodnotou hash a integrované zabezpečení Windows. Další informace najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Tato vazba podporuje následující funkce:  
  
-   Zabezpečení přenosu HTTPS.  
  
-   Základní ověřování protokolu HTTP.  
  
-   WS-Security.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, a <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 V kódu, použijte <xref:System.ServiceModel.WSHttpBinding> třídy; v konfiguraci, použijte [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Ve výchozím nastavení, tato vazba implementuje specifikaci WS-Security a nabízí interoperabilitu mezi službami, které implementují WS-* specifikace. Podporuje následující:  
  
-   Zabezpečení přenosu HTTPS.  
  
-   WS-Security.  
  
-   HTTPS přenosu ochrany pomocí pověření zabezpečení zpráv SOAP za účelem ověřování totožnosti volající.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, a <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 V kódu, použijte <xref:System.ServiceModel.WSDualHttpBinding> třídy; v konfiguraci, použijte [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Tato vazba je navržená k umožnění duplexní služby aplikace. Tato vazba implementuje specifikaci WS-Security pro zabezpečení na základě zpráv přenosu. Zabezpečení přenosu není k dispozici. Ve výchozím nastavení poskytuje následující funkce:  
  
-   Implementuje zasílání zpráv WS-Reliable spolehlivosti.  
  
-   Implementuje pro ověřování a zabezpečení přenosu WS-Security.  
  
-   Používá protokol HTTP pro doručování zpráv.  
  
-   Použije kódování zprávy text/XML.  
  
 Vazba pomocí WS-Security (zabezpečení vrstvy zpráva), umožňuje nakonfigurovat následující parametry:  
  
-   Sada algoritmů zabezpečení k určení kryptografického algoritmu.  
  
-   Vazba pro následující možnosti:  
  
    -   Poskytuje služby přihlašovací údaje k dispozici out-of-band na straně klienta.  
  
    -   Zadání přihlašovacích údajů služby vyjednávat ze služby jako součást instalace kanálu.  
  
 Další informace naleznete v tématu <xref:System.ServiceModel.WSDualHttpSecurity> a <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 V kódu, použijte <xref:System.ServiceModel.NetTcpBinding> třídy; v konfiguraci, použijte [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Tato vazba je optimalizovaná pro komunikaci mezi počítači. Ve výchozím nastavení má následující vlastnosti:  
  
-   Implementuje přenosové vrstvy zabezpečení.  
  
-   Využívá Windows zabezpečení pro ověřování a zabezpečení přenosu.  
  
-   Používá protokol TCP pro přenos.  
  
-   Implementuje kódování binární zprávy.  
  
-   Implementuje posílání WS-Reliable.  
  
 Mezi možnosti patří následující:  
  
-   Zabezpečení zpráv vrstvy (pomocí WS-Security).  
  
-   Zabezpečení s pověřením zpráv přenosu – důvěrnost a integrita poskytuje tak zabezpečení TLS (Transport Layer) přes TCP a přihlašovací údaje pro autorizaci poskytuje WS-Security.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, a <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 V kódu, použijte <xref:System.ServiceModel.NetNamedPipeBinding> třídy; v konfiguraci, použijte [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Tato vazba je optimalizovaná pro komunikaci mezi procesy (obvykle ve stejném počítači). Ve výchozím nastavení tato vazba má následující vlastnosti:  
  
-   Používá přenos pro přenos zpráv a ověřování zabezpečení.  
  
-   Použití pojmenované kanály pro doručování zpráv.  
  
-   Implementuje kódování binární zprávy.  
  
-   Šifrování a podepisování zpráv.  
  
 Mezi možnosti patří následující:  
  
-   Ověřování pomocí zabezpečení Windows.  
  
 Další informace najdete v tématu <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, a <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 V kódu, použijte <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy; v konfiguraci, použijte [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Tato vazba je optimalizovaný pro vytváření klienti WCF a služeb, které spolupracují s koncovými body mimo - WCF Microsoft řízení front zpráv MSMQ.  
  
 Ve výchozím nastavení tato vazba používá zabezpečení přenosu a obsahuje následující vlastnosti zabezpečení:  
  
-   Zabezpečení může být zakázány (žádné).  
  
-   Zabezpečení přenosu služby MSMQ (přenos).  
  
 Další informace naleznete v tématu <xref:System.ServiceModel.NetMsmqSecurity> a <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 V kódu, použijte <xref:System.ServiceModel.NetMsmqBinding> třídy; v konfiguraci, použijte [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 Tato vazba je určena pro použití při vytváření služeb WCF, které vyžadují služby MSMQ Podpora zpráv zařazených do fronty.  
  
 Ve výchozím nastavení tato vazba používá zabezpečení přenosu a obsahuje následující vlastnosti zabezpečení:  
  
-   Zabezpečení může být zakázány (žádné).  
  
-   Zabezpečení přenosu služby MSMQ (přenos).  
  
-   Zabezpečení založené na protokolu SOAP zprávy (zprávy).  
  
-   Souběžné přenosu zpráv zabezpečení a (i).  
  
-   Podporované typy přihlašovacích údajů klienta: Žádný, Windows, uživatelské jméno, certifikát, třídy IssuedToken.  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> Přihlašovacích údajů se podporuje jenom režim zabezpečení je nastaven na hodnotu <xref:System.ServiceModel.NetMsmqSecurityMode.Both> nebo <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 Další informace naleznete v tématu <xref:System.ServiceModel.MessageSecurityOverMsmq> a <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 V kódu, použijte <xref:System.ServiceModel.WSFederationHttpBinding> třídy; v konfiguraci, použijte [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Ve výchozím nastavení tato vazba používá WS-Security (zabezpečení zprávy vrstvy).  
  
 Další informace najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, a <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Pokud žádná z vazeb poskytovaných systémem nesplňuje požadavky, můžete vytvořit vlastní vazby s element vazby zabezpečení vlastní. Další informace najdete v tématu [možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Možnosti vázání  
 V následující tabulce najdete Souhrn funkcí, které nabízí v nastavení režimu zabezpečení, to znamená, pokud režim zabezpečení je nastavený na vypíše dostupné funkce `Transport`, `Message`, nebo `TransportWithMessageCredential`. Pomocí této tabulky vám pomůže najít funkce zabezpečení, které vaše aplikace vyžaduje.  
  
|Nastavení|Funkce|  
|-------------|--------------|  
|Přenos|Ověřování serveru<br /><br /> Ověření klienta<br /><br /> Zabezpečení typu Point-to-Point<br /><br /> Interoperabilita<br /><br /> Hardwarová akcelerace<br /><br /> Vysoká propustnost<br /><br /> Zabezpečené brány firewall<br /><br /> Aplikace s vysokou latencí<br /><br /> Znova šifrovat napříč více segmentů směrování|  
|Zpráva|Ověřování serveru<br /><br /> Ověření klienta<br /><br /> Koncové zabezpečení<br /><br /> Interoperabilita<br /><br /> Deklarace identity ve formátu RTF<br /><br /> Federace<br /><br /> Vícefaktorové ověřování<br /><br /> Vlastní tokeny<br /><br /> Služba notář/časové razítko<br /><br /> Aplikace s vysokou latencí<br /><br /> Trvalost podpisy zpráv|  
|TransportWithMessageCredential|Ověřování serveru<br /><br /> Ověření klienta<br /><br /> Zabezpečení typu Point-to-Point<br /><br /> Interoperabilita<br /><br /> Hardwarová akcelerace<br /><br /> Vysoká propustnost<br /><br /> Deklarace identity vzhled plně funkčního klienta<br /><br /> Federace<br /><br /> Vícefaktorové ověřování<br /><br /> Vlastní tokeny<br /><br /> Zabezpečené brány firewall<br /><br /> Aplikace s vysokou latencí<br /><br /> Znova šifrovat napříč více segmentů směrování|  
  
 V následující tabulce jsou uvedeny vazby, které podporují různá nastavení režimu. Vyberte vazbu tabulky použít k vytvoření vašeho koncového bodu služby.  
  
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
  
## <a name="transport-credentials-in-bindings"></a>Přihlašovací údaje přenosu ve vazbách  
 V následující tabulce jsou uvedeny typy přihlašovacích údajů klienta, která je k dispozici při použití buď `BasicHttpBinding` nebo `WSHttpBinding` v režimu zabezpečení přenosu.  
  
|Type|Popis|  
|----------|-----------------|  
|Žádný|Určuje, že klient není potřeba k dispozici žádné přihlašovací údaje. Výsledkem je k anonymní klienta.|  
|Základní|Základní ověřování. Další informace najdete v tématu RFC 2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest, k dispozici na <https://go.microsoft.com/fwlink/?LinkId=84023>.|  
|ověřování algoritmem Digest|Ověřování algoritmem Digest. Další informace najdete v tématu RFC 2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest, k dispozici na <https://go.microsoft.com/fwlink/?LinkId=84023>.|  
|NTLM|NT LAN Manager (NTLM) authentication.|  
|Windows|Ověřování Windows.|  
|Certifikát|Ověřování provádí pomocí certifikátu.|  
|Třídy IssuedToken|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí tokenem vydaným službou tokenů zabezpečení nebo pomocí [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Další informace najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Přihlašovací údaje klienta zprávy ve vazbách  
 Následující tabulka uvádí typy přihlašovacích údajů klienta, která je k dispozici při použití vazby v režimu zabezpečení zpráv.  
  
|Type|Popis|  
|----------|-----------------|  
|Žádné|Umožňuje službě komunikovat s anonymní klienty.|  
|Windows|Umožňuje výměny zpráv SOAP podle ověřený kontext přihlašovacích údajů Windows.|  
|UserName|Umožňuje službě tak, aby vyžadovala, která klient ověřena pomocí pověření uživatelského jména. Všimněte si, že pokud režim zabezpečení je nastavený na `TransportWithMessageCredential`, WCF nepodporuje odeslání hesla hodnotou hash nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro režim zabezpečení zpráv. V důsledku toho WCF vynutí, že při použití uživatelských přihlašovacích údajů název je zabezpečený přenos.|  
|Certifikát|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu.|  
|Třídy IssuedToken|Umožňuje službě můžete zadat vlastní token služby tokenů zabezpečení.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Možnosti zabezpečení u vlastních vazeb](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Chování zabezpečení](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
