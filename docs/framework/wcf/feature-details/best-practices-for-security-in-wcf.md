---
title: Doporučené postupy pro zabezpečení ve WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
ms.openlocfilehash: c99ab5e1e72aefc688df1692091e60caf930d5e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597615"
---
# <a name="best-practices-for-security-in-wcf"></a>Doporučené postupy pro zabezpečení ve WCF
V následujících částech jsou uvedeny osvědčené postupy při vytváření zabezpečených aplikací pomocí Windows Communication Foundation (WCF). Další informace o zabezpečení najdete v tématu [požadavky](security-considerations-in-wcf.md)na zabezpečení, [požadavky na zabezpečení pro data](security-considerations-for-data.md)a [bezpečnostní hlediska s metadaty](security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identifikace služeb, které provádějí ověřování systému Windows pomocí hlavních názvů služby  
 Služby je možné identifikovat buď pomocí hlavního názvu uživatele (UPN) nebo hlavních názvů služby (SPN). Služby spuštěné v rámci účtů počítačů, jako je třeba síťová služba, mají identitu hlavního názvu služby odpovídající počítači, na kterém běží. Služby spuštěné v rámci uživatelských účtů mají identitu hlavního názvu uživatele (UPN) odpovídající uživateli, pod kterým běží, i když `setspn` Nástroj lze použít k přiřazení hlavního názvu služby (SPN) k uživatelskému účtu. Konfigurace služby, aby se mohla identifikovat přes hlavní název služby (SPN) a konfigurace klientů připojujících se ke službě k používání tohoto hlavního názvu služby (SPN) může ztížit určité útoky. Tento návod se vztahuje na vazby pomocí protokolu Kerberos nebo vyjednávání SSPI.  Klienti musí pořád určovat hlavní název služby (SPN) v případě, že se rozhraní SSPI vrátí do protokolu NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Ověření identit služby v jazyce WSDL  
 WS-SecurityPolicy umožňuje službám publikovat informace o vlastních identitách v metadatech. Při načítání prostřednictvím `svcutil` nebo jiných metod, jako jsou <xref:System.ServiceModel.Description.WsdlImporter> tyto informace o identitě přeloženy na vlastnosti identity adres koncového bodu služby WCF. Klienti, kteří neověřují, zda jsou tyto identity služby správné a účinně obcházejí ověřování služby. Škodlivá Služba může tyto klienty zneužít ke spouštění předávání přihlašovacích údajů a dalších "muž v prostředních" útokech změnou identity deklarované v jejím WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Použít certifikáty x509 místo protokolu NTLM  
 WCF nabízí dva mechanismy pro ověřování peer-to-peer: certifikáty x509 (používané rovnocenným kanálem) a ověřování systému Windows, kde se vyjednávání SSPI odchází z protokolu Kerberos na NTLM.  Ověřování založené na certifikátech s použitím velikostí klíčů 1024 bitů nebo více se upřednostňuje na NTLM z několika důvodů:  
  
- dostupnost vzájemného ověřování,  
  
- použití silnějších kryptografických algoritmů a  
  
- větší obtížnost použití předávaných přihlašovacích údajů x509.  

## <a name="always-revert-after-impersonation"></a>Vždy vrátit po zosobnění  
 Pokud používáte rozhraní API, která umožňují zosobnění klienta, nezapomeňte se vrátit k původní identitě. Například při použití <xref:System.Security.Principal.WindowsIdentity> a <xref:System.Security.Principal.WindowsImpersonationContext> použijte příkaz jazyka C# `using` nebo `Using` příkaz Visual Basic, jak je znázorněno v následujícím kódu. <xref:System.Security.Principal.WindowsImpersonationContext>Třída implementuje <xref:System.IDisposable> rozhraní, a proto modul CLR (Common Language Runtime) automaticky vrátí původní identitu, jakmile kód opustí `using` blok.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Zosobnit pouze podle potřeby  
 Pomocí <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody <xref:System.Security.Principal.WindowsIdentity> třídy je možné použít zosobnění v velmi kontrolovaném oboru. To je na rozdíl od použití <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnosti <xref:System.ServiceModel.OperationBehaviorAttribute> , která umožňuje zosobnění pro rozsah celé operace. Kdykoli je to možné, řízení rozsahu zosobnění pomocí přesnější <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Získání metadat z důvěryhodných zdrojů  
 Ujistěte se, že důvěřujete zdroji metadat a zajistěte, aby žádná z nich nebyla úmyslně poškozená s metadaty. Metadata získaná pomocí protokolu HTTP se odesílají ve formátu prostého textu a můžou být poškozená. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti a, použijte adresu URL poskytnutou funkcí Tvůrce služby ke stažení dat pomocí protokolu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikování metadat pomocí zabezpečení  
 Aby nedocházelo k manipulaci s publikovanými metadaty služby, zabezpečte koncový bod výměny metadat pomocí přenosu nebo zabezpečení na úrovni zprávy. Další informace najdete v tématech [publikování koncových bodů metadat](../publishing-metadata-endpoints.md) a [Postupy: publikování metadat pro službu pomocí kódu](how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Zajistěte použití místního vystavitele.  
 Pokud je pro danou vazbu zadána adresa vystavitele a vazba, místní vystavitel není použit pro koncové body, které používají tuto vazbu. Klienti, kteří očekávají, že by vždy používali místního vystavitele, by měli zajistit, aby nepoužívali takovou vazbu ani nezměnili vazbu tak, že adresa vystavitele je null.  
  
## <a name="saml-token-size-quotas"></a>Kvóty pro velikost tokenu SAML  
 Pokud jsou ve zprávách serializovány tokeny jazyka SAML (Security Assert Markup Language), buď když jsou vydávány službou tokenů zabezpečení (STS), nebo když je klienti prezentují službám v rámci ověřování, maximální kvóta velikosti zprávy musí být dostatečně velká, aby se vešlo na token SAML a ostatní části zprávy. V normálních případech jsou dostatečné výchozí kvóty velikosti zprávy. V případech, kdy je token SAML velký, protože obsahuje stovky deklarací, se kvóty musí zvýšit tak, aby vyhovovaly serializovanému tokenu. Další informace o kvótách najdete v tématu věnovaném [bezpečnostním hlediskům pro data](security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Pro vlastní vazby nastavte SecurityBindingElement. IncludeTimestamp na true.  
 Při vytváření vlastní vazby je nutné nastavit <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> na `true` . V opačném případě, pokud <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> je nastaven na `false` a klient používá asymetrický klíč založený na klíči, jako je například certifikát x509, zpráva nebude podepsána.  
  
## <a name="see-also"></a>Viz také

- [Otázky zabezpečení](security-considerations-in-wcf.md)
- [Důležité informace o zabezpečení pro data](security-considerations-for-data.md)
- [Informace o zabezpečení metadat](security-considerations-with-metadata.md)
