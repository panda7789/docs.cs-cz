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
ms.openlocfilehash: 5bfea40a500dc1355b439ae7d949b0d96d3ab08c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495606"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Postupy: Konfigurace pověření ve službě Federation Service
Ve Windows Communication Foundation (WCF), vytváření federované služby se skládá z následujících postupů hlavní:  
  
1.  Konfigurace <xref:System.ServiceModel.WSFederationHttpBinding> nebo podobné vlastní vazby. Další informace o vytváření odpovídající vazby, najdete v části [postupy: vytvoření třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2.  Konfigurace <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> který určuje, jak vystavené tokeny, které jsou uvedené ve službě jsou ověřeni.  
  
 Toto téma obsahuje podrobné informace o druhém kroku. Další informace o fungování federované služby najdete v tématu [Federation](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Chcete-li nastavit vlastnosti IssuedTokenServiceCredential v kódu  
  
1.  Použití <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> vlastnost <xref:System.ServiceModel.Description.ServiceCredentials> třídy vrátíte odkaz na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> instance. Vlastnost je k němu přistupovat z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost <xref:System.ServiceModel.ServiceHostBase> třídy.  
  
2.  Nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> vlastnost `true` Pokud samoobslužné vystavené tokeny [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty jsou ověřovány. Výchozí hodnota je `false`.  
  
3.  Naplnění kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastnost s instancí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy. Jednotlivé instance představují vystavitele ze kterého bude služba ověřovat tokeny.  
  
    > [!NOTE]
    >  Na rozdíl od klienta kolekce vrácené <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastnost, kolekci známých certifikátů není kolekci s klíčem. Služba přijímá tokeny, které zadaný certifikáty vydávají bez ohledu na adresu klienta, který odeslal zprávu obsahující vystavený token (přičemž podléhá další omezení, která jsou popsána dále v tomto tématu).  
  
4.  Nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> vlastnost na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnot výčtu. To lze provést pouze v kódu. Výchozí hodnota je <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5.  Pokud <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> je nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, pak přiřaďte instanci vlastní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy k <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnost.  
  
6.  Pokud <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> je nastaven na `ChainTrust` nebo `PeerOrChainTrust`, nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> vlastnost na hodnotu odpovídající z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> výčtu. Všimněte si, že odvolání režimu se nepoužívá v `PeerTrust` nebo `Custom` režimy ověřování.  
  
7.  V případě potřeby přiřadit instanci vlastní <xref:System.IdentityModel.Tokens.SamlSerializer> třídy k <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> vlastnost. Vlastní serializátor zabezpečení kontrolní výrazy Markup Language (SAML) je potřeba, například k analýze vlastní kontrolní výrazy SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Chcete-li nastavit vlastnosti IssuedTokenServiceCredential v konfiguraci  
  
1.  Vytvoření `<issuedTokenAuthentication>` jako podřízený element <`serviceCredentials`> elementu.  
  
2.  Nastavit `allowUntrustedRsaIssuers` atribut `<issuedTokenAuthentication>` element `true` Pokud ověřování vystavený token, jako například [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty.  
  
3.  Vytvoření `<knownCertificates>` jako podřízený element `<issuedTokenAuthentication>` elementu.  
  
4.  Vytvořit v počtu nula či více `<add>` elementy jako podřízené objekty `<knownCertificates>` elementu a určete, jak vyhledat certifikát pomocí `storeLocation`, `storeName`, `x509FindType`, a `findValue` atributy.  
  
5.  V případě potřeby nastavte `samlSerializer` atribut <`issuedTokenAuthentication`> elementu, který chcete název typu vlastní <xref:System.IdentityModel.Tokens.SamlSerializer> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví vlastnosti <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> v kódu.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby federované služby pro ověření klienta musí být splněné o vydaných token následující podmínky:  
  
-   Pokud digitální podpis vystavený token používá klíče identifikátorem zabezpečení RSA <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> musí být vlastnost `true`.  
  
-   Při podpisu vystavený token používá X.509 vystavitele sériové číslo, identifikátor klíče subjektu X.509 nebo identifikátor zabezpečení kryptografický otisk X.509, vydaný token musí být podepsané certifikátem v kolekci vrácené <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastnost <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>třídy.  
  
-   Při vydaný token je podepsaná pomocí certifikátu X.509, musíte ověřit certifikát na sémantiku zadaný hodnotou <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnost, bez ohledu na to, jestli se certifikát odešle k předávající straně jako <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> nebo byl získán z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastnost. Další informace o ověření certifikátu X.509 najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Například nastavení <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> k <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> by ověření všechny vydané token, jejichž podpisový certifikát se nachází ve `TrustedPeople` úložiště certifikátů. V takovém případě nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> vlastnost, která má buď <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> nebo <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Můžete vybrat jiné režimy, včetně <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Když `Custom` je vybrána, je nutné přiřadit instanci <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy k <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> vlastnost. Vlastní validátor můžete ověřit certifikáty pomocí všechna kritéria, která ho líbí. Další informace najdete v tématu [postupy: vytvoření služby, který využívá validátor certifikátu vlastní](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Viz také  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Federace a důvěryhodnost](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
