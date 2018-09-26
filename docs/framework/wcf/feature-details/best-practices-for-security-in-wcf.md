---
title: Doporučené postupy pro zabezpečení ve WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
author: BrucePerlerMS
ms.openlocfilehash: a45ec6b5cdd241cb92069e8097bc94baa65b2166
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075620"
---
# <a name="best-practices-for-security-in-wcf"></a>Doporučené postupy pro zabezpečení ve WCF
V následujících částech jsou osvědčené postupy, které je třeba zvážit při vytváření zabezpečených aplikací pomocí služby Windows Communication Foundation (WCF). Další informace o zabezpečení najdete v tématu [aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), a [informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identifikace služeb ověřování Windows s hlavní názvy služby  
 Služby lze identifikovat s hlavní názvy uživatelů (UPN) nebo hlavní názvy služby (SPN). Služby spuštěné pod účty počítače, například Síťová služba mají hlavní název služby identity odpovídající počítač, na kterém běží. Služby spuštěné v rámci uživatelské účty mají identita UPN odpovídající uživatel spuštěnými jako, i když `setspn` nástroj je možné přiřadit název SPN pro uživatelský účet. Konfigurace služby, tak ho lze identifikovat pomocí hlavního názvu služby a konfiguraci klientů připojuje ke službě, aby používali tuto hlavního názvu služby mohl provádět určité útokům obtížnější. Tento návod se vztahuje na vazby, které používají vyjednávání protokolu Kerberos nebo SSPI.  Klienti byste specifikovat název SPN v případě, kdy SSPI spadne zpět na protokol NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Ověření identity služby ve WSDL  
 WS-SecurityPolicy umožňuje službám pro zveřejnění informací o svoje vlastní identity v metadatech. Při načítání prostřednictvím `svcutil` nebo jiné metody, jako <xref:System.ServiceModel.Description.WsdlImporter>, tato informace o identitě se přeloží na vlastnosti identity adresy koncových bodů služby WCF. Klientů, kteří Neověřovat, že tyto identity služby jsou správné a platný efektivně se nebude používat ověřování služby. Škodlivé služby budou moci zneužít tyto klienty k provedení předávání přihlašovacích údajů a dalších útoků "man in the middle" tak, že změníte identitu uplatněné ve své WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Používat X509 certifikáty místo protokolu NTLM  
 WCF nabízí dva mechanismy ověřování peer-to-peer: X509 certifikáty (používané protokolu peer channel) a ověřování Windows, ve kterém vyjednávání SSPI změní úroveň z protokolu Kerberos k ověřování NTLM.  Ověřování pomocí certifikátů pomocí velikostí klíče 1 024 bitů nebo více je upřednostňována před NTLM z několika důvodů:  
  
-   dostupnost vzájemného ověřování  
  
-   Použijte silnější kryptografické algoritmy a  
  
-   větší potíže využití předané X509 přihlašovací údaje.  
   
## <a name="always-revert-after-impersonation"></a>Po zosobnění se vždycky vrátit  
 Při použití rozhraní API vám umožní zosobnění klienta, je potřeba vrátit zpět na původní identitu. Například při použití <xref:System.Security.Principal.WindowsIdentity> a <xref:System.Security.Principal.WindowsImpersonationContext>, pomocí C# `using` příkazu nebo Visual Basic`Using` příkaz, jak je znázorněno v následujícím kódu. <xref:System.Security.Principal.WindowsImpersonationContext> Implementuje třída <xref:System.IDisposable> rozhraní a proto common language runtime (CLR) se automaticky vrátí původní identitu jakmile opustí kód `using` bloku.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Zosobnění pouze v případě potřeby  
 Použití <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metodu <xref:System.Security.Principal.WindowsIdentity> třídy, je možné použít zosobnění ve velmi řízené oboru. To se liší od použití <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute>, který umožňuje zosobnění pro obor celá operace. Kdykoli je to možné, řízení rozsahu zosobnění s použitím více přesné <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metody.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Získat Metadata z důvěryhodných zdrojů  
 Ujistěte se, že důvěřujete jeho zdroji metadata a ujistěte se, že nikdo nemanipuloval s metadaty. Metadata načten pomocí protokolu HTTP se odesílá ve formátu prostého textu a mohou být změněny. Pokud služba používá <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> vlastnosti, použijte adresu URL poskytnutou Tvůrce služby ke stahování dat pomocí protokolu HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publikování metadat pomocí zabezpečení  
 Chcete-li zabránit manipulaci s publikovaných metadat služby, zabezpečený koncový bod metadat exchange s přenosu nebo zabezpečení na úrovni zprávy. Další informace najdete v tématu [publikování kocových bodů metadat](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) a [postupy: publikování metadat služby pomocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Zkontrolujte použití místního vystavitele  
 Případného vystavitele adresu a vazbu jsou pro danou vazbu lokálního vystavitele se nepoužije pro koncové body, které tuto vazbu používají. Klienti, kteří očekávají, že vždy používejte lokálního vystavitele zajistil nepoužívají takovou vazbu nebo jejich změňte vazbu tak, aby adresa Vystavitel je null.  
  
## <a name="saml-token-size-quotas"></a>Kvóty velikost tokenu SAML  
 Při tokeny zabezpečení kontrolní výrazy SAML (Markup Language) serializují ve zprávách, když jsou vydány službou tokenu služby zabezpečení (STS) nebo když se klienti k dispozici je ke službám jako součást ověření, maximální kvóta velikosti zprávy musí být dostatečně k tomuto tokenu SAML a další části zprávy dostačující. V případech, normální postačí výchozí kvóty velikosti zprávy. Ale v případech, kdy je SAML token velké vzhledem k tomu, že obsahuje stovky deklarace identity, kvót by měl být skutečnost zohlednit zvýšením serializovaný token. Další informace o kvótách najdete v tématu [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>SecurityBindingElement.IncludeTimestamp nastavena na hodnotu True na vlastních vazeb  
 Při vytváření vlastní vazby, je nutné nastavit <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> k `true`. Jinak, pokud <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> je nastavena na `false`, a že klient používá asymetrické na základě klíčů token jako je například x X509 certifikát, zprávy nebude podepsán.  
  
## <a name="see-also"></a>Viz také  
 [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [Informace o zabezpečení metadat](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
