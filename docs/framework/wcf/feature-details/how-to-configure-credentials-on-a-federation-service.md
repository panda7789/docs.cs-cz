---
title: 'Postupy: Konfigurace pověření ve službě Federation Service'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 33df685b4d14130ae00d59012706b7637924c9be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699833"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Postupy: Konfigurace pověření ve službě Federation Service
Ve Windows Communication Foundation (WCF), vytvoření federovaného služby se skládá z následujících hlavních kroků:  
  
1. Konfigurace <xref:System.ServiceModel.WSFederationHttpBinding> nebo podobné vlastní vazby. Další informace o vytváření příslušnou datovou vazbu najdete v tématu [jak: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Konfigurace <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> , která určuje, jak vydané tokeny, které se zobrazí ve službě jsou ověřeni.  
  
 Toto téma obsahuje podrobné informace o druhém kroku. Další informace o tom, jak funguje federované služby najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Chcete-li nastavit vlastnosti IssuedTokenServiceCredential v kódu  
  
1. Použití <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> vlastnost <xref:System.ServiceModel.Description.ServiceCredentials> třídy vrátit odkaz na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> instance. Vlastnost přistupuje z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost <xref:System.ServiceModel.ServiceHostBase> třídy.  
  
2. Nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> vlastnost `true` Pokud samostatně vydané tokeny [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty jsou k ověření. Výchozí hodnota je `false`.  
  
3. Naplnění kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastnost s instancí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy. Jednotlivé instance představují vystavitele, ze kterého bude služba ověřovat tokeny.  
  
    > [!NOTE]
    >  Na rozdíl od klientů kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost kolekce známých certifikátů není kolekci s klíčem. Služba přijímá tokeny, které zadané certifikáty vydávat bez ohledu na adresu klienta, který odeslal zprávu obsahující vydaný token (v souladu s další omezení, které jsou popsány dále v tomto tématu).  
  
4. Nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> vlastnost na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnot výčtu. To lze provést pouze v kódu. Výchozí hodnota je <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Pokud <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> je nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, přiřaďte instanci vlastní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídu <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnost.  
  
6. Pokud <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> je nastavena na `ChainTrust` nebo `PeerOrChainTrust`, nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> vlastnost na odpovídající hodnotu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> výčtu. Všimněte si, že režim odvolání se nepoužívá v `PeerTrust` nebo `Custom` režimy ověřování.  
  
7. V případě potřeby přiřadit instanci vlastního <xref:System.IdentityModel.Tokens.SamlSerializer> třídu <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> vlastnost. Uživatelský serializátor zabezpečení kontrolní výrazy SAML (Markup Language) je potřeba například pro analýzu vlastní kontrolní výrazy SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Chcete-li nastavit vlastnosti IssuedTokenServiceCredential v konfiguraci  
  
1. Vytvoření `<issuedTokenAuthentication>` jako podřízený element <`serviceCredentials`> element.  
  
2. Nastavte `allowUntrustedRsaIssuers` atribut `<issuedTokenAuthentication>` elementu `true` Pokud vystavený token, jako například ověřování [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty.  
  
3. Vytvoření `<knownCertificates>` element jako podřízený objekt `<issuedTokenAuthentication>` elementu.  
  
4. Vytvoření nula nebo více `<add>` prvků jako podřízených prvků `<knownCertificates>` prvek a určete, jak vyhledat certifikát pomocí `storeLocation`, `storeName`, `x509FindType`, a `findValue` atributy.  
  
5. V případě potřeby nastavte `samlSerializer` atribut <`issuedTokenAuthentication`> element názvu typu vlastního <xref:System.IdentityModel.Tokens.SamlSerializer> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví vlastnosti <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> v kódu.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 V pořadí pro federované služby pro ověření klienta musí být vydaný token splněné následující podmínky:  
  
- Pokud digitální podpis vydaný token využívá klíče identifikátor zabezpečení RSA <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> musí být vlastnost `true`.  
  
- Při podpisu vydaný token používá X.509 vystavitele sériové číslo, identifikátor klíče subjektu X.509 nebo identifikátor zabezpečení kryptografický otisk X.509, vydaný token musí být podepsané certifikátem v kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastnost <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>třídy.  
  
- Když vydaný token je podepsaná pomocí certifikátu X.509, certifikát musí ověřit na sémantiku zadaný hodnotou <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost, bez ohledu na to, zda certifikát byla odeslána k předávající straně jako <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> nebo byl získán z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastnost. Další informace o ověřování certifikátů X.509 naleznete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Například nastavení <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> k <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> by ověřit jakékoli vydaný token, jehož podpisový certifikát se nachází ve `TrustedPeople` úložiště certifikátů. V takovém případě nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> vlastnost buď <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> nebo <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Můžete vybrat jiné režimy, včetně <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Když `Custom` je vybrali, je nutné přiřadit instanci <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídu <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> vlastnost. Vlastní validátor můžete ověřit certifikáty pomocí všechna kritéria, která vlastní stavový objekt. Další informace najdete v tématu [jak: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Viz také:

- [Federace](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federace a důvěryhodnost](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
