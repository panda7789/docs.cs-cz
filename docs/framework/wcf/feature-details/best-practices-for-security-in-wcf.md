---
title: Doporučené postupy pro zabezpečení ve WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c8c0c084ac3b1cf06fc5f2b3df85fa979744e17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185423"
---
# <a name="best-practices-for-security-in-wcf"></a>Doporučené postupy pro zabezpečení ve WCF
V následujících částech jsou uvedeny osvědčené postupy, které je třeba vzít v úvahu při vytváření zabezpečených aplikací pomocí služby Windows Communication Foundation (WCF). Další informace o zabezpečení naleznete v [tématech Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), Důležité informace o zabezpečení [dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)a [Aspekty zabezpečení s metadaty](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identifikace služeb provádějících ověřování systému Windows pomocí přemrštitelné sítě  
 Služby lze identifikovat buď s hlavními názvy uživatelů (UPN) nebo hlavní názvy služeb (SPN). Služby spuštěné pod účty počítače, jako je například síťová služba, mají identitu hlavního síťového připojení odpovídající počítači, který jsou spuštěny. Služby spuštěné pod uživatelskými účty mají identitu hlavního uživatele `setspn` odpovídající uživateli, jako je uživatel, i když nástroj lze použít k přiřazení hlavního název služby k uživatelskému účtu. Konfigurace služby tak, aby ji bylo možné identifikovat prostřednictvím hlavního serveru služeb pro připojení k síti A konfigurace klientů, kteří se připojují ke službě tak, aby tuto službu SPN mohla ztížit určité útoky. Tento návod se vztahuje na vazby pomocí Kerberos nebo SSPI vyjednávání.  Klienti by měli stále zadat hlavní výdělečnou hodnotu v případě, že sspi spadá zpět do NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Ověření identit služby v wsdl  
 WS-SecurityPolicy umožňuje službám publikovat informace o svých vlastních identitách v metadatech. Při načítání `svcutil` prostřednictvím nebo <xref:System.ServiceModel.Description.WsdlImporter>jiné metody, jako je například , tyto informace o identitě je přeložen do vlastností identity adresy koncového bodu služby WCF. Klienti, kteří neověřují, že tyto identity služby jsou správné a platné, účinně obejít ověřování služby. Škodlivá služba může tyto klienty zneužít ke spuštění předávání přihlašovacích údajů a dalších útoků "man in the middle" změnou identity nárokované v jeho WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Místo NTLM použijte certifikáty X509  
 WCF nabízí dva mechanismy pro ověřování mezi dvěma účastníky: certifikáty X509 (používané rovnocenným kanálem) a ověřování systému Windows, kde se vyjednávání SSPI snižuje z protokolu Kerberos na NTLM.  Ověřování pomocí klíčů o velikosti 1024 bitů nebo více je upřednostňováno před protokolem NTLM z několika důvodů:  
  
- dostupnost vzájemného ověřování pravosti,  
  
- používání silnějších kryptografických algoritmů a  
  
- větší obtížnost využití předávaných pověření X509.  

## <a name="always-revert-after-impersonation"></a>Vždy vrátit po zosobnění  
 Při použití api, které umožňují zosobnění klienta, nezapomeňte se vrátit k původní identity. Například při použití <xref:System.Security.Principal.WindowsIdentity> <xref:System.Security.Principal.WindowsImpersonationContext>a , použijte `using` c# příkaz`Using` nebo příkaz jazyka Visual Basic, jak je znázorněno v následujícím kódu. Třída <xref:System.Security.Principal.WindowsImpersonationContext> implementuje <xref:System.IDisposable> rozhraní a proto modul CLR (COMMON Language runtime) se automaticky vrátí `using` k původní identitě, jakmile kód opustí blok.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Zosobnit pouze podle potřeby  
 Pomocí <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody třídy <xref:System.Security.Principal.WindowsIdentity> je možné použít zosobnění ve velmi řízeném oboru. To je na rozdíl <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> od <xref:System.ServiceModel.OperationBehaviorAttribute>použití vlastnosti , která umožňuje zosobnění pro rozsah celé operace. Kdykoli je to možné, řídit rozsah zosobnění pomocí přesnější <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Získání metadat z důvěryhodných zdrojů  
 Ujistěte se, že důvěřujete zdroji metadat a ujistěte se, že s nimi nikdo nemanipuloval. Metadata načtená pomocí protokolu HTTP jsou odesílána ve prostém textu a lze s nimi manipulovat. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti a, použijte adresu URL dodanou tvůrcem služby ke stažení dat pomocí protokolu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikovat metadata pomocí zabezpečení  
 Chcete-li zabránit manipulaci s publikovanými metadaty služby, zabezpečte koncový bod výměny metadat pomocí zabezpečení přenosu nebo na úrovni zprávy. Další informace naleznete v [tématu Publikování koncových bodů metadat](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) a [postup: Publikování metadat pro službu pomocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Zajistit použití místního vystavitra  
 Pokud je pro danou vazbu zadána adresa vystavitvystavitea a vazba, místní vystavitel se nepoužívá pro koncové body, které tuto vazbu používají. Klienti, kteří očekávají, že budou vždy používat místního vystavittele, by měli zajistit, aby takovou vazbu nepoužívali nebo aby vazbu upravili tak, aby adresa vystavittele byla null.  
  
## <a name="saml-token-size-quotas"></a>Kvóty velikosti tokenu SAML  
 Pokud jsou tokeny jazyka tokenů s výrazy zabezpečení značkovací jazyk (SAML) serializovány ve zprávách, buď při jejich vydání službou TOKEN služby zabezpečení (STS), nebo když je klienti prezentují službám jako součást ověřování, musí být kvóta maximální velikosti zprávy dostatečně velké pro token SAML a další části zprávy. V normálních případech jsou dostatečné výchozí kvóty velikosti zprávy. Však v případech, kdy token SAML je velký, protože obsahuje stovky deklarací identity, kvóty by měly být zvýšeny tak, aby vyhovovaly serializovaný token. Další informace o kvótách naleznete v [tématu Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Nastavit SecurityBindingElement.IncludeTimestamp na True na vlastní vazby  
 Při vytváření vlastní vazby je <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> `true`nutné nastavit na . V opačném <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> případě, `false`pokud je nastavena na , a klient používá asymetrický token založený na klíči, jako je například certifikát X509, zpráva nebude podepsána.  
  
## <a name="see-also"></a>Viz také

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Důležité informace o zabezpečení pro data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)
- [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
