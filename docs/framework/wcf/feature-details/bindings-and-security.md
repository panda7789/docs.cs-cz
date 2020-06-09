---
title: Vazby a zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 0c41f357d63158979e448c2cc36f1e80b74b18d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587505"
---
# <a name="bindings-and-security"></a>Vazby a zabezpečení

Vazby poskytnuté systémem, které jsou součástí Windows Communication Foundation (WCF), nabízejí rychlý způsob, jak programovat aplikace WCF. S jednou výjimkou mají všechny vazby povolené výchozí schéma zabezpečení. Toto téma vám pomůže vybrat správnou vazbu pro vaše požadavky na zabezpečení.

Přehled zabezpečení služby WCF najdete v tématu [Přehled zabezpečení](security-overview.md). Další informace o programování WCF pomocí vazeb naleznete v tématu [PROGRAMMING WCF Security](programming-wcf-security.md).

Pokud jste již vybrali vazbu, můžete získat další informace o chování za běhu, které jsou spojeny se zabezpečením v [bezpečnostním chování](security-behaviors-in-wcf.md).

Některé funkce zabezpečení nejsou programovatelné pomocí vazeb poskytovaných systémem. Další ovládací prvky s použitím vlastní vazby najdete v tématu [Možnosti zabezpečení s vlastními](security-capabilities-with-custom-bindings.md)vazbami.

## <a name="security-functions-of-bindings"></a>Funkce zabezpečení vazeb

WCF zahrnuje řadu vazeb poskytovaných systémem, které splňují nejvíc potřeb. Pokud konkrétní vazba nestačí, můžete také vytvořit vlastní vazbu. Seznam vazeb poskytovaných systémem naleznete v tématu [systémové vazby](../system-provided-bindings.md). Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../extending/custom-bindings.md).

