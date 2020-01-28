---
title: Výběr typu pověření
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 6737f7daeb37e2e296ca0429d73b963743c409a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746150"
---
# <a name="selecting-a-credential-type"></a>Výběr typu pověření
*Přihlašovací údaje* jsou pomocí služby data Windows Communication Foundation (WCF) navázány buď požadované identity, nebo schopnosti. Například Passport je přihlašovací údaje, které jsou státními záležitostmi k prokázání občanství v zemi nebo oblasti. V rámci WCF můžou přihlašovací údaje trvat mnoho forem, jako jsou tokeny uživatelských jmen a certifikáty X. 509. Toto téma popisuje přihlašovací údaje, jak se používají ve službě WCF a jak vybrat správné přihlašovací údaje pro vaši aplikaci.  
  
 V mnoha zemích a oblastech je licence ovladače příkladem přihlašovacích údajů. Licence obsahuje data, která představují identitu a možnosti osoby. Obsahuje důkaz o vlastnictví ve formě obrázku svého držitele. Licence je vydaná důvěryhodnou autoritou, obvykle státním oddělením licencí. Licence je zapečetěná a může obsahovat hologram, který ukazuje, že není úmyslně poškozen nebo padělaný.  
  
 Předložení přihlašovacích údajů zahrnuje prezentaci dat i kontrolu jejich držení. WCF podporuje různé typy přihlašovacích údajů na úrovni zabezpečení Transport i zpráva. Zvažte například dva typy přihlašovacích údajů, které podporuje WCF: uživatelské jméno a (X. 509) přihlašovací údaje certifikátu.  
  
 Pro přihlašovací údaje uživatelského jména představuje uživatelské jméno deklaraci identity a heslo poskytne důkaz o vlastnictví. Důvěryhodná autorita v tomto případě je systém, který ověřuje uživatelské jméno a heslo.  
  
 Pomocí přihlašovacích údajů certifikátu X. 509 se dá jako deklarace identity použít název subjektu, alternativní název subjektu nebo konkrétní pole v rámci certifikátu, zatímco další pole, jako jsou `Valid From` a `Valid To`, určují platnost certifikátu.  
  
## <a name="transport-credential-types"></a>Typy přenosových údajů  
 V následující tabulce jsou uvedeny možné typy přihlašovacích údajů klienta, které mohou být použity v rámci vazby v režimu zabezpečení přenosu. Při vytváření služby nastavte vlastnost `ClientCredentialType` na jednu z těchto hodnot, abyste určili typ přihlašovacích údajů, které musí klient zadat ke komunikaci s vaší službou. Můžete nastavit typy buď v kódu, nebo v konfiguračních souborech.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient nemusí prezentovat žádné přihlašovací údaje. To se týká anonymního klienta.|  
