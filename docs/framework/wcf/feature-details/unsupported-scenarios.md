---
title: Nepodporované scénáře
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 2e44cbf159d5df724a5213648b28d952f49b8e8d
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845675"
---
# <a name="unsupported-scenarios"></a>Nepodporované scénáře
Z různých důvodů Windows Communication Foundation (WCF) nepodporuje některé konkrétní bezpečnostní scénáře. Například [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition neimplementuje ověřovací protokoly SSPI nebo protokolu Kerberos, a proto WCF nepodporuje spouštění služby s ověřováním Windows na této platformě. Jiné ověřovací mechanismy, jako je například uživatelské jméno a heslo a integrované ověřování protokolu HTTP/HTTPS se nepodporuje při spuštění WCF v části Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Zosobnění scénáře  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Zosobněnou identitou může není tok, když klienti provádět asynchronní volání  
 Když klient WCF umožňuje asynchronní volání služeb WCF pomocí ověřování Windows v zosobnění, může dojít k ověření, s identitou procesu klienta místo zosobněnou identitou.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP a zabezpečené kontextu Token souboru Cookie povolené  
 WCF nepodporuje zosobnění a <xref:System.InvalidOperationException> je vyvolána při dodržení následujících podmínek:  
  
-   Operační systém je [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Režim ověřování výsledkem identita Windows.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute> je nastavena na <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Vytvoří token kontextu zabezpečení na základě stavu (SCT) (ve výchozím nastavení, je zakázáno vytváření).  
  
 Základě stavu SCT lze vytvořit pouze použití vlastní vazby. Další informace najdete v tématu [postupy: vytvoření Token kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) V kódu, je tak, že vytvoříte element vazby zabezpečení povoleno token (buď <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> metoda a nastavení `requireCancellation` parametr `false`. Parametr odkazuje na ukládání do mezipaměti SCT. Nastavením této hodnoty na `false` povolí tuto funkci SCT na základě stavu.  
  
 V konfiguraci, případně token je povoleno tak, že vytvoříte <`customBinding`>, následným přidáním <`security`> element a nastavení `authenticationMode` atribut SecureConversation a `requireSecurityContextCancellation` atribut `true`.  
  
> [!NOTE]
>  Předchozí požadavky jsou specifické. Například <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> vytvoří element vazby, která má za následek Windows identity, ale nevytváří SCT. Proto ji můžete použít `Required` možnost [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Konfliktům technologie ASP.NET  
 WCF a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] můžete jak povolit nebo zakázat zosobnění. Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace WCF je hostitelem ke konfliktu může existovat mezi WCF a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nastavení konfigurace. V případě konfliktu, nastavení WCF má přednost, pokud <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> je nastavena na <xref:System.ServiceModel.ImpersonationOption.NotAllowed>v takovém případě [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] přednost má nastavení zosobnění.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Načítání sestavení může selhat v zosobnění  
 Pokud zosobněného kontextu nemá přístupová práva k načtení sestavení a pokud je první common language runtime (CLR) se pokouší načíst sestavení pro tuto doménu AppDomain, <xref:System.AppDomain> ukládá do mezipaměti selhání. Následné pokusy o načtení tohoto sestavení (nebo sestavení) nezdaří, i po vrácení zosobnění a i když vrácený kontext má přístupová práva k načtení sestavení. Je to proto, že modul CLR nebude znovu pokoušet zatížení po změně kontextu uživatele. Je nutné restartovat aplikační domény na obnovení po chybě.  
  
> [!NOTE]
>  Výchozí hodnota <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třída je <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Ve většině případů objekt context identifikace úroveň zosobnění nemá žádná práva k načtení žádné další sestavení. Toto je výchozí hodnota, tohle je velmi běžné podmínku je potřeba vědět. Identifikace úroveň zosobnění také nastane, pokud proces zosobnění nemá `SeImpersonate` oprávnění. Další informace najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegování vyžaduje vyjednávání přihlašovacích údajů  
 Delegování používat ověřování protokolu Kerberos, musí implementovat protokol Kerberos s vyjednávání přihlašovacích údajů (říká se jim více větev nebo vícekrokové protokolu Kerberos). Pokud se rozhodnete implementovat ověřování protokolem Kerberos bez vyjednávání přihlašovacích údajů (říká se jim konečný nebo jedné fáze Kerberos), je vyvolána výjimka. Další informace o tom, jak implementovat vyjednávání přihlašovacích údajů najdete v tématu [ladění chyby s ověřováním Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Kryptografie  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 se podporuje jenom pro použití symetrického klíče  
 WCF podporuje širokou škálu šifrování a podpis digest vytváření algoritmy, které můžete zadat pomocí sadu algoritmů v vazeb poskytovaných systémem. Pro důkladnější zabezpečení WCF podporuje algoritmy zabezpečení hashovací algoritmus (SHA) 2, konkrétně SHA-256, pro vytvoření hodnoty hash podpisu digest. Tato verze podporuje SHA-256 pouze pro použití symetrického klíče, jako jsou klíče protokolu Kerberos, a pokud se certifikát X.509, který nepoužívá k podepisování zpráv. WCF nepodporuje podpisy RSA (používá se v certifikátech X.509) při použití hodnoty hash SHA-256 kvůli aktuální chybějící podpora pro RSA-SHA256 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Kompatibilní se standardem FIPS hodnoty hash SHA-256 není podporován  
 WCF nepodporuje hodnoty hash SHA-256 kompatibilní se standardem FIPS, takže algoritmus sad, které používají algoritmus SHA-256 nepodporují službou WCF na systémech, kde je nutné používat algoritmy splňující standard FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Při úpravě registru může dojít k selhání algoritmy odpovídající standardu FIPS  
 Můžete povolit nebo zakázat informace o zpracování normy FIPS (Federal) - algoritmy odpovídající s použitím místní zabezpečení nastavení Microsoft Management Console (MMC) snap - v. Můžete také přístup k nastavení v registru. Upozorňujeme však, že WCF nepodporuje použití obnovte nastavení registru. Pokud je hodnota nastavena na jinou hodnotu než 1 nebo 0, nekonzistentní výsledky mohla probíhat CLR a operačního systému.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Omezení šifrování AES kompatibilní se standardem FIPS  
 Šifrování AES kompatibilní s FIPS v duplexní zpětná volání v úrovni zosobnění identifikace nefunguje.  
  
### <a name="cngksp-certificates"></a>Certifikátů CNG/KSP  
 *Cryptography API: Next Generation (CNG)* dlouhodobé nahrazuje rozhraní CryptoAPI. Toto rozhraní API je k dispozici v nespravovaném kódu na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] a novějších verzích Windows.  
  
 Rozhraní .NET framework 4.6.1 a starší verze nepodporují tyto certifikáty, protože používají starší verzi rozhraní CryptoAPI pro zpracování certifikátů CNG/KSP. Použití těchto certifikátů pomocí rozhraní .NET Framework 4.6.1 a dřívějších verzích způsobí výjimku.  
  
 Existují dva možné způsoby, jak zjistit, pokud certifikát využívá KSP:  
  
-   Proveďte `p/invoke` z `CertGetCertificateContextProperty`a zkontrolujte `dwProvType` na vrácený `CertGetCertificateContextProperty`.  
  
-   Použití `certutil` příkazu z příkazového řádku pro dotazování na certifikáty. Další informace najdete v tématu [úkoly programu Certutil pro řešení problémů s certifikáty](https://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Zpráva zabezpečení nezdaří, pokud pomocí zosobnění technologie ASP.NET a režim kompatibility ASP.NET je vyžadován  
 WCF nepodporuje následující kombinaci nastavení, protože nebrání ověření klienta před:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Je povoleno zosobnění. To se provádí v souboru Web.config tak, že nastavíte `impersonate` atribut <`identity`> element `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režim kompatibility se povoluje nastavením `aspNetCompatibilityEnabled` atribut [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) k `true`.  
  
-   Režim zabezpečení zprávy se používá.  
  
 Vyřešit se vypnout [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režim kompatibility. Nebo, pokud [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] se vyžaduje režim kompatibility, zakažte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zosobnění běží na procesorech a místo toho použijte zosobnění poskytované WCF. Další informace najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Selhání literálu adresu IPv6  
 Požadavky na zabezpečení nezdaří, pokud klient a služba se ve stejném počítači, a literál adresy IPv6 se používají pro službu.  
  
 Literál IPv6 adresy práce, pokud klienta a služby jsou na různých strojích.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Selhání načtení WSDL pomocí federovaného vztahu důvěryhodnosti  
 WCF vyžaduje právě jeden dokument WSDL pro každý uzel v řetězci federovaný vztah důvěryhodnosti. Dejte pozor, abyste nastavili smyčku při určení koncových bodů. Jedním ze způsobů, ve kterém mohou vyplývat smyčky je stažení WSDL řetězců federovaný vztah důvěryhodnosti pomocí dvou nebo více odkazů v jednom dokumentu WSDL. Běžný scénář, které mohou způsobit potíže je federované služby, kde jsou obsaženy Server Token zabezpečení a službě uvnitř stejného hostitele ServiceHost.  
  
 Příklad této situace je služba s následující tři adresy koncových bodů:  
  
- `http://localhost/CalculatorService/service` (služba)  
  
- `http://localhost/CalculatorService/issue_ticket` (STS)  
  
- `http://localhost/CalculatorService/mex` (koncový bod metadat)  
  
 Tím dojde k výjimce.  
  
 Provedete tento scénář fungovat tak, že vložíte `issue_ticket` koncový bod jinde.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Atributy pro Import WSDL může být ztraceno  
 WCF ztratí sledování atributů na `<wst:Claims>` prvek `RST` šablony při importu WSDL. To se stane při importu WSDL, když zadáte `<Claims>` přímo v `WSFederationHttpBinding.Security.Message.TokenRequestParameters` nebo `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` přímo namísto kolekce typů deklarací identity.  Protože importu ztratí atributy, vazba není odezvy správně prostřednictvím WSDL a je nesprávné na straně klienta.  
  
 Oprava je upravte vazbu přímo v klientovi po provedení importu.  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
