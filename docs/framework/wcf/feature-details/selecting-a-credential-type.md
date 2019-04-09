---
title: Výběr typu pověření
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 8aa959aa952e839039bebffddddd951fbc1eb0d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167840"
---
# <a name="selecting-a-credential-type"></a>Výběr typu pověření
*Přihlašovací údaje* jsou data Windows Communication Foundation (WCF) používá k navázání uváděné identity nebo funkce. Passport je například přihlašovací údaje, které státní instituce problémy prokázání citizenship v zemi nebo oblast. Ve službě WCF přihlašovací údaje mohou mít mnoho forem, jako je například název tokeny uživatele a certifikáty X.509. Toto téma popisuje přihlašovací údaje, jak se používají v WCF a tom, jak vybrat správné přihlašovací údaje pro vaše aplikace.  
  
 V mnoha zemích a oblastech licence ovladače je příkladem přihlašovacích údajů. Licence obsahuje data, která představuje identitu uživatele a možnosti. Obsahuje doklad o vlastnictví v podobě obrázku vlastníka. Licence je vydán důvěryhodnou autoritou, obvykle vládní oddělení licencování. Licence je zapečetěná a může obsahovat hologram, zobrazuje, že nebyla úmyslně nebo padělat.  
  
 Zobrazení přihlašovacích údajů zahrnuje prezentace dat i doklad o vlastnictví dat. WCF podporuje celou řadu typů přihlašovacích údajů při přenosu i zpráva úrovně zabezpečení. Představte si třeba dva typy přihlašovacích údajů, které jsou podporované ve službě WCF: uživatelské jméno a (X.509) certifikát přihlašovacích údajů.  
  
 Pro přístupové uživatelské jméno uživatelské jméno představuje nárokován identitu a heslo zajišťuje důkazy o vlastnictví. Jako důvěryhodnou autoritu v tomto případě je systém, který ověří uživatelské jméno a heslo.  
  
 S přihlašovacími údaji pro certifikát X.509, název subjektu nebo alternativní název subjektu konkrétních polí v rámci certifikát může sloužit jako deklarace identity, zatímco jiné polí, jako `Valid From` a `Valid To` pole, zadejte jeho platnost certifikát.  
  
## <a name="transport-credential-types"></a>Typy přenosu přihlašovacích údajů  
 Následující tabulka uvádí možné typy přihlašovacích údajů klienta, které mohou být využívána vazbu v režim zabezpečení transport. Při vytváření služby, nastavte `ClientCredentialType` vlastnost na jednu z těchto hodnot k určení typu přihlašovacích údajů, které klient musíte dodávat ke komunikaci s vaší službou. Typy lze nastavit v kódu nebo konfiguračního souboru.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádné|Určuje, že klient není potřeba k dispozici žádné přihlašovací údaje. Výsledkem je k anonymní klienta.|  
