---
title: Výběr typu pověření
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 756017462ccaf8a555b0634e8a43cfdd3bc63d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="selecting-a-credential-type"></a>Výběr typu pověření
*Přihlašovací údaje* jsou data Windows Communication Foundation (WCF) používá k navázání uváděné identity nebo funkce. Passport je například přihlašovací údaje, které government problémy k prokázání přístupem v zemi nebo oblasti. Ve službě WCF přihlašovací údaje mohou mít mnoho forem, jako je například uživatelské jméno tokeny a certifikáty X.509. Toto téma popisuje přihlašovací údaje, jak se používají ve WCF a jak vybrat správné přihlašovací údaje pro vaši aplikaci.  
  
 V mnoha jiných zemí a oblastí licence ovladače je příkladem pověření. Licence obsahuje data, která představuje identitu uživatele a možnosti. Obsahuje důkaz vlastnictví ve formě obrázku vlastník. Licence je vydán důvěryhodnou autoritou, většinou vládních oddělení licencování. Licence je zapečetěná a může obsahovat hologram, zobrazující, že nebyla manipulováno nebo padělat.  
  
 Prezentace pověření zahrnuje prezentací data a ověření vlastní data. WCF podporuje celou řadu typů přihlašovacích údajů při přepravě a zpráva úrovně zabezpečení. Představte si třeba dva typy přihlašovacích údajů, které jsou podporovány ve WCF: uživatelské jméno a (X.509) certifikát přihlašovacích údajů.  
  
 Pro název přihlašovací údaje uživatele uživatelské jméno představuje deklarovaná identita a heslo zajišťuje důkazy o u sebe. Jako důvěryhodnou autoritu v tomto případě je systém, který ověří uživatelské jméno a heslo.  
  
 Pomocí pověření certifikátu X.509, názvu subjektu, alternativní název subjektu nebo v konkrétních polí v rámci certifikát lze použít jako deklarace identity, při další pole, jako `Valid From` a `Valid To` pole, zadejte jeho platnost certifikát.  
  
## <a name="transport-credential-types"></a>Typy přenosu přihlašovacích údajů  
 Následující tabulka uvádí možné typy pověření klienta, které mohou být využívána vazbu v režimu zabezpečení přenosu. Při vytváření služby, nastavte `ClientCredentialType` vlastnost na jednu z těchto hodnot pro určení typu pověření, které klient musíte dodávat ke komunikaci s vaší služby. Typy můžete nastavit v kódu nebo konfiguračního souboru.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient nemusí k dispozici žádné pověření. Výsledkem anonymním klientem.|  
