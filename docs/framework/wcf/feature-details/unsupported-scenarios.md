---
title: Nepodporované scénáře
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: b643e6df8a877860ce36fc6ee34c4e4ca08ec748
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921162"
---
# <a name="unsupported-scenarios"></a>Nepodporované scénáře

Z různých důvodů nepodporuje Windows Communication Foundation (WCF) některé konkrétní scénáře zabezpečení. Například Windows XP Home Edition neimplementuje ověřovací protokoly SSPI nebo Kerberos, a proto WCF nepodporuje spouštění služby s ověřováním systému Windows na této platformě. Další mechanismy ověřování, jako je uživatelské jméno/heslo a integrované ověřování HTTP/HTTPS, se podporují při použití WCF v systému Windows XP Home Edition.

## <a name="impersonation-scenarios"></a>Scénáře zosobnění

### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Zosobněná identita možná není při provádění asynchronních volání vydávána klientem.
 Když klient služby WCF provede asynchronní volání služby WCF pomocí ověřování systému Windows v zosobnění, může dojít k ověřování pomocí identity klientského procesu namísto zosobněné identity.

### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Systém Windows XP a soubor cookie zabezpečeného tokenu kontextu povoleny

WCF nepodporuje zosobnění a <xref:System.InvalidOperationException> je vyvolána, pokud existují následující podmínky:

- Operační systém je Windows XP.

- Režim ověřování má za následek identitu Windows.

- Vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.OperationBehaviorAttribute> je nastavena na hodnotu <xref:System.ServiceModel.ImpersonationOption.Required>.