|Základní|Určuje základní ověřování klienta. Další informace najdete v tématu RFC2617 –[ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|ověřování algoritmem Digest|Určuje ověřování algoritmem digest pro klienta. Další informace najdete v tématu RFC2617 –[ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|Ntlm|Určuje NT LAN Manager (NTLM) authentication. Používá se, pokud z nějakého důvodu nelze použít ověřování pomocí protokolu Kerberos. Jeho použití jako záložní můžete také zakázat nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> vlastnost `false`, což způsobí, že WCF, aby se snažíme vyvolá výjimku, pokud je použit protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemůže zabránit odeslání při přenosu přihlašovacích údajů protokolů NTLM.|  
|Windows|Určuje ověřování Windows. Chcete-li zadat pouze protokol Kerberos v doméně Windows, nastavte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> vlastnost `false` (výchozí hodnota je `true`).|  
|Certifikát|Provádí ověření klienta pomocí certifikátu X.509.|  
|Heslo|Uživatel musí zadat uživatelské jméno a heslo. Ověření páru jméno/heslo uživatele pomocí ověřování Windows nebo jiné vlastní řešení.|  
  
### <a name="message-client-credential-types"></a>Typy zpráv klienta přihlašovacích údajů  
 V následující tabulce jsou uvedeny typy možných přihlašovacích údajů, které můžete použít při vytváření aplikace, který používá zabezpečení zpráv. Tyto hodnoty můžete použít v kódu nebo konfiguračního souboru.  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|Žádný|Určuje, že klient nemusí představovat přihlašovací údaje. Výsledkem je k anonymní klienta.|  
|Windows|Umožňuje výměny zpráv SOAP probíhá v kontextu zabezpečení vytvořen se přihlašovací údaje Windows.|  
|Uživatelské jméno|Umožňuje službě tak, aby vyžadovala ověření klienta s pověření uživatelského jména. Všimněte si, že WCF nepovoluje žádné kryptografické operace s uživatelskými jmény, jako je například generuje podpis nebo šifrovat data. WCF se zajistí, že při použití uživatelských přihlašovacích údajů název je zabezpečený přenos.|  
|Certifikát|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu X.509.|  
|Vydaný Token|Vlastní token typu nakonfigurovaný podle zásady zabezpečení. Výchozí typ tokenu je zabezpečení kontrolní výrazy SAML (Markup Language). Token, který je vystaven Služba tokenů zabezpečení. Další informace najdete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Model vyjednávání přihlašovacích údajů služby  
 *Vyjednávání* je proces vytvoření vztahu důvěryhodnosti mezi klientem a službou výměnou přihlašovacích údajů. Proces se provádí opakované mezi klientem a služby, aby zpřístupnit pouze informace potřebné k dalším krokem v procesu vyjednávání. V praxi konečný výsledek je doručování přihlašovacích údajů pro služby klienta, který se má použít v následných operací.  
  
 S jednou výjimkou ve výchozím nastavení vazeb poskytovaných systémem ve službě WCF vyjednávání přihlašovacích údajů služby automaticky při použití zabezpečení na úrovni zprávy. (Výjimkou je <xref:System.ServiceModel.BasicHttpBinding>, což není povoleno zabezpečení ve výchozím nastavení.) Chcete-li toto chování zakázat, přečtěte si téma <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnosti.  
  
> [!NOTE]
>  Při použití zabezpečení SSL v rozhraní .NET Framework 3.5 nebo novější, klienta WCF používá i zprostředkující certifikáty ve své vlastní úložiště certifikátů a zprostředkujících certifikátů přijatých během vyjednávání SSL k provedení ověřování řetězu certifikátů na služby certifikát. Rozhraní .NET framework 3.0 využívá jenom nainstalované v místním úložišti certifikátů zprostředkující certifikáty.  
  
#### <a name="out-of-band-negotiation"></a>Vyjednávání Out-of-Band  
 Pokud je zakázané automatické vyjednávání, přihlašovací údaje služby musí být zřízená v klientském počítači před odesláním jakýchkoli zpráv do služby. To se také označuje jako *out-of-band* zřizování. Například pokud je typ zadané přihlašovací údaje certifikát, a je zakázáno automatické vyjednávání, klient musí kontaktujte vlastníka služby pro příjem a nainstalujte certifikát na počítači se systémem klientské aplikace. To můžete udělat, třeba když chcete striktně řídit, které klienti mají přístup k nějaké službě v případě business-to-business. V tomto out z-obsluhy vzdálené správy – vyjednávání lze provést v e-mailu a certifikátu X.509 je uložen v úložišti certifikátů Windows, pomocí nástroje, jako je modul snap-in Certifikáty konzoly Microsoft Management Console (MMC).  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Vlastnost se používá k poskytování služby pomocí certifikátu, který bylo dosaženo pomocí out-of-band vyjednávání. To je nezbytné, při použití <xref:System.ServiceModel.BasicHttpBinding> třídy, protože vazba nepovoluje automatizované vyjednávání. Vlastnost se používá také ve scénáři bez korelace nejsou duplexní. Toto je scénář, kde server odešle zprávu do klienta bez nutnosti klient nejdřív odešlete požadavek na server. Protože server nemá žádné žádosti z klienta, musí používat certifikát klienta pro šifrování zprávy do klienta.  
  
## <a name="setting-credential-values"></a>Nastavení hodnot přihlašovacích údajů  
 Jakmile vyberete režim zabezpečení, je nutné zadat samotné přihlašovací údaje. Například pokud typ přihlašovacích údajů nastavená na "certifikáty", pak musíte přidružit konkrétní přihlašovací údaje (například konkrétní certifikát X.509) služba nebo klient.  
  
 V závislosti na tom, zda jsou programovací službu nebo klienta metoda pro nastavení hodnoty přihlašovacích údajů se mírně liší.  
  
### <a name="setting-service-credentials"></a>Nastavení přihlašovacích údajů služby  
 Pokud používáte režim přenosu a používáte jako přenosového protokolu HTTP, musíte použít buď Internetové informační služby (IIS) nebo konfigurace portu s certifikátem. Další informace najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) a [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Při zřizování služby pomocí přihlašovacích údajů v kódu, vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy a zadejte příslušná pověření pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třídy přistupovat prostřednictvím <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost.  
  
#### <a name="setting-a-certificate"></a>Nastavení certifikátu  
 Chcete-li zřídit službu společně s certifikátem X.509, který se má použít k ověřování klientů, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy.  
  
 Při zřizování služby pomocí klientského certifikátu, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> třídy.  
  
#### <a name="setting-windows-credentials"></a>Nastavení přihlašovacích údajů Windows  
 Pokud klient Určuje platné uživatelské jméno a heslo, tyto přihlašovací údaje se používá k ověření klienta. V opačném případě se používají přihlašovací údaje aktuálního přihlášeného uživatele.  
  
### <a name="setting-client-credentials"></a>Nastavení přihlašovacích údajů klienta  
 Ve službě WCF klientské aplikace připojit ke službám pomocí klienta WCF. Každý klient je odvozen od <xref:System.ServiceModel.ClientBase%601> třídy a <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost na klientovi umožňuje specifikaci různých hodnot přihlašovacích údajů klienta.  
  
#### <a name="setting-a-certificate"></a>Nastavení certifikátu  
 Při zřizování služby certifikátem X.509, který se používá k ověření klienta ke službě, použijte <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Jak se používají přihlašovací údaje pro klienta k ověření klienta ke službě  
 Poskytuje informace o klientech přihlašovacích údajů potřebných pro komunikaci se službou buď pomocí <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnost. Zabezpečený kanál používá tyto informace k ověření klienta ke službě. Ověřování se provádí prostřednictvím jednoho ze dvou režimů:  
  
-   Přihlašovací údaje klienta se používají jednou před odesláním první zprávu pomocí instance klienta WCF k vytvoření kontextu zabezpečení. Všechny zprávy aplikace jsou pak zabezpečené skrze kontext zabezpečení.  
  
-   Přihlašovací údaje klienta slouží k ověření každé aplikace zpráva odeslaná do služby. V tomto případě žádný kontext pokládáme stav, mezi klientem a službou.  
  
### <a name="established-identities-cannot-be-changed"></a>Zavedené identity nejde změnit.  
 Při použití první způsob je trvale přidružený identity klienta vytvořeným kontextem. Po vytvoření kontextu zabezpečení, to znamená, nemůže být změněna identita přidružené ke klientovi.  
  
> [!IMPORTANT]
>  Neexistuje situace je potřeba vědět po nelze Přepnutí identity (to znamená, když vytvořit bezpečnostní kontext je na výchozí chování). Pokud vytvoříte službu, která komunikuje s druhou službu, identity používá k otevření klienta WFG pro druhý služby nelze změnit. To stane problém, pokud více klientů můžou používat první služby a služby zosobňuje klienty při přístupu ke službě druhý. Pokud služba opakované používání stejného klienta pro všechny volající, všechna volání do druhé služby se provádějí s identitou první volajícího, která byla použita k otevření klienta ke službě druhý. Jinými slovy služba používá identity první klient pro své klienty komunikovat se službou druhý. To může vést ke zvýšení oprávnění. Pokud to není požadované chování služby, musíte sledovat jednotliví volající a vytvořit nového klienta do druhé služby pro každý jedinečných volajícího a zajistit, aby používal službu pouze správné klienta pro správné volajícího komunikovat se službou druhý.  
  
 Další informace o přihlašovací údaje a zabezpečených relací najdete v tématu [aspekty zabezpečení pro zabezpečené relace](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
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
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Programování zabezpečení WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
