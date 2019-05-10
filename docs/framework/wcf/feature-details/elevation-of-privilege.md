---
title: Zvýšení oprávnění
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: 1e42e2726b54464d479398c023c3e7caecf9b054
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753051"
---
# <a name="elevation-of-privilege"></a>Zvýšení oprávnění
*Zvýšení úrovně oprávnění* výsledkem udělení povolení útočník nad rámec těchto zpočátku udělená oprávnění. Například útočník se sadou oprávnění "jen pro čtení" oprávnění nějakým způsobem zvýší oprávnění set "pro čtení a zápisu."  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Důvěryhodné služby STS musí podepsat deklarací identity tokenu SAML  
 Token zabezpečení kontrolní výrazy SAML (Markup Language) je obecný XML token, který je výchozím typem vydávaných tokenů. SAML token lze sestavit pomocí tokenu služby zabezpečení (STS), která důvěřuje end webové služby v typické exchange. Tokeny SAML obsahují deklarace identity v příkazech. Útočník může kopírovat platný token deklarace identity, vytvořte nový token SAML a podepište ho pomocí různých vystavitele. Cílem je zjistit, jestli server ověřuje vydavatelů a pokud ne, využívat slabé stránky k sestavení kompletních tokeny SAML, které umožňují oprávnění nad rámec těchto určených podle důvěryhodné služby tokenů zabezpečení.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> Třídy ověří digitální podpis obsažených v tokenu SAML a ve výchozím nastavení <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> vyžaduje, aby byly podepsány tokeny SAML certifikátem X.509, který je platný, kdy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy je nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust` režim pouze není dostatečná k určení, zda je důvěryhodného vystavitele tokenu SAML. Služby, které vyžadují podrobnější model důvěryhodnosti můžete buď používat ověřování a vynucování zásad pro kontrolu vystavitele deklarace identity sady produkované vystavený ověřovací token nebo použít nastavení pro ověření X.509 na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> omezit sadu povolené, podpisové certifikáty. Další informace najdete v tématu [správa deklarací identity a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) a [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Přepnutí Identity bez kontextu zabezpečení  
 Platí jenom pro následující [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Když se vytvoří připojení mezi klientem a serverem a identity klienta se nezmění, s výjimkou jednoho situaci: Po otevření klienta WCF, pokud jsou splněny všechny následující podmínky:  
  
- Postupy k vytvoření kontextu zabezpečení (pomocí zabezpečení přenosu, nebo relaci zabezpečení zprávu) je vypnout (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> je nastavena na `false` v případě zabezpečení zpráv nebo nebyl schopen vytvořit zabezpečení přenosu relace se používá v případě zabezpečení přenosu. HTTPS je jedním z takových transport).  
  
- Používáte ověřování Windows.  
  
- Přihlašovací údaje, které explicitně nenastavíte.  
  
- Jsou volání služby za zosobněného kontextu.  
  
 Pokud jsou splněné tyto podmínky, může změnit identity použité k ověření klienta ke službě (nemusí být zosobněnou identitou, ale identitu procesu místo) po otevření klienta WCF. K tomu dochází, protože přihlašovací údaje Windows používá k ověření klienta ke službě se přenášejí se všechny zprávy a pověření pro ověřování se získávají z identita Windows aktuálního vlákna. Pokud se identita Windows aktuálního vlákna změní (například zosobněním různých volajícího), může také změnit přihlašovací údaj, který je připojen ke zprávě a použít k ověření klienta ke službě.  
  
 Pokud chcete mít deterministické chování při použití ověřování Windows společně s zosobnění je nutné explicitně nastavit přihlašovací údaje Windows nebo je potřeba vytvořit kontext zabezpečení ve službě. K tomuto účelu použijte relaci zabezpečení zprávy nebo relace zabezpečení přenosu. Například net.tcp přenosu může poskytnout relace zabezpečení přenosu. Kromě toho musí používat pouze synchronní verzi klientské operace při volání služby. Pokud vytvoříte vztah kontextu zabezpečení zprávy, by neměl uchováváte připojení ke službě otevřít déle než nakonfigurované relace období obnovení, protože identita můžete také změnit během procesu obnovení relace.  
  
### <a name="credentials-capture"></a>Snímek přihlašovací údaje  
 Toto se vztahuje na [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]a následné verze.  
  
 Klient používá přihlašovací údaje nebo služby, které jsou založeny na aktuální kontext vlákna. Přihlašovací údaje jsou získané `Open` – metoda (nebo `BeginOpen`, pro asynchronní volání) se nazývá klienta nebo služby. Pro obě <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ClientBase%601> třídy, `Open` a `BeginOpen` dědí metody <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> a <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> metody <xref:System.ServiceModel.Channels.CommunicationObject> třídy.  
  
> [!NOTE]
>  Při použití `BeginOpen` metody zachycené přihlašovací údaje nelze zaručit pověření proces, který volá metodu.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Token mezipamětí povolit jejich přehrání pomocí zastaralá Data  
 WCF používá místní autority zabezpečení (LSA) `LogonUser` funkce k ověřování uživatelů pomocí uživatelského jména a hesla. Protože funkci přihlášení je nákladná operace, WCF umožňuje, abyste mezipaměť tokenů, které představují ověřeným uživatelům ke zvýšení výkonu. Mechanizmus ukládání do mezipaměti ukládá výsledky z `LogonUser` pro další použití. Tento mechanismus je ve výchozím nastavení; zakázané. ji Pokud chcete povolit, nastavte <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> vlastnost `true`, nebo použijte `cacheLogonTokens` atribut [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Můžete nastavit čas to Live (TTL) pro tokeny v mezipaměti tak, že nastavíte <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> vlastnost <xref:System.TimeSpan>, nebo použijte `cachedLogonTokenLifetime` atribut `userNameAuthentication` element; výchozí hodnota je 15 minut. Všimněte si, že token je uložené v mezipaměti, libovolného klienta, který zobrazí stejné uživatelské jméno a heslo můžete použít i token, i v případě, že uživatelský účet je odstraněn z Windows, nebo pokud se změnila jeho heslo. Dokud hodnota TTL nevyprší a token, který se odebere z mezipaměti, WCF umožňuje (potenciálně škodlivý) uživatele ověřit.  
  
 Chcete-li tento problém zmírnit: Snížit tak, že nastavíte okno útoku `cachedLogonTokenLifetime` hodnotu na nejkratší dobu span uživatelé potřebují.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Vydaný Token autorizace: Vypršení platnosti obnovit velké hodnoty  
 Za určitých podmínek <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> může být nastaven na hodnotu neočekávaně větší ( <xref:System.DateTime.MaxValue> pole hodnota minus jeden den, nebo 20. prosince 9999).  
  
 K tomu dojde při použití <xref:System.ServiceModel.WSFederationHttpBinding> a některé z vazeb poskytovaných systémem, které mají vydaný token jako klient typ přihlašovacích údajů.  
  
 Tato situace nastane také při vytváření vlastní vazby pomocí jedné z následujících metod:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Chcete-li tento problém zmírnit, musíte zkontrolovat zásady autorizace pro akce a čas vypršení platnosti jednotlivých zásad autorizace.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Služba používá jiný certifikát než zamýšlené klienta  
 Za určitých podmínek lze klienta digitálně podepsat zprávy pomocí certifikátu X.509 a službu načíst jiný certifikát než zamýšlené.  
  
 Tato situace může nastat v následujících případech:  
  
- Klient digitálně podepíše zprávu pomocí certifikátu X.509 nepřipojí certifikát X.509 na zprávu, ale spíš jenom odkazuje na certifikát s použitím jeho identifikátor klíče subjektu.  
  
- Počítač služby obsahuje dva nebo více certifikátů se stejným klíčem veřejné, ale obsahují rozdílné informace.  
  
- Služba načte certifikát, který odpovídá identifikátoru klíče subjektu, ale to není ten, který klient chtěli použít. Když WCF obdrží zprávu a ověří podpis, WCF mapuje informace v neúmyslnému certifikát X.509 na sadu deklarací identity, které jsou rozdílné a potenciálně se zvýšenými oprávněními z co očekává klienta.  
  
 Chcete-li tento problém zmírnit, odkaz X.509 certifikátu dalším způsobem, jako je třeba použití <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
