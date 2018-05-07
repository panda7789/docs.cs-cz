---
title: Nepodporované scénáře
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 5cc4e65ce4f93a352b651203757a484a9d90a85d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="unsupported-scenarios"></a>Nepodporované scénáře
Z různých důvodů Windows Communication Foundation (WCF) nepodporuje některé scénáře konkrétní zabezpečení. Například [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition neimplementuje ověřovací protokoly SSPI nebo protokolu Kerberos, a proto WCF nepodporuje spuštěna služba pomocí ověřování systému Windows na této platformě. Další mechanismy ověřování, jako je například uživatelské jméno a heslo a integrované ověřování protokolu HTTP nebo HTTPS jsou podporovány při spuštění WCF pod Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Zosobnění scénáře  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Zosobněnou identitou může není toku, když klienti asynchronní volání  
 Pokud klienta WCF provede asynchronní volání služby WCF pomocí ověřování systému Windows v zosobnění, může dojít ověřování pomocí identity procesu klientů namísto zosobněnou identitou.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP a zabezpečené kontextu tokenu souboru Cookie povoleno  
 WCF nepodporuje zosobnění a <xref:System.InvalidOperationException> se vyvolá, když existují následující podmínky:  
  
-   Operační systém je [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Režim ověřování výsledkem identitu systému Windows.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute> je nastaven na <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Vytvoření tokenu kontextu zabezpečení na základě stavu (SCT) (ve výchozím nastavení, bude zakázáno vytváření).  
  
 SCT na základě stavu mohou být vytvořeny pouze použití vlastní vazby. Další informace najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) V kódu je povolena token vytvořením element vazby a zabezpečení (buď <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> metoda a nastavení `requireCancellation` parametru `false`. Parametr odkazuje na ukládání do mezipaměti SCT. Nastavení na hodnotu `false` povolí funkci SCT na základě stavu.  
  
 V konfiguraci, případně token je povoleno tak, že vytvoříte <`customBinding`>, pak přidávání <`security`> elementu a nastavení `authenticationMode` atribut SecureConversation a `requireSecurityContextCancellation` atribut `true`.  
  
> [!NOTE]
>  Požadavky na předchozí jsou konkrétní. Například <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> vytvoří element vazby, který má za následek identitu systému Windows, ale nevytváří SCT. Proto můžete použít je s `Required` možnost [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Možný konflikt ASP.NET  
 WCF a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] můžete i povolit nebo zakázat zosobnění. Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace WCF je hostitelem konflikt mohou existovat mezi WCF a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nastavení konfigurace. Nastavení WCF v případě konfliktu, má přednost před, pokud <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> je nastavena na <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, v takovém případě [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] přednost má nastavení zosobnění.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Zosobnění může při načítání sestavení  
 Pokud zosobněného kontextu nemá přístupová práva k načtení sestavení a pokud je první modul CLR (CLR) se pokouší o načtení sestavení pro tuto doménu AppDomain <xref:System.AppDomain> ukládá do mezipaměti selhání. Následné pokusy o načtení tohoto sestavení (nebo sestavení) nezdaří, i po vrácení zosobnění a to i v případě vrácený kontextu má přístupová práva k načtení sestavení. Je to proto, že modul CLR nebude znovu pokoušet zatížení po změně kontextu uživatele. Je nutné restartovat doménu aplikace pro obnovení po selhání.  
  
> [!NOTE]
>  Výchozí hodnota <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třída je <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Ve většině případů kontextu zosobnění identifikace úroveň nemá práva k načtení všech dalších sestavení. Toto je výchozí hodnota, to je velmi běžné podmínku, která má být vědomi. Identifikace úroveň zosobnění dojde i v případě zosobnění proces nemá `SeImpersonate` oprávnění. Další informace najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegování vyžaduje vyjednávání pověření  
 Pokud chcete používat ověřování protokolu Kerberos s delegováním, musí implementovat protokol Kerberos s vyjednávání pověření (někdy nazývané více větev nebo vícekrokový protokolu Kerberos). Pokud budete implementovat ověřování protokolem Kerberos bez vyjednávání pověření (někdy nazývané jednorázové nebo jedním větev protokolu Kerberos), je vyvolána výjimka. Další informace o tom, jak implementovat vyjednávání pověření najdete v tématu [ladění chyb ověřování systému Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Kryptografie  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>Algoritmus SHA-256 se podporuje jenom pro použití symetrického klíče  
 WCF podporuje celou řadu šifrování a podpis digest vytvoření algoritmy, které můžete zadat v sadě algoritmus vazby poskytované systémem. Pro lepší zabezpečení podporuje WCF Secure Hash Algorithm (SHA) 2 algoritmy, konkrétně SHA-256, pro vytvoření hodnoty hash podpisu digest. Tato verze podporuje SHA-256 pouze pro použití symetrického klíče, jako jsou klíče protokolu Kerberos, a kde se certifikát X.509 nepoužívá k podepsání zprávy. WCF nepodporuje RSA podpisy (používá se v certifikátech X.509) pomocí algoritmu hash SHA-256 z důvodu aktuálního nedostatečná podpora pro RSA-SHA256 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Kompatibilní se standardem FIPS hodnoty hash SHA-256 nepodporují  
 WCF nepodporuje hodnoty hash SHA-256 kompatibilní se standardem FIPS, takže algoritmus sady, které používají algoritmus SHA-256 nepodporují WCF v systémech, kdy je potřeba použít algoritmy splňující standard FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Kompatibilní se standardem FIPS algoritmy může selhat v případě úpravy registru  
 Můžete povolit nebo zakázat zpracování standardů FIPS (Federal Information) - algoritmus kompatibilní s použitím místní zabezpečení nastavení Microsoft Management Console (MMC) snap - v. Můžete taky přejít na nastavení v registru. Upozorňujeme však, že WCF nepodporuje pomocí klíče registru obnovte nastavení. Pokud je hodnota nastavena na jinou hodnotu než 1 nebo 0, nekonzistentní výsledky může proběhnout mezi modulu CLR a operační systém.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Omezení šifrování AES kompatibilní se standardem FIPS  
 Šifrování AES kompatibilní s FIPS v duplexní zpětná volání v úrovni zosobnění identifikace nefunguje.  
  
### <a name="cngksp-certificates"></a>Certifikáty CNG nebo KSP  
 *Cryptography API: Next Generation (CNG)* je dlouhodobé náhradou rozhraní CryptoAPI. Toto rozhraní API je k dispozici v nespravovaném kódu na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] a novějších verzích systému Windows.  
  
 Rozhraní .NET framework 4.6.1 a starší verze nepodporují tyto certifikáty, protože používají starší verzi rozhraní CryptoAPI pro zpracování CNG nebo KSP certifikáty. Použití těchto certifikátů pomocí rozhraní .NET Framework 4.6.1 a starší verze způsobí výjimku.  
  
 Existují dvě možné způsoby, jak zjistit, jestli certifikát používá KSP:  
  
-   Proveďte `p/invoke` z `CertGetCertificateContextProperty`a zkontrolovat `dwProvType` na vrácený `CertGetCertificateContextProperty`.  
  
-   Použití `certutil` příkazu z příkazového řádku pro dotazování certifikáty. Další informace najdete v tématu [Certutil úlohy pro řešení problémů s certifikáty](http://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Zpráva zabezpečení nezdaří, pokud pomocí zosobnění technologie ASP.NET a kompatibilitu s technologií ASP.NET se vyžaduje  
 WCF nepodporuje následující kombinace nastavení, protože zabraňují ověření klienta, ze které se vyskytují:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Je povoleno zosobnění. K tomu je potřeba v souboru Web.config nastavení `impersonate` atribut <`identity`> elementu, který chcete `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je povolený režim kompatibility nastavením `aspNetCompatibilityEnabled` atribut [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) k `true`.  
  
-   Režim zabezpečení zpráv se používá.  
  
 Řešení je k vypnutí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility. Nebo, pokud [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] je vyžadován režimu kompatibility, zakažte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zosobnění funkci a místo toho použijte zadaný WCF zosobnění. Další informace najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Selhání literálu adres IPv6  
 Požadavky na zabezpečení úspěšná, když klient a služba jsou na stejném počítači, a literálu adresy IPv6 se používají pro službu.  
  
 Literál IPv6 řeší pracovní, pokud klienta a služby jsou na různých počítačích.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Selhání načtení WSDL pomocí federovaného vztahu důvěryhodnosti  
 WCF vyžaduje přesně jeden dokument WSDL pro každý uzel v řetězu federovaný vztah důvěryhodnosti. Dejte pozor, abyste nastavit smyčku při zadávání koncové body. Jedním ze způsobů, ve kterém mohou vyplývat smyčky je pomocí dvou nebo více odkazů ve stejném dokumentu WSDL a WSDL stahování řetězy federovaný vztah důvěryhodnosti. Běžný scénář, který může vytvořit tento problém je federované služby, kde jsou serverem tokenu zabezpečení a službě obsaženy uvnitř stejné ServiceHost.  
  
 Příkladem takové situaci je služba s následující tři adresy koncových bodů:  
  
-   http://localhost/CalculatorService/service (dále jen "služba")  
  
-   http://localhost/CalculatorService/issue_ticket (STS)  
  
-   http://localhost/CalculatorService/mex (koncový bod metadat)  
  
 To vyvolá výjimku.  
  
 Můžete použít tento scénář fungovat umístěním `issue_ticket` jinde koncový bod.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL Import atributy mohou být ztraceno  
 WCF ztratí sledování atributů na `<wst:Claims>` element v `RST` šablony při importu WSDL. To se stane při importu WSDL, když zadáte `<Claims>` přímo v `WSFederationHttpBinding.Security.Message.TokenRequestParameters` nebo `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` místo přímo pomocí kolekce typů deklarací identity.  Vzhledem k tomu, že import ztratí atributy, vazba nemá odezvy správně prostřednictvím WSDL a proto je nesprávný na straně klienta.  
  
 Oprava je upravit vazby přímo v klientovi po provedení importu.  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
