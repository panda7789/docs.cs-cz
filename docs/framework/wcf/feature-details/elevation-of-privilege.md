---
title: Zvýšení oprávnění
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: eae3c2a72e686774ee510dfc3ec9db04df7db630
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966174"
---
# <a name="elevation-of-privilege"></a>Zvýšení oprávnění
*Zvýšení úrovně oprávnění* z důvodu udělení oprávnění k autorizaci útočníka nad rámec původně udělených. Například útočník, který má sadu oprávnění "jen pro čtení", nějakým způsobem pozvyšuje sadu tak, aby zahrnovala možnost "čtení a zápis".  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Důvěryhodné STS by měl podepsat deklarace identity tokenu SAML.  
 Token SAML (Security Assert Markup Language) je obecný token XML, který je výchozím typem pro vydané tokeny. Token SAML může být vytvořen pomocí služby tokenů zabezpečení (STS), kterou koncová webová služba důvěřuje v typickém systému Exchange. Tokeny SAML obsahují deklarace v příkazech. Útočník může zkopírovat deklarace identity z platného tokenu, vytvořit nový token SAML a podepsat ho pomocí jiného vystavitele. Záměrem je určit, jestli Server ověřuje vystavitele, a pokud ne, využije slabiny k vytváření tokenů SAML, které umožňují oprávnění nad rámec těch, které jsou určené důvěryhodnou službou STS.  
  
 Třída ověřuje digitální podpis obsažený v tokenu SAML a výchozí hodnota <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> vyžaduje, aby tokeny SAML byly podepsány certifikátem X. 509 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> , který je <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> platný při nastavení třídy na hodnotu. <xref:System.IdentityModel.Tokens.SamlAssertion> <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust`samotný režim není dostačující k určení, zda je Vystavitel tokenu SAML důvěryhodný. Služby, které vyžadují podrobnější model vztahu důvěryhodnosti, můžou použít zásady autorizace a vynucení ke kontrole vystavitele sad deklarací vytvořených pomocí ověřování vydaných tokenů, nebo <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> k omezení sady parametrů ověřování pomocí X. 509. povolené podpisové certifikáty. Další informace najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) a [federačních a](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)vydaných tokenů.  
  
## <a name="switching-identity-without-a-security-context"></a>Přepínání identity bez kontextu zabezpečení  
 Následující platí pouze pro WinFX.  
  
 Při navázání připojení mezi klientem a serverem se identita klienta nemění, s výjimkou jedné situace: po otevření klienta služby WCF platí všechny následující podmínky:  
  
- Procedury pro vytvoření kontextu zabezpečení (pomocí relace zabezpečení přenosu nebo relace zabezpečení zprávy) jsou vypnuty (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost je nastavena na `false` hodnotu v případě zabezpečení zprávy nebo přenosu neschopnýho navázání zabezpečení). v případě transportního zabezpečení se používají relace. Protokol HTTPS je jedním z příkladů takového přenosu.  
  
- Používáte ověřování systému Windows.  
  
- Přihlašovací údaje výslovně nenastavíte.  
  
- Voláte službu pod zosobněným kontextem zabezpečení.  
  
 Pokud jsou tyto podmínky splněné, může se identita používaná k ověření klienta ke službě změnit (nejedná se o zosobněnou identitu, ale také o identitu procesu) po otevření klienta WCF. Důvodem je, že přihlašovací údaje systému Windows použité k ověření klienta pro službu jsou přenášeny pomocí každé zprávy a přihlašovací údaje, které se používají pro ověřování, se získávají z identity Windows aktuálního vlákna. Pokud se identita Windows aktuálního vlákna změní (například zosobněním jiného volajícího), může se také změnit přihlašovací údaj, který je připojený ke zprávě a který slouží k ověření klienta ke službě.  
  
 Pokud chcete mít deterministické chování při ověřování systému Windows společně s zosobněním, je nutné explicitně nastavit pověření systému Windows nebo vytvořit kontext zabezpečení s touto službou. Provedete to tak, že použijete relaci zabezpečení zprávy nebo relaci zabezpečení přenosu. Například přenos NET. TCP může poskytovat relaci zabezpečení přenosu. Kromě toho je nutné při volání služby použít pouze synchronní verzi operací klienta. Pokud vytvoříte kontext zabezpečení zprávy, neměli byste udržovat připojení ke službě otevřené déle než nakonfigurované období obnovy relace, protože identitu lze také změnit během procesu obnovení relace.  
  
### <a name="credentials-capture"></a>Zachycení přihlašovacích údajů  
 Následující postup [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]se týká a dalších verzí.  
  
 Přihlašovací údaje, které používá klient nebo služba, jsou založené na aktuálním kontextovém vlákně. Pověření jsou získána při `Open` volání metody (nebo `BeginOpen`pro asynchronní volání) klienta nebo služby. <xref:System.ServiceModel.ClientBase%601> Protřídy`Open` imetody`BeginOpen` a dědí z<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metod<xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> a třídy. <xref:System.ServiceModel.Channels.CommunicationObject> <xref:System.ServiceModel.ServiceHost>  
  
> [!NOTE]
> Při použití `BeginOpen` metody nemohou být zachycené přihlašovací údaje zaručené jako přihlašovací údaje procesu, který volá metodu.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Mezipaměť tokenů umožňují opakované přehrání pomocí zastaralých dat.  
 Služba WCF používá k ověřování uživatelů pomocí funkce místního `LogonUser` úřadu zabezpečení (LSA) uživatelské jméno a heslo. Vzhledem k tomu, že funkce přihlášení je nákladná operace, umožňuje WCF ukládat tokeny, které reprezentují ověřené uživatele, aby zvýšily výkon. Mechanismus ukládání do mezipaměti ukládá výsledky `LogonUser` pro následné použití. Tento mechanismus je ve výchozím nastavení zakázaný. Pokud ji chcete povolit, nastavte <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> vlastnost na `true`nebo `cacheLogonTokens` [ \<použijte atribut UserNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Můžete nastavit hodnotu TTL (Time to Live) pro tokeny <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> v mezipaměti nastavením vlastnosti na hodnotu <xref:System.TimeSpan>nebo `userNameAuthentication` použít `cachedLogonTokenLifetime` atribut prvku. výchozí hodnota je 15 minut. Všimněte si, že i když je token uložen v mezipaměti, může token použít libovolný klient, který představuje stejné uživatelské jméno a heslo, i když se uživatelský účet odstraní ze systému Windows nebo pokud jeho heslo bylo změněno. Až do vypršení hodnoty TTL dojde k odebrání tokenu z mezipaměti, WCF umožní ověřování (případně zlomyslného) uživateli.  
  
 Pro zmírnění tohoto problému: Snižte interval útoku nastavením `cachedLogonTokenLifetime` hodnoty na nejkratší časový rozsah, který uživatelé potřebují.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Autorizace vydaného tokenu: Konec platnosti resetování na velkou hodnotu  
 Za určitých podmínek <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> může být vlastnost objektu nastavena na <xref:System.DateTime.MaxValue> neočekávaně větší hodnotu (hodnota pole minus jeden den nebo 20. prosince 9999).  
  
 K tomu dochází při použití <xref:System.ServiceModel.WSFederationHttpBinding> a všech vazeb poskytovaných systémem, které mají vystavený token jako typ pověření klienta.  
  
 K tomu dochází také při vytváření vlastních vazeb pomocí jedné z následujících metod:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Aby to bylo možné zmírnit, musí zásady autorizace kontrolovat akci a čas vypršení platnosti každé zásady autorizace.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Služba používá jiný certifikát než zamýšlený klient.  
 Za určitých podmínek může klient digitálně podepsat zprávu pomocí certifikátu X. 509 a nechat službu, aby načetla jiný certifikát, než je ten, který je určen.  
  
 Tato situace může nastat za následujících okolností:  
  
- Klient digitálně podepisuje zprávu pomocí certifikátu X. 509 a nepřipojuje ke zprávě certifikát X. 509, ale místo toho pouze odkazuje na certifikát pomocí identifikátoru klíče subjektu.  
  
- Počítač služby obsahuje dva nebo více certifikátů se stejným veřejným klíčem, ale obsahuje jiné informace.  
  
- Služba načte certifikát, který odpovídá identifikátoru klíče subjektu, ale nejedná se o klienta, kterého se má použít. Když WCF obdrží zprávu a ověří signaturu, služba WCF namapuje informace v nezamýšleném certifikátu X. 509 na sadu deklarací, které se liší a potenciálně se zvýší z toho, co klient očekával.  
  
 Pokud to chcete zmírnit, odkázat na certifikát X. 509 jiným způsobem, jako je <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>například použití.  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
