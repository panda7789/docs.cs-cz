---
title: "Zvýšení oprávnění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2e44d0ecf6afb81928d83ea925f836f8b6927d97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="elevation-of-privilege"></a>Zvýšení oprávnění
*Zvýšení úrovně oprávnění* výsledkem udělení povolení útočník nad rámec těchto původně udělí oprávnění. Například útočník se sadou oprávnění "jen pro čtení" oprávnění nějakým způsobem zvyšuje sadu "pro čtení a zápisu."  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Důvěryhodné služby tokenů zabezpečení by měl přihlásit deklarací tokenu SAML  
 Token zabezpečení kontrolní výrazy Markup Language (SAML) je obecný token XML, který je výchozím typem pro vydané tokeny. SAML token lze sestavit pomocí zabezpečení tokenu služby (STS), end webová služba vztahy důvěryhodnosti v typické systému exchange. Tokeny SAML obsahují deklarace identity v příkazech. Útočník může kopírovat deklarace identity z platný token, vytvořit nový token SAML a podepište ho pomocí různých vystavitele. Je cílem zjistit, zda server ověřuje vystavitelů a pokud ne, využívat slabinu vytvořit tokeny SAML, které umožňují oprávnění nad rámec těchto určený pomocí důvěryhodné služby tokenů zabezpečení.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> Třída ověřuje digitální podpis obsažených v tokenu SAML a ve výchozím nastavení <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> vyžaduje, aby tokeny SAML být podepsány certifikátem X.509, který je platný, kdy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třída je nastaven na <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust`režim samostatně je nedostatečná pro určení, zda je důvěryhodného vystavitele tokenu SAML. Služby, které vyžadují podrobnější model důvěryhodnosti můžete buď použít ověřování a vynucování zásad pro kontrolu vystavitele deklarace identity sady vyprodukované vydaných tokenů ověřování nebo nastavení ověření X.509 na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> omezit sadu povoleno, podpisové certifikáty. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) a [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Přepínání Identity bez kontextu zabezpečení  
 Následující se vztahují pouze na [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Po navázání připojení mezi klientem a serverem, identita klienta nezmění, kromě jednoho situaci: po [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] otevřít klienta, pokud jsou splněny všechny následující podmínky:  
  
-   Postup vytvoření kontextu zabezpečení (pomocí zabezpečení přenosu nebo relaci zabezpečení zpráv) je vypnuté (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> je nastavena na `false` v případě zabezpečení zpráv nebo není schopen vytvořit zabezpečení přenosu relace se používá v případě zabezpečení přenosu. Příkladem takových přenosu je HTTPS).  
  
-   Používáte ověřování systému Windows.  
  
-   Přihlašovací údaje není explicitně nastavena.  
  
-   Při volání služby v kontextu zosobněného zabezpečení.  
  
 Pokud jsou splněné tyto podmínky, identita použitá k ověření klienta ke službě může změnit (nemusí být zosobněnou identitou ale identitě procesu místo) po [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta je otevřen. K tomu dochází, protože pověření systému Windows používá k ověření klienta ke službě se přenáší s každou zprávu a pověření použité pro ověřování se získávají z aktuální vlákno identitu systému Windows. Pokud se změní identitu Windows aktuální vlákno (například zosobněním různých volající), mohou také změnit pověření, které je připojen ke zprávě a použít k ověření klienta ke službě.  
  
 Pokud budete chtít mít deterministické chování při použití ověřování systému Windows společně s zosobnění je třeba explicitně nastavit pověření systému Windows nebo budete muset vytvořit kontext zabezpečení se službou. K tomu použijte relace zabezpečení zprávy nebo relace přenosu zabezpečení. Přenos net.tcp můžete například zadat relaci zabezpečení přenosu. Kromě toho musíte použít synchronní verzi klientské operace, při volání služby. Pokud vytvoříte kontextu zabezpečení zprávy, by neměl necháte připojení ke službě otevřete delší než interval obnovování nakonfigurované relace, protože identita můžete také změnit během procesu obnovení relace.  
  
### <a name="credentials-capture"></a>Zachycení přihlašovacích údajů  
 Toto se vztahuje na [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]a další verze.  
  
 Pověření používaná klientem nebo služby jsou založené na aktuální vlákno kontextu. Přihlašovací údaje byly získány při `Open` – metoda (nebo `BeginOpen`, pro asynchronní volání) se nazývá klienta nebo služby. Pro obě <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ClientBase%601> třídy, `Open` a `BeginOpen` metody dědit z <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> a <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> metody <xref:System.ServiceModel.Channels.CommunicationObject> třídy.  
  
> [!NOTE]
>  Při použití `BeginOpen` metoda, přihlašovací údaje zachytit nemůže zaručit jako přihlašovací údaje proces, který volá metodu.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Token mezipamětí povolit opětovného přehrání pomocí zastaralá Data  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá místní autority zabezpečení (LSA) `LogonUser` funkce k ověření uživatele podle uživatelského jména a hesla. Protože funkce přihlášení je nákladná operace, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje mezipaměti tokeny, které představují ověřeným uživatelům zvýšit výkon. Ukládání do mezipaměti mechanismus uloží výsledky z `LogonUser` pro další použití. Tento mechanismus vypnutá ve výchozím nastavení; Chcete-li ji povolit, nastavte <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> vlastnost `true`, nebo použijte `cacheLogonTokens` atribut [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Můžete nastavit dobu to Live (TTL) pro uložené v mezipaměti tokeny pomocí nastavení <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> vlastnosti <xref:System.TimeSpan>, nebo použijte `cachedLogonTokenLifetime` atribut `userNameAuthentication` element; výchozí hodnota je 15 minut. Všimněte si, že i když token se uloží do mezipaměti, libovolného klienta, který představuje stejné uživatelské jméno a heslo lze použít s tokenem, i v případě, že uživatelský účet je odstraněn ze systému Windows, nebo došlo ke změně jeho heslo. Dokud hodnota TTL nevyprší a token se odebere z mezipaměti, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje ověření (potenciálně škodlivý) uživatele.  
  
 Toto riziko lze snížit: snížit okno útoku nastavením `cachedLogonTokenLifetime` hodnotu na nejkratší dobu span uživatelé potřebují.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Vystavený Token autorizace: Vypršení platnosti se resetování velké hodnoty  
 Za určitých podmínek <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> může být nastaven na hodnotu neočekávaně větší ( <xref:System.DateTime.MaxValue> pole hodnotu minus jeden den, nebo 20 prosince 9999).  
  
 K tomu dojde při použití <xref:System.ServiceModel.WSFederationHttpBinding> a některé z vazby poskytované systémem, které mají token vydaných jako klient typ přihlašovacích údajů.  
  
 Také k tomu dojde, když vytvoříte vlastní vazby pomocí jedné z následujících metod:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Toto riziko lze snížit musí zkontrolujte zásady autorizace, akci a čas vypršení platnosti, každá zásada autorizace.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Služba používá jiný certifikát než zamýšleného klienta  
 Za určitých podmínek můžete klienta digitálnímu podepisování zpráv společně s certifikátem X.509 a službu načíst jiný certifikát než zamýšlené.  
  
 Tato situace může nastat v následujících případech:  
  
-   Klient digitálně podepíše zprávu pomocí certifikátu X.509. certifikát a nepřipojí certifikátu X.509 na zprávu, ale spíš jenom odkazuje na základě jeho identifikátoru klíče subjektu certifikátu.  
  
-   Služby počítače obsahuje dva nebo víc certifikátů se stejný veřejný klíč, ale obsahují různé informace.  
  
-   Služba načte certifikát, který odpovídá identifikátoru klíče subjektu, ale není ten, který má klient použít. Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obdrží zprávu a ověří podpis, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mapuje informace v nezamýšleným certifikátu X.509 sadu deklarací identity, které jsou jiné a potenciálně zvýšenými z co očekává klienta.  
  
 Toto riziko lze snížit odkaz X.509 certifikátu dalším způsobem, například pomocí <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Viz také  
 [Aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Odmítnutí služby](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Manipulaci](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