Každá vazba ve službě WCF má dvě formy: jako rozhraní API a jako XML element použitý v konfiguračním souboru. Například `WSHttpBinding` (rozhraní API) má protějšek v [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .

V následující části jsou uvedeny obě formy pro každou vazbu a jsou shrnuty funkce zabezpečení.

### <a name="basichttp"></a>BasicHttp

V kódu použijte <xref:System.ServiceModel.BasicHttpBinding> třídu; v konfiguraci použijte [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) .

Tato vazba je navržená pro použití s řadou existujících technologií, včetně následujících:

- ASP.NET Web Services (ASMX), verze 1.

- Aplikace pro vylepšení webových služeb (WSE).

- Základní profil definovaný ve specifikaci interoperability webových služeb (WS-I) ( <https://go.microsoft.com/fwlink/?LinkId=38955> ).

- Základní profil zabezpečení definovaný v WS-I.

Ve výchozím nastavení tato vazba není zabezpečená. Je navržená tak, aby spolupracovala se službami ASMX. Je-li zabezpečení povoleno, je vazba navržena pro bezproblémové meziprovozu s mechanismy zabezpečení Internetová informační služba (IIS), jako je základní ověřování, Digest a integrované zabezpečení systému Windows. Další informace najdete v tématu [Přehled zabezpečení přenosu](transport-security-overview.md). Tato vazba podporuje následující:

- Zabezpečení přenosu HTTPS.

- Základní ověřování HTTP.

- WS-Security.

Další informace naleznete v tématech <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType> a <xref:System.ServiceModel.BasicHttpSecurityMode>.

### <a name="wshttpbinding"></a>WSHttpBinding

V kódu použijte <xref:System.ServiceModel.WSHttpBinding> třídu; v konfiguraci použijte [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .

Ve výchozím nastavení tato vazba implementuje specifikaci WS-Security a poskytuje interoperabilitu se službami, které implementují specifikace WS-*. Podporuje následující:

- Zabezpečení přenosu HTTPS.

- WS-Security.

- Ochrana přenosu HTTPS se zabezpečením přihlašovacích údajů zprávy SOAP pro ověřování volajícího.

Další informace naleznete v tématech <xref:System.ServiceModel.WSHttpSecurity> , <xref:System.ServiceModel.MessageSecurityOverHttp> , <xref:System.ServiceModel.MessageCredentialType> , <xref:System.ServiceModel.SecurityMode> , <xref:System.ServiceModel.HttpTransportSecurity> , <xref:System.ServiceModel.HttpClientCredentialType> a <xref:System.ServiceModel.HttpProxyCredentialType> .

### <a name="wsdualhttpbinding"></a>WSDualHttpBinding

V kódu použijte <xref:System.ServiceModel.WSDualHttpBinding> třídu; v konfiguraci použijte [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) .

Tato vazba je navržena tak, aby umožňovala duplexní aplikace služby. Tato vazba implementuje specifikace WS-Security pro zabezpečení přenosu založeného na zprávách. Zabezpečení přenosu není k dispozici. Ve výchozím nastavení nabízí tyto funkce:

- Implementuje pro spolehlivost zasílání zpráv WS-Reliable.

- Implementuje protokol WS-Security pro přenos zabezpečení a ověřování.

- Pro doručování zpráv používá protokol HTTP.

- Používá kódování textu nebo zprávy XML.

 Pomocí protokolu WS-Security (Message-Layer Security) vám vazba umožňuje konfigurovat následující parametry:

- Sada algoritmů zabezpečení pro určení kryptografického algoritmu.

- Možnosti vazby pro následující:

  - Poskytování přihlašovacích údajů služby v klientovi, které jsou k dispozici vzdáleně.

  - Poskytování přihlašovacích údajů služby vyjednaných ze služby jako součást nastavení kanálu.

Další informace naleznete v tématech <xref:System.ServiceModel.WSDualHttpSecurity> a <xref:System.ServiceModel.WSDualHttpSecurityMode>.

### <a name="nettcpbinding"></a>NetTcpBinding

V kódu použijte <xref:System.ServiceModel.NetTcpBinding> třídu; v konfiguraci použijte [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) .

Tato vazba je optimalizovaná pro komunikaci mezi počítači. Ve výchozím nastavení má následující vlastnosti:

- Implementuje zabezpečení transportní vrstvy.

- Využívá zabezpečení systému Windows k přenosu zabezpečení a ověřování.

- Používá protokol TCP pro přenos.

- Implementuje kódování binární zprávy.

- Implementuje zasílání zpráv WS-Reliable.

Mezi tyto možnosti patří:

- Zabezpečení vrstvy zpráv (pomocí WS-Security).

- Zabezpečení přenosu s přihlašovacími údaji ke zprávě – důvěrnost a integrita poskytovaná protokolem TLS (Transport Layer Security) prostřednictvím TCP a přihlašovací údaje k autorizaci poskytované WS-Security.

Další informace naleznete v tématech <xref:System.ServiceModel.NetTcpSecurity> , <xref:System.ServiceModel.TcpTransportSecurity> , <xref:System.ServiceModel.TcpClientCredentialType> , <xref:System.ServiceModel.MessageSecurityOverTcp> a <xref:System.ServiceModel.MessageCredentialType> .

### <a name="netnamedpipebinding"></a>NetNamedPipeBinding

V kódu použijte <xref:System.ServiceModel.NetNamedPipeBinding> třídu; v konfiguraci použijte [\<netNamedPipeBinding>](../../configure-apps/file-schema/wcf/netnamedpipebinding.md) .

Tato vazba je optimalizovaná pro komunikaci mezi procesy (obvykle na stejném počítači). Ve výchozím nastavení má tato vazba následující vlastnosti:

- Používá zabezpečení přenosu pro přenos a ověřování zpráv.

- Pro doručování zpráv používá pojmenované kanály.

- Implementuje kódování binární zprávy.

- Šifrování a podepisování zpráv.

Mezi tyto možnosti patří:

- Ověřování pomocí zabezpečení systému Windows.

Další informace najdete v tématech <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode> a <xref:System.ServiceModel.NamedPipeTransportSecurity>.

### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding

V kódu použijte <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídu; v konfiguraci použijte [\<msmqIntegrationBinding>](../../configure-apps/file-schema/wcf/msmqintegrationbinding.md) .

Tato vazba je optimalizovaná pro vytváření klientů a služeb WCF, které spolupracují s koncovými body služby Řízení front zpráv (MSMQ) bez WCF.

Ve výchozím nastavení používá tato vazba zabezpečení přenosu a poskytuje následující bezpečnostní charakteristiky:

- Zabezpečení je možné zakázat (žádné).

- Zabezpečení přenosu MSMQ (přenos).

Další informace naleznete v tématech <xref:System.ServiceModel.NetMsmqSecurity> a <xref:System.ServiceModel.NetMsmqSecurityMode>.

### <a name="netmsmqbinding"></a>NetMsmqBinding

V kódu použijte <xref:System.ServiceModel.NetMsmqBinding> třídu; v konfiguraci použijte [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) .

Tato vazba je určená pro použití při vytváření služeb WCF, které vyžadují podporu zpráv ve frontě MSMQ.

Ve výchozím nastavení používá tato vazba zabezpečení přenosu a poskytuje následující bezpečnostní charakteristiky:

- Zabezpečení je možné zakázat (žádné).

- Zabezpečení přenosu MSMQ (přenos).

- Zabezpečení zpráv založené na protokolu SOAP (zpráva).

- Současná přenosová a zabezpečená zabezpečení zpráv (obojí).

- Podporované typy přihlašovacích údajů klienta: žádné, Windows, UserName, Certificate, třídy IssuedToken.

<xref:System.ServiceModel.MessageCredentialType.Certificate>Přihlašovací údaje jsou podporovány pouze v případě, že je režim zabezpečení nastaven na hodnotu <xref:System.ServiceModel.NetMsmqSecurityMode.Both> nebo <xref:System.ServiceModel.NetMsmqSecurityMode.Message> .

Další informace naleznete v tématech <xref:System.ServiceModel.MessageSecurityOverMsmq> a <xref:System.ServiceModel.MsmqTransportSecurity>.

### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding

V kódu použijte <xref:System.ServiceModel.WSFederationHttpBinding> třídu; v konfiguraci použijte [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .

Ve výchozím nastavení používá tato vazba protokol WS-Security (zabezpečení vrstvy zpráv).

Další informace najdete v tématu [federace](federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity> a <xref:System.ServiceModel.WSFederationHttpSecurityMode> .

## <a name="custom-bindings"></a>Vlastní vazby

Pokud žádná z vazeb poskytovaných systémem nesplňuje požadavky, můžete vytvořit vlastní vazbu s vlastním prvkem vazby zabezpečení. Další informace najdete v tématu [Možnosti zabezpečení s vlastními vazbami](security-capabilities-with-custom-bindings.md).

## <a name="binding-choices"></a>Volby vazby

Následující tabulka shrnuje funkce nabízené v nastavení režim zabezpečení, to znamená, že uvádí funkce, které jsou k dispozici, když je režim zabezpečení nastavený na `Transport` , `Message` nebo `TransportWithMessageCredential` . Tato tabulka vám umožní najít funkce zabezpečení, které vaše aplikace vyžaduje.

|Nastavení|Funkce|
|-------------|--------------|
|Přenos|Ověření serveru<br /><br /> Ověření klienta<br /><br /> Zabezpečení Point-to-Point<br /><br /> Interoperabilita<br /><br /> Hardwarová akcelerace<br /><br /> Vysoká propustnost<br /><br /> Zabezpečená brána firewall<br /><br /> Aplikace s vysokou latencí<br /><br /> Opětovné šifrování napříč několika segmenty směrování|
|Zpráva|Ověření serveru<br /><br /> Ověření klienta<br /><br /> Komplexní zabezpečení<br /><br /> Interoperabilita<br /><br /> Bohatá deklarace identity<br /><br /> metadata<br /><br /> Vícefaktorové ověřování<br /><br /> Vlastní tokeny<br /><br /> Služba notář/časové razítko<br /><br /> Aplikace s vysokou latencí<br /><br /> Trvalost signatur zpráv|
|TransportWithMessageCredential|Ověření serveru<br /><br /> Ověření klienta<br /><br /> Zabezpečení Point-to-Point<br /><br /> Interoperabilita<br /><br /> Hardwarová akcelerace<br /><br /> Vysoká propustnost<br /><br /> Plně funkční deklarace klientů<br /><br /> metadata<br /><br /> Vícefaktorové ověřování<br /><br /> Vlastní tokeny<br /><br /> Zabezpečená brána firewall<br /><br /> Aplikace s vysokou latencí<br /><br /> Opětovné šifrování napříč několika segmenty směrování|

Následující tabulka uvádí vazby, které podporují různá nastavení režimu. Vyberte vazbu z tabulky, kterou chcete použít k vytvoření koncového bodu služby.

|Vazba|Podpora transportního režimu|Podpora režimu zpráv|Podpora TransportWithMessageCredential|
|-------------|----------------------------|--------------------------|--------------------------------------------|
|`BasicHttpBinding`|Ano|Ano|Ano|
|`WSHttpBinding`|Ano|Ano|Ano|
|`WSDualHttpBinding`|No|Yes|No|
|`NetTcpBinding`|Ano|Ano|Ano|
|`NetNamedPipeBinding`|Ano|Ne|No|
|`NetMsmqBinding`|Ano|Ano|No|
|`MsmqIntegrationBinding`|Yes|Ne|Ne|
|`wsFederationHttpBinding`|No|Ano|Ano|

## <a name="transport-credentials-in-bindings"></a>Přihlašovací údaje pro přenos ve vazbách

Následující tabulka uvádí typy přihlašovacích údajů klienta, které jsou k dispozici při použití `BasicHttpBinding` nebo `WSHttpBinding` v režimu zabezpečení přenosu.

|Typ|Popis|
|----------|-----------------|
|Žádné|Určuje, že klient nemusí prezentovat žádné přihlašovací údaje. To se týká anonymního klienta.|
|Basic|Základní ověřování. Další informace najdete v dokumentu RFC 2617 – ověřování HTTP: základní a ověřování algoritmem Digest, dostupné na adrese <https://go.microsoft.com/fwlink/?LinkId=84023> .|
|Otisk|Ověřování hodnotou hash. Další informace najdete v dokumentu RFC 2617 – ověřování HTTP: základní a ověřování algoritmem Digest, dostupné na adrese <https://go.microsoft.com/fwlink/?LinkId=84023> .|
|NTLM|Ověřování NT LAN Manager (NTLM).|
|Windows|Ověřování systému Windows.|
|Certifikát|Ověřování provedeno pomocí certifikátu.|
|Třídy IssuedToken|Umožňuje službě, aby vyžadovala ověření klienta pomocí tokenu vydaného službou tokenu zabezpečení nebo službou CardSpace. Další informace najdete v tématu [federace a vystavené tokeny](federation-and-issued-tokens.md).|

### <a name="message-client-credentials-in-bindings"></a>Přihlašovací údaje klienta zprávy ve vazbách

V následující tabulce jsou uvedeny typy přihlašovacích údajů klienta, které jsou k dispozici při použití vazby v režimu zabezpečení zprávy.

|Typ|Popis|
|----------|-----------------|
|Žádné|Umožňuje službě interakci s anonymními klienty.|
|Windows|Povoluje výměnu zpráv SOAP pod ověřeným kontextem pověření systému Windows.|
|UserName|Umožňuje službě, aby vyžadovala ověření klienta pomocí pověření uživatelského jména. Všimněte si, že pokud je režim zabezpečení nastaven na hodnotu `TransportWithMessageCredential` , WCF nepodporuje odeslání výtahu hesla nebo odvození klíče pomocí hesla a použití takových klíčů pro zabezpečení režimu zpráv. Technologie WCF proto vynutila, že při použití přihlašovacích údajů uživatelského jména je přenos zabezpečený.|
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu.|
|Třídy IssuedToken|Umožňuje službě používat službu tokenů zabezpečení k poskytnutí vlastního tokenu.|

## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](security-overview.md)
- [Zabezpečení služeb a klientů](securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](selecting-a-credential-type.md)
- [Možnosti zabezpečení u vlastních vazeb](security-capabilities-with-custom-bindings.md)
- [Chování zabezpečení](security-behaviors-in-wcf.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