|Základní|Určuje základní ověřování pro klienta. Další informace najdete v tématu RFC2617 –[ověřování protokolu http: základní a ověřování algoritmem Digest](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|Otisk|Určuje ověřování algoritmem Digest pro klienta. Další informace najdete v tématu RFC2617 –[ověřování protokolu http: základní a ověřování algoritmem Digest](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|NTLM|Určuje ověřování v systému NT LAN Manager (NTLM). Tato část se používá, pokud z nějakého důvodu nemůžete použít ověřování pomocí protokolu Kerberos. Můžete ji také zakázat jako zálohu nastavením vlastnosti <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> na `false`, což způsobí, že služba WCF vyvolá výjimku, pokud se používá protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemusí bránit posílání přihlašovacích údajů protokolu NTLM po drátě.|  
|Windows|Určuje ověřování systému Windows. Chcete-li zadat pouze protokol Kerberos v doméně systému Windows, nastavte vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> na hodnotu `false` (výchozí hodnota je `true`).|  
|Certifikát|Provádí ověřování klientů pomocí certifikátu X. 509.|  
|Heslo|Uživatel musí zadávat uživatelské jméno a heslo. Ověřte dvojici uživatelského jména a hesla pomocí ověřování systému Windows nebo jiného vlastního řešení.|  
  
### <a name="message-client-credential-types"></a>Typy přihlašovacích údajů klienta zprávy  
 Následující tabulka uvádí možné typy přihlašovacích údajů, které můžete použít při vytváření aplikace, která používá zabezpečení zpráv. Tyto hodnoty můžete použít buď v kódu, nebo v konfiguračních souborech.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient nemusí prezentovat přihlašovací údaje. To se týká anonymního klienta.|  
|Windows|Umožňuje výměnu zpráv SOAP v rámci kontextu zabezpečení vytvořeného pomocí pověření systému Windows.|  
|Uživatelské jméno|Umožňuje službě, aby vyžadovala ověření klienta pomocí přihlašovacích údajů uživatelského jména. Všimněte si, že WCF nepovoluje žádné kryptografické operace s uživatelskými jmény, jako je například generování podpisu nebo šifrování dat. WCF zajišťuje zabezpečený přenos při použití přihlašovacích údajů uživatelského jména.|  
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu X. 509.|  
|Vydaný token|Vlastní typ tokenu konfigurovaný podle zásad zabezpečení. Výchozí typ tokenu je SAML (Security Assert Markup Language). Token je vydaný službou tokenů zabezpečení. Další informace najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Model vyjednávání pověření služby  
 *Vyjednávání* je proces navázání vztahu důvěryhodnosti mezi klientem a službou výměnou přihlašovacích údajů. Proces se provádí iterativním způsobem mezi klientem a službou, aby bylo možné zveřejnit pouze informace potřebné k dalšímu kroku procesu vyjednávání. V praxi je konečným výsledkem doručení přihlašovacích údajů služby klientovi, který se má použít v dalších operacích.  
  
 S jednou výjimkou jsou ve výchozím nastavení vazby poskytované systémem ve službě WCF vyjednávat pověření služby automaticky při použití zabezpečení na úrovni zprávy. (Výjimka je <xref:System.ServiceModel.BasicHttpBinding>, která ve výchozím nastavení nepovoluje zabezpečení.) Pokud chcete toto chování zakázat, přečtěte si téma vlastnosti <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A>.  
  
> [!NOTE]
> Když se zabezpečení SSL používá s .NET Framework 3,5 a novějším, používá klient WCF jak zprostředkující certifikáty v úložišti certifikátů, tak zprostředkující certifikáty přijaté během vyjednávání SSL k provedení ověření řetězu certifikátů na úrovni služby. certifikát. .NET Framework 3,0 používá pouze zprostředkující certifikáty nainstalované v místním úložišti certifikátů.  
  
#### <a name="out-of-band-negotiation"></a>Vzdálené vyjednávání  
 Pokud je automatické vyjednávání zakázané, musí se přihlašovací údaje služby zřídit v klientovi předtím, než se odešlou zprávy do služby. Tato možnost se označuje také jako *vzdálené* zřizování. Pokud je například zadaný typ přihlašovacích údajů certifikát a automatické vyjednávání je zakázané, musí se klient obrátit na vlastníka služby a přijmout a nainstalovat certifikát na počítači, na kterém je spuštěná klientská aplikace. To se dá udělat například v případě, že chcete přesně určit, kteří klienti budou mít přístup ke službě ve scénáři Business-to-Business. Toto vzdálené vyjednávání se dá provést v e-mailu a certifikát X. 509 je uložený v úložišti certifikátů Windows pomocí nástroje, jako je modul snap-in Certifikáty konzoly MMC (Microsoft Management Console).  
  
> [!NOTE]
> Vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> slouží k poskytování služby s certifikátem, který byl dosažen prostřednictvím vzdáleného vyjednávání. To je nezbytné při použití třídy <xref:System.ServiceModel.BasicHttpBinding>, protože vazba nepovoluje automatizované vyjednávání. Tato vlastnost se používá také v nerelačním scénáři. Jedná se o scénář, kdy server pošle klientovi zprávu, aniž by musela nejdřív odeslat požadavek na server. Vzhledem k tomu, že server nemá požadavek od klienta, musí použít certifikát klienta k zašifrování zprávy klientovi.  
  
## <a name="setting-credential-values"></a>Nastavení hodnot přihlašovacích údajů  
 Po výběru režimu zabezpečení musíte zadat vlastní přihlašovací údaje. Pokud je například typ přihlašovacích údajů nastavený na "certifikát", musíte ke službě nebo klientovi přidružit konkrétní přihlašovací údaje (třeba konkrétní certifikát X. 509).  
  
 V závislosti na tom, jestli programujete službu nebo klienta, se metoda nastavení hodnoty přihlašovacích údajů mírně liší.  
  
### <a name="setting-service-credentials"></a>Nastavování přihlašovacích údajů služby  
 Pokud používáte transportní režim a jako přenos používáte protokol HTTP, musíte použít buď Internetová informační služba (IIS), nebo nakonfigurovat port s certifikátem. Další informace najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) a [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pokud chcete zřídit službu s přihlašovacími údaji v kódu, vytvořte instanci třídy <xref:System.ServiceModel.ServiceHost> a určete příslušné přihlašovací údaje pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třídy, ke kterým se dostanete prostřednictvím vlastnosti <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.  
  
#### <a name="setting-a-certificate"></a>Nastavení certifikátu  
 Pokud chcete zřídit službu s certifikátem X. 509, který se má použít k ověření služby pro klienty, použijte metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> třídy <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>.  
  
 Chcete-li zřídit službu s klientským certifikátem, použijte metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> třídy <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>.  
  
#### <a name="setting-windows-credentials"></a>Nastavení přihlašovacích údajů systému Windows  
 Pokud klient zadá platné uživatelské jméno a heslo, použije se k ověření klienta přihlašovací údaje. V opačném případě se použijí přihlašovací údaje aktuálně přihlášeného uživatele.  
  
### <a name="setting-client-credentials"></a>Nastavování přihlašovacích údajů klienta  
 V rámci WCF klientské aplikace používají pro připojení ke službám klienta WCF. Každý klient je odvozen z třídy <xref:System.ServiceModel.ClientBase%601> a vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> na straně klienta umožňuje specifikaci různých hodnot přihlašovacích údajů klienta.  
  
#### <a name="setting-a-certificate"></a>Nastavení certifikátu  
 Chcete-li zřídit službu s certifikátem X. 509, který slouží k ověření klienta ke službě, použijte metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> třídy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Způsob použití přihlašovacích údajů klienta k ověření klienta ke službě  
 Informace o přihlašovacích údajích klienta požadovaných ke komunikaci se službou jsou k dispozici pomocí vlastnosti <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> nebo vlastnosti <xref:System.ServiceModel.ChannelFactory.Credentials%2A>. Kanál zabezpečení používá tyto informace k ověření klienta ke službě. Ověřování se provádí prostřednictvím jednoho ze dvou režimů:  
  
- Pověření klienta se používají před odesláním první zprávy pomocí instance klienta služby WCF pro vytvoření kontextu zabezpečení. Všechny zprávy aplikace jsou poté zabezpečeny prostřednictvím kontextu zabezpečení.  
  
- Pověření klienta slouží k ověření každé zprávy aplikace odeslané službě. V takovém případě není mezi klientem a službou vytvořen žádný kontext.  
  
### <a name="established-identities-cannot-be-changed"></a>Zavedené identity nelze změnit.  
 Při použití první metody je vytvořený kontext trvale přidružen k identitě klienta. To znamená, že jakmile je kontext zabezpečení vytvořen, nelze změnit identitu přidruženou k klientovi.  
  
> [!IMPORTANT]
> Je potřeba vědět, kdy identitu nejde přepnout (to znamená, že při navazování kontextu zabezpečení je výchozí chování). Pokud vytvoříte službu, která komunikuje s druhou službou, nelze změnit identitu použitou k otevření klienta služby WCF pro druhou službu. Tato chyba se může nacházet v případě, že více klientů smí používat první službu a služba zosobňuje klienty při přístupu k druhé službě. Pokud služba znovu používá stejného klienta pro všechny volající, všechna volání druhé služby se provádějí v rámci identity prvního volajícího, který se použil k otevření klienta pro druhou službu. Jinými slovy, služba používá identitu prvního klienta, aby všichni klienti komunikovali s druhou službou. To může vést ke zvýšení oprávnění. Pokud se nejedná o požadované chování vaší služby, musíte sledovat každého volajícího a vytvořit nového klienta k druhé službě pro každého jiného volajícího a zajistit, aby služba používala správného klienta pro správného volajícího, aby komunikoval s druhou službou.  
  
 Další informace o přihlašovacích údajích a zabezpečených relacích najdete v tématu [požadavky na zabezpečení pro zabezpečené relace](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