|Základní|Určuje základní ověřování pro klienta. Další informace najdete v tématu RFC2617 –[ověřování protokolu HTTP: Basic a ověřování algoritmem Digest](http://go.microsoft.com/fwlink/?LinkID=88313).|  
|Ověřování algoritmem Digest|Určuje, ověřování hodnotou hash pro klienta. Další informace najdete v tématu RFC2617 –[ověřování protokolu HTTP: Basic a ověřování algoritmem Digest](http://go.microsoft.com/fwlink/?LinkID=88313).|  
|NTLM|Určuje NT LAN Manager (NTLM) authentication. To se používá, pokud z nějakého důvodu nelze použít ověřování pomocí protokolu Kerberos. Můžete také zakázat jeho použití jako zálohu nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> vlastnost `false`, což způsobí, že WCF aby best effort vyvolá výjimku, pokud se používá protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemusí zabránit odesílány prostřednictvím sítě pověření NTLM.|  
|Windows|Určuje ověřování systému Windows. Chcete-li zadat pouze protokol Kerberos v doméně systému Windows, nastavte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> vlastnost `false` (výchozí hodnota je `true`).|  
|certifikát|Provede ověření klienta pomocí certifikátu X.509.|  
|Heslo|Uživatel musí zadat uživatelské jméno a heslo. Ověření dvojici jméno a heslo uživatele pomocí ověřování systému Windows nebo jiné vlastní řešení.|  
  
### <a name="message-client-credential-types"></a>Typy zpráv klienta přihlašovacích údajů  
 V následující tabulce jsou uvedeny typy možné přihlašovacích údajů, které můžete použít při vytvoření aplikace, která používá zabezpečení zpráv. Můžete použít tyto hodnoty v kódu nebo konfiguračního souboru.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient nemusí pověření k dispozici. Výsledkem anonymním klientem.|  
|Windows|Umožňuje výměny zpráv protokolu SOAP proběhnout v kontextu zabezpečení vytvořených pomocí pověření systému Windows.|  
|Uživatelské jméno|Umožňuje službě tak, aby vyžadovala ověření klienta s názvem pověření uživatele. Všimněte si, že všechny kryptografické operace s uživatelskými jmény, například generování podpis nebo šifrování dat není povoleno WCF. WCF zajistí, že při použití přihlašovací údaje uživatele název zabezpečené přenosu.|  
|certifikát|Umožňuje službě vyžadují, ověření klienta pomocí certifikátu X.509.|  
|Vydané tokenu|Vlastní token typ nakonfigurovaný podle zásady zabezpečení. Výchozí typ tokenu je zabezpečení kontrolní výrazy Markup Language (SAML). Token je vydaný služby tokenu zabezpečení. Další informace najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Model vyjednávání pověření služby  
 *Vyjednávání* je proces vytvoření vztahu důvěryhodnosti mezi sebou klient a služba nahrazením přihlašovací údaje. Proces je provést opakované mezi klientem a službu, která zveřejnit pouze informace potřebné pro další krok v procesu vyjednávání. V praxi konečný výsledek je doručování služby pověření klienta, který se má použít v další operacích.  
  
 S jednou výjimkou ve výchozím nastavení vazby poskytované systémem ve WCF vyjednávat přihlašovací údaje služby automaticky při použití zabezpečení na úrovni zpráv. (Výjimkou je <xref:System.ServiceModel.BasicHttpBinding>, který není povolen zabezpečení ve výchozím nastavení.) Chcete-li toto chování zakázat, přečtěte si téma <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnosti.  
  
> [!NOTE]
>  Použijete zabezpečení SSL v rozhraní .NET Framework 3.5 a později klienta WCF pomocí zprostředkující certifikáty v úložišti certifikátů i zprostředkující certifikáty obdržel během vyjednávání SSL k ověření řetězu certifikátů se službou provést certifikát. Rozhraní .NET framework 3.0 používá jenom nainstalovaná v místním úložišti certifikátů zprostředkující certifikáty.  
  
#### <a name="out-of-band-negotiation"></a>Out-of-Band vyjednávání  
 Pokud je zakázáno automatické vyjednávání, přihlašovací údaje služby musí být zřízená na straně klienta před odesláním všechny zprávy ve službě. To je také označován jako *out-of-band* zřizování. Například pokud typ zadané přihlašovací údaje je certifikát, a je zakázáno automatické vyjednávání, klient musí požádejte vlastníka služby přijímat a nainstalujte certifikát na počítači se systémem klientské aplikace. To lze provést, například, pokud chcete výhradně řídit, které klienti mají přístup k službě ve scénáři business-to-business. Tento out z – vzdálené vyjednávání lze provést v e-mailu a certifikát X.509 je uložen v úložišti certifikátů systému Windows, pomocí nástroje, jako je modul snap-in Certifikáty konzoly Microsoft Management Console (MMC).  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Vlastnost slouží k poskytování služby certifikátem, který bylo dosaženo pomocí out-of-band vyjednávání. To je nezbytné při použití <xref:System.ServiceModel.BasicHttpBinding> třídy, protože vazba neumožňuje automatizované vyjednávání. Vlastnost se také používá ve scénáři s bez korelace nejsou duplexní. Jedná o scénář, kde server odešle zprávu do klienta bez nutnosti klient nejdřív odeslat požadavek na server. Protože server nemá požadavek od klienta, musí používat certifikát klienta pro šifrování zprávy do klienta.  
  
## <a name="setting-credential-values"></a>Hodnoty nastavení přihlašovacích údajů  
 Jakmile vyberete režim zabezpečení, je nutné zadat skutečné přihlašovací údaje. Například pokud typ přihlašovacích údajů je nastavena na "certifikátu", pak je třeba přidružit konkrétní přihlašovací údaje (například konkrétní certifikátu X.509) služba nebo klienta.  
  
 V závislosti na tom, jestli jsou programování služby nebo klienta metoda pro nastavení hodnoty přihlašovacích údajů se mírně liší.  
  
### <a name="setting-service-credentials"></a>Nastavení pověření služby  
 Pokud používáte režim přenosu a používáte protokol HTTP jako přenos, musíte použít buď Internetové informační služby (IIS) nebo port konfigurovat pomocí certifikátu. Další informace najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) a [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Ke zřízení služby s přihlašovacími údaji v kódu, vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy a zadejte příslušná pověření pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třída, přistupovat prostřednictvím <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.  
  
#### <a name="setting-a-certificate"></a>Nastavení certifikátu  
 Chcete-li zřídit službu společně s certifikátem X.509, který se má použít k ověřování klientů, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> – třída.  
  
 Chcete-li zřizovat služby pomocí certifikátu klienta, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> – třída.  
  
#### <a name="setting-windows-credentials"></a>Nastavení přihlašovacích údajů systému Windows  
 Pokud klient Určuje platné uživatelské jméno a heslo, že pověření se používá k ověření klienta. Jinak jsou použita pověření aktuálního přihlášeného uživatele.  
  
### <a name="setting-client-credentials"></a>Nastavení přihlašovacích údajů klienta  
 Ve službě WCF klienta aplikací připojit ke službám pomocí klienta WCF. Každý klient je odvozena z <xref:System.ServiceModel.ClientBase%601> třída a <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost na klientovi umožňuje specifikaci různých hodnot pověření klienta.  
  
#### <a name="setting-a-certificate"></a>Nastavení certifikátu  
 Chcete-li zřídit službu společně s certifikátem X.509, který se používá k ověření klienta pro službu, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> – třída.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Jak pověření klienta slouží k ověření klienta ke službě  
 Poskytuje informace o pověření klienta vyžadované pro komunikaci se službou buď pomocí <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnost. Zabezpečený kanál používá tuto informaci k ověřování klienta ke službě. Ověřování se provádí prostřednictvím jednoho ze dvou režimů:  
  
-   Pověření klienta jsou použity jednou před odesláním první zprávu pomocí instance klienta WCF vytvoření kontextu zabezpečení. Všechny zprávy aplikace jsou pak zabezpečené skrze kontext zabezpečení.  
  
-   Pověření klienta slouží k ověření všechny aplikace zprávy odeslané do služby. V takovém případě je mezi klientem a službu navázat žádný kontext.  
  
### <a name="established-identities-cannot-be-changed"></a>Zavedené identity nelze změnit.  
 Pokud je použita první metoda, zavedených kontextu je trvale přidružen je identita klienta. To znamená po vytvoření kontext zabezpečení nelze změnit identitu přidruženou ke klientovi.  
  
> [!IMPORTANT]
>  Je situaci znát při nelze přepnout identity (to znamená, když vytvoření zabezpečení kontext je na výchozí chování). Pokud vytvoříte službu, která komunikuje s druhou služby, nelze změnit identitu použitý k otevření klienta WCF na službu druhý. Pokud je povoleno více klientů používat první službu a službu zosobňuje klienti při přístupu ke službě druhý to všechno bude problém. Pokud službu znovu použije stejného klienta pro všechny volající, všechna volání do druhé služby hotovi s identitou první volající, který byl použitý k otevření klienta ke službě druhý. Jinými slovy služba používá identity první klienta pro všechny jeho klienty komunikovat se službou druhý. To může vést ke zvýšení úrovně oprávnění. Pokud není toto chování žádoucí vaší služby, musíte sledovat každou volajícího a vytvořit nového klienta ke službě druhý pro každý odlišné volajícího a zajistit, aby používal službu pouze správné klienta pro správné volající komunikovat se službou druhý.  
  
 Další informace o pověření a zabezpečených relací najdete v tématu [důležité informace o zabezpečení pro zabezpečené relace](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>  
 [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