- Vytvoří se token kontextu zabezpečení založený na stavu (SCT) (ve výchozím nastavení je vytváření zakázané).

 SCT založenou na stavu lze vytvořit pouze pomocí vlastní vazby. Další informace najdete v tématu [Postup: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](how-to-create-a-security-context-token-for-a-secure-session.md).) V kódu je token povolen vytvořením elementu vazby zabezpečení (buď <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> metody a nastavením parametru `requireCancellation` na `false`. Parametr odkazuje na ukládání do mezipaměti pro SCT. Nastavením hodnoty na `false` povolíte funkci SCT založenou na stavu.

 Alternativně je v konfiguraci povolen token vytvořením <`customBinding`> a poté přidáním <`security`> elementu a nastavením atributu `authenticationMode` na hodnotu SecureConversation a `requireSecurityContextCancellation` atribut `true`.

> [!NOTE]
> Předchozí požadavky jsou specifické. Například <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> vytvoří prvek vazby, který má za následek identitu Windows, ale nevytvoří SCT. Proto ji můžete použít s možností `Required` v systému Windows XP.

### <a name="possible-aspnet-conflict"></a>Možný konflikt ASP.NET

WCF a ASP.NET můžou povolit nebo zakázat zosobnění. Když je ASP.NET hostitelem aplikace WCF, může mezi konfiguračními nastaveními WCF a ASP.NET existovat konflikt. V případě konfliktu má nastavení WCF přednost, pokud vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> nastavena na hodnotu <xref:System.ServiceModel.ImpersonationOption.NotAllowed>. v takovém případě má přednost nastavení ASP.NET zosobnění.

### <a name="assembly-loads-may-fail-under-impersonation"></a>Načtení sestavení může v zosobnění selhat.

Pokud zosobněný kontext nemá přístupová práva k načtení sestavení a je-li prvním modulem CLR (Common Language Runtime), který se pokouší načíst sestavení pro tuto doménu AppDomain, <xref:System.AppDomain> ukládá chybu do mezipaměti. Následné pokusy o načtení tohoto sestavení (nebo sestavení) selžou, dokonce i po vrácení zosobnění a i v případě, že má kontext vrácená přístupová práva k načtení sestavení. Důvodem je to, že modul CLR se znovu nepokusí o načtení po změně kontextu uživatele. Je nutné restartovat doménu aplikace pro zotavení po selhání.

> [!NOTE]
> Výchozí hodnota vlastnosti <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> třídy <xref:System.ServiceModel.Security.WindowsClientCredential> je <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Ve většině případů kontext zosobnění na úrovni identifikace nemá žádná práva k načtení dalších sestavení. Toto je výchozí hodnota, takže se jedná o velmi běžnou podmínku, kterou je třeba znát. K zosobnění na úrovni identifikace dojde také v případě, že proces zosobnění nemá oprávnění `SeImpersonate`. Další informace najdete v tématu [delegování a zosobnění](delegation-and-impersonation-with-wcf.md).

### <a name="delegation-requires-credential-negotiation"></a>Delegování vyžaduje vyjednávání přihlašovacích údajů

Chcete-li použít ověřovací protokol Kerberos s delegováním, je nutné implementovat protokol Kerberos s vyjednáváním přihlašovacích údajů (někdy označovaným jako multi-nohy nebo multi-step Kerberos). Pokud implementujete ověřování protokolu Kerberos bez vyjednávání přihlašovacích údajů (někdy nazývaného jednorázové rozhraní Kerberos), vyvolá se výjimka. Další informace o tom, jak implementovat vyjednávání pověření, najdete v tématu [ladění chyb ověřování systému Windows](debugging-windows-authentication-errors.md).

## <a name="cryptography"></a>Kryptografie

### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 se podporuje jenom pro použití symetrického klíče.

WCF podporuje nejrůznější algoritmy pro vytváření algoritmů šifrování a otisků podpisů, které můžete zadat pomocí sady algoritmů v rámci vazeb poskytovaných systémem. Pro lepší zabezpečení podporuje WCF algoritmy SHA (Secure Hash Algorithm) 2, konkrétně SHA-256, pro vytváření hodnot hash MD5 signatur. Tato verze podporuje SHA-256 jenom pro použití symetrického klíče, jako jsou klíče Kerberos, a kde se k podpisu zprávy nepoužívá certifikát X. 509. WCF nepodporuje signatury RSA (používané v certifikátech X. 509) pomocí algoritmu SHA-256 hash kvůli současnému nedostatku podpory RSA-SHA256 v WinFX.

### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Hodnoty hash SHA-256 kompatibilní se standardem FIPS nejsou podporovány.

Služba WCF nepodporuje hodnoty hash kompatibilní se standardem FIPS-256, takže sady algoritmů, které používají algoritmus SHA-256, nejsou podporovány službou WCF v systémech, kde je vyžadováno použití algoritmů kompatibilních se standardem FIPS.

### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Pokud upravíte registr, může dojít k selhání algoritmů kompatibilních se standardem FIPS.

Algoritmy kompatibilní se standardem FIPS (Federal Information Processing Standards) můžete povolit a zakázat pomocí modulu snap-in Místní nastavení zabezpečení konzoly Microsoft Management Console (MMC). Můžete také použít nastavení v registru. Všimněte si ale, že WCF nepodporuje použití registru k resetování nastavení. Pokud je hodnota nastavena na jinou hodnotu než 1 nebo 0, může dojít k nekonzistentním výsledkům mezi CLR a operačním systémem.

### <a name="fips-compliant-aes-encryption-limitation"></a>Omezení šifrování AES kompatibilní se standardem FIPS

Šifrování AES kompatibilní se standardem FIPS nefunguje v duplexních zpětných voláních v rámci zosobnění na úrovni identifikace.

### <a name="cngksp-certificates"></a>CNG/KSP – certifikáty

*Kryptografické rozhraní API: nové generace (CNG)* je dlouhodobá náhrada za rozhraní CryptoAPI. Toto rozhraní API je k dispozici v nespravovaném kódu v systémech Windows Vista, Windows Server 2008 a novějších verzích Windows.

 .NET Framework 4.6.1 a starší verze tyto certifikáty nepodporují, protože využívají starší rozhraní CryptoAPI ke zpracování certifikátů CNG/KSP. Použití těchto certifikátů s .NET Framework 4.6.1 a staršími verzemi způsobí výjimku.

 Existují dva možné způsoby, jak zjistit, jestli certifikát používá KSP:

- Proveďte `p/invoke` `CertGetCertificateContextProperty`a zkontrolujte `dwProvType` na vráceném `CertGetCertificateContextProperty`.

- Použijte příkaz `certutil` z příkazového řádku pro dotazování certifikátů. Další informace najdete v tématu [úlohy certutil při řešení potíží s certifikáty](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc772619(v=ws.10)).

## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Pokud se vyžaduje použití zosobnění ASP.NET a je vyžadována kompatibilita ASP.NET, zabezpečení zprávy se nezdařila.

Služba WCF nepodporuje následující kombinaci nastavení, protože může zabránit tomu, aby se ověřování klienta objevilo:

- Zosobnění ASP.NET je povoleno. To se provádí v souboru Web. config nastavením atributu `impersonate` <`identity`elementu > na `true`.

- Režim kompatibility ASP.NET je povolen nastavením atributu `aspNetCompatibilityEnabled` [\<serviceHostingEnvironment >](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) na `true`.

- Používá se zabezpečení režimu zpráv.

Rozhlasem je vypnutí režimu kompatibility ASP.NET. Nebo, pokud je vyžadován režim kompatibility ASP.NET, zakažte funkci zosobnění ASP.NET a místo ní použijte zosobnění poskytované WCF. Další informace najdete v tématu [delegování a zosobnění](delegation-and-impersonation-with-wcf.md).

## <a name="ipv6-literal-address-failure"></a>Chyba adresy literálu IPv6

Požadavky na zabezpečení selžou, pokud se klient a služba nacházejí ve stejném počítači a pro službu se používají adresy literálu IPv6.

 Pokud je služba a klient v různých počítačích, je adresa IPv6 literálů funkční.

## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Selhání načítání WSDL s federovaným vztahem důvěryhodnosti

WCF vyžaduje přesně jeden dokument WSDL pro každý uzel ve federovaném řetězu důvěryhodných certifikátů. Při zadávání koncových bodů buďte opatrní, abyste nevytvořili smyčku. Jedním ze způsobů, jak mohou nastat smyčky, je použití stažení WSDL řetězců federovaného vztahu důvěryhodnosti se dvěma nebo více odkazy ve stejném dokumentu WSDL. Běžným scénářem, který může způsobovat tento problém, je federované služba, ve které se server tokenu zabezpečení a služba nachází uvnitř stejné třídy ServiceHost.

 Příkladem této situace je služba s následujícími třemi adresami koncových bodů:

- `http://localhost/CalculatorService/service` (služba)

- `http://localhost/CalculatorService/issue_ticket` (STS)

- `http://localhost/CalculatorService/mex` (koncový bod metadat)

 Vyvolá výjimku.

 Tuto situaci můžete udělat tak, že umístíte koncový bod `issue_ticket` jinam.

## <a name="wsdl-import-attributes-can-be-lost"></a>Atributy importu WSDL se můžou ztratit.

Technologie WCF ztratí při importu WSDL sledování atributů prvku `<wst:Claims>` v šabloně `RST`. K tomu dojde během importu WSDL, pokud zadáte `<Claims>` přímo v `WSFederationHttpBinding.Security.Message.TokenRequestParameters` nebo `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` namísto použití kolekcí typu deklarace přímo.  Vzhledem k tomu, že import ztratí atributy, vazba nezaokrouhlí cestu správně prostřednictvím WSDL, a proto není na straně klienta správná.

 Opravou je změna vazby přímo na klientovi po provedení importu.

## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](security-considerations-in-wcf.md)
- [Zpřístupnění informací](information-disclosure.md)
- [Zvýšení oprávnění](elevation-of-privilege.md)
- [Útok DoS](denial-of-service.md)
- [Falšování](tampering.md)
- [Útoky opakováním](replay-attacks.md)
