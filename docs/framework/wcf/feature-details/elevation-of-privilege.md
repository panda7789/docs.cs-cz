---
title: Zvýšení oprávnění
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: 8838b139efa20bc796fc21567cc6fc9ee8691eee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283245"
---
# <a name="elevation-of-privilege"></a>Zvýšení oprávnění
*Zvýšení úrovně oprávnění* z důvodu udělení oprávnění k autorizaci útočníka nad rámec původně udělených. Například útočník, který má sadu oprávnění "jen pro čtení", nějakým způsobem pozvyšuje sadu tak, aby zahrnovala možnost "čtení a zápis".  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Důvěryhodné STS by měl podepsat deklarace identity tokenu SAML.  
 Token SAML (Security Assert Markup Language) je obecný token XML, který je výchozím typem pro vydané tokeny. Token SAML může být vytvořen pomocí služby tokenů zabezpečení (STS), kterou koncová webová služba důvěřuje v typickém systému Exchange. Tokeny SAML obsahují deklarace v příkazech. Útočník může zkopírovat deklarace identity z platného tokenu, vytvořit nový token SAML a podepsat ho pomocí jiného vystavitele. Záměrem je určit, jestli Server ověřuje vystavitele, a pokud ne, využije slabiny k vytváření tokenů SAML, které umožňují oprávnění nad rámec těch, které jsou určené důvěryhodnou službou STS.  
  
 Třída <xref:System.IdentityModel.Tokens.SamlAssertion> ověřuje digitální podpis obsažený v tokenu SAML a výchozí <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> vyžaduje, aby tokeny SAML byly podepsány certifikátem X. 509, který je platný, pokud je <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> třídy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. pouze v režimu `ChainTrust` nestačí určit, zda je Vystavitel tokenu SAML důvěryhodný. Služby, které vyžadují podrobnější model důvěryhodnosti, můžou použít zásady autorizace a vynucení k ověření vystavitele sad deklarací vyprodukovaných ověřováním vydaných tokenů, nebo k omezení sady povolených podpisových certifikátů použít nastavení ověřování X. 509 na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>. Další informace najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) a [federačních a vydaných tokenů](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Přepínání identity bez kontextu zabezpečení  
 Následující platí pouze pro WinFX.  
  
 Při navázání připojení mezi klientem a serverem se identita klienta nemění, s výjimkou jedné situace: po otevření klienta služby WCF platí všechny následující podmínky:  
  
- Procedury pro vytvoření kontextu zabezpečení (pomocí relace zabezpečení přenosu nebo relace zabezpečení zprávy) se vypnou (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost je nastavená na `false` v případě zabezpečení zprávy nebo přenosu neschopných vytvářet relace zabezpečení v případě transportního zabezpečení. Protokol HTTPS je jedním z příkladů takového přenosu.  
  
- Používáte ověřování systému Windows.  
  
- Přihlašovací údaje výslovně nenastavíte.  
  
- Voláte službu pod zosobněným kontextem zabezpečení.  
  
 Pokud jsou tyto podmínky splněné, může se identita používaná k ověření klienta ke službě změnit (nejedná se o zosobněnou identitu, ale také o identitu procesu) po otevření klienta WCF. Důvodem je, že přihlašovací údaje systému Windows použité k ověření klienta pro službu jsou přenášeny pomocí každé zprávy a přihlašovací údaje, které se používají pro ověřování, se získávají z identity Windows aktuálního vlákna. Pokud se identita Windows aktuálního vlákna změní (například zosobněním jiného volajícího), může se také změnit přihlašovací údaj, který je připojený ke zprávě a který slouží k ověření klienta ke službě.  
  
 Pokud chcete mít deterministické chování při ověřování systému Windows společně s zosobněním, je nutné explicitně nastavit pověření systému Windows nebo vytvořit kontext zabezpečení s touto službou. Provedete to tak, že použijete relaci zabezpečení zprávy nebo relaci zabezpečení přenosu. Například přenos NET. TCP může poskytovat relaci zabezpečení přenosu. Kromě toho je nutné při volání služby použít pouze synchronní verzi operací klienta. Pokud vytvoříte kontext zabezpečení zprávy, neměli byste udržovat připojení ke službě otevřené déle než nakonfigurované období obnovy relace, protože identitu lze také změnit během procesu obnovení relace.  
  
### <a name="credentials-capture"></a>Zachycení přihlašovacích údajů  
 Následující postup se týká .NET Framework 3,5 a dalších verzí.  
  
 Přihlašovací údaje, které používá klient nebo služba, jsou založené na aktuálním kontextovém vlákně. Pověření jsou získána při volání metody `Open` (nebo `BeginOpen`, pro asynchronní volání) klienta nebo služby. Pro třídy <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ClientBase%601> dědí metody `Open` a `BeginOpen` z <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> a <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> metod třídy <xref:System.ServiceModel.Channels.CommunicationObject>.  
  
> [!NOTE]
> Při použití metody `BeginOpen` nemůže být zachycená pověření zaručena jako přihlašovací údaje procesu, který volá metodu.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Mezipaměť tokenů umožňují opakované přehrání pomocí zastaralých dat.  
 Služba WCF používá funkci místního úřadu zabezpečení (LSA) `LogonUser` k ověřování uživatelů podle uživatelského jména a hesla. Vzhledem k tomu, že funkce přihlášení je nákladná operace, umožňuje WCF ukládat tokeny, které reprezentují ověřené uživatele, aby zvýšily výkon. Mechanismus ukládání do mezipaměti ukládá výsledky z `LogonUser` pro následné účely. Tento mechanismus je ve výchozím nastavení zakázaný. Pokud ho chcete povolit, nastavte vlastnost <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> na `true`nebo použijte atribut `cacheLogonTokens` [\<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Můžete nastavit hodnotu TTL (Time to Live) pro tokeny uložené v mezipaměti nastavením vlastnosti <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> na <xref:System.TimeSpan>nebo použít atribut `cachedLogonTokenLifetime` elementu `userNameAuthentication`; Výchozí hodnota je 15 minut. Všimněte si, že i když je token uložen v mezipaměti, může token použít libovolný klient, který představuje stejné uživatelské jméno a heslo, i když se uživatelský účet odstraní ze systému Windows nebo pokud jeho heslo bylo změněno. Až do vypršení hodnoty TTL dojde k odebrání tokenu z mezipaměti, WCF umožní ověřování (případně zlomyslného) uživateli.  
  
 Pokud to chcete zmírnit, zmenšete okno útoku nastavením `cachedLogonTokenLifetime` hodnoty na nejkratší časový rozsah, který uživatelé potřebují.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Autorizace vydaných tokenů: vypršení platnosti resetování na velkou hodnotu  
 Za určitých podmínek může být vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> <xref:System.IdentityModel.Policy.AuthorizationContext> nastavena na neočekávaně větší hodnotu (hodnota pole <xref:System.DateTime.MaxValue> minus jeden den nebo 20. prosince 9999).  
  
 K tomu dochází při použití <xref:System.ServiceModel.WSFederationHttpBinding> a všech systémových vazeb, které mají vystavený token jako typ přihlašovacích údajů klienta.  
  
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
  
 Pokud to chcete zmírnit, odkažte na certifikát X. 509 jiným způsobem, jako je například použití <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
