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
ms.openlocfilehash: 05f35bbb7dbb34cd4067c407578038cbb4eff70f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599139"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Postupy: Konfigurace pověření ve službě Federation Service
V Windows Communication Foundation (WCF) se vytváření federované služby skládá z následujících hlavních postupů:  
  
1. Konfigurace <xref:System.ServiceModel.WSFederationHttpBinding> nebo podobná vlastní vazba. Další informace o vytváření příslušné vazby naleznete v tématu [How to: Create a WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md).  
  
2. Konfigurace <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> , která určuje, jak se ověřují vydané tokeny služby.  
  
 V tomto tématu najdete podrobné informace o druhém kroku. Další informace o tom, jak federované služba funguje, najdete v tématu [federace](federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Nastavení vlastností IssuedTokenServiceCredential v kódu  
  
1. Pomocí <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> vlastnosti <xref:System.ServiceModel.Description.ServiceCredentials> třídy vraťte odkaz na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> instanci. Vlastnost je k dispozici z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnosti <xref:System.ServiceModel.ServiceHostBase> třídy.  
  
2. Nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> vlastnost na, `true` Pokud mají být ověřovány tokeny vystavené svým držitelem, jako jsou karty CardSpace. Výchozí formát je `false`.  
  
3. Naplňte kolekci vrácenou <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastností s instancemi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy. Každá instance představuje Vystavitel, ze kterého bude služba ověřovat tokeny.  
  
    > [!NOTE]
    > Na rozdíl od kolekce na straně klienta vracené <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastností není kolekce známých certifikátů kolekcí klíčů. Služba přijímá tokeny, které zadávají zadané certifikáty, bez ohledu na adresu klienta, která odeslala zprávu obsahující vydaný token (podléhá dalším omezením, která jsou popsána dále v tomto tématu).  
  
4. Nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> vlastnost na jednu z <xref:System.ServiceModel.Security.X509CertificateValidationMode> hodnot výčtu. To lze provést pouze v kódu. Výchozí formát je <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Pokud <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> je vlastnost nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> , pak k vlastnosti přiřaďte instanci vlastní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> .  
  
6. Pokud <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> je nastaven na `ChainTrust` nebo `PeerOrChainTrust` , nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> vlastnost na odpovídající hodnotu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> výčtu. Všimněte si, že se režim odvolání nepoužívá `PeerTrust` v `Custom` režimech ověřování nebo.  
  
7. V případě potřeby přiřaďte vlastnosti instanci vlastní <xref:System.IdentityModel.Tokens.SamlSerializer> třídy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> . Je zapotřebí vlastní serializátor jazyka SAML (Security Assert Markup Language), například pro analýzu vlastních kontrolních výrazů SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Nastavení vlastností IssuedTokenServiceCredential v konfiguraci  
  
1. Vytvoření `<issuedTokenAuthentication>` prvku jako podřízeného `serviceCredentials` prvku <>.  
  
2. Nastavte `allowUntrustedRsaIssuers` atribut `<issuedTokenAuthentication>` elementu na `true` , pokud ověřujete token, který byl vystaven svým držitelem, jako je například karta CardSpace.  
  
3. Vytvořte `<knownCertificates>` prvek jako podřízený `<issuedTokenAuthentication>` prvek elementu.  
  
4. Vytvořte nula nebo více `<add>` prvků jako podřízené položky `<knownCertificates>` prvku a určete, jak se má certifikát najít pomocí `storeLocation` `storeName` atributů,, `x509FindType` a `findValue` .  
  
5. V případě potřeby nastavte `samlSerializer` atribut <`issuedTokenAuthentication`> elementu na název typu vlastní <xref:System.IdentityModel.Tokens.SamlSerializer> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví vlastnosti <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> v kódu.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby federované služby ověřily klienta, musí mít následující informace o vydaném tokenu hodnotu true:  
  
- Pokud digitální podpis vydaného tokenu používá identifikátor klíče zabezpečení RSA, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> musí být vlastnost `true` .  
  
- Pokud podpis vydaného tokenu používá sériové číslo vystavitele X. 509, identifikátor klíče subjektu X. 509 nebo identifikátor zabezpečení kryptografických otisků X. 509, musí být vydaný token podepsán certifikátem v kolekci vrácené <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastností <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy.  
  
- Pokud je vydaný token podepsaný pomocí certifikátu X. 509, musí certifikát ověřit podle sémantiky určené hodnotou <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnosti, a to bez ohledu na to, jestli byl certifikát odeslán do předávající strany jako <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> nebo získaný z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> Vlastnosti. Další informace o ověřování certifikátu X. 509 najdete v tématu [práce s certifikáty](working-with-certificates.md).  
  
 Například nastavení, aby se <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> ověřil jakýkoli vydaný token, jehož podpisový certifikát je v `TrustedPeople` úložišti certifikátů. V takovém případě nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> vlastnost na buď <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> nebo <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine> . Můžete vybrat jiné režimy, včetně <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> . Když `Custom` je vybráno, je nutné přiřadit instanci <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy k <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> Vlastnosti. Vlastní validátor může ověřit certifikáty pomocí libovolných kritérií, jako je. Další informace najdete v tématu [Postup: vytvoření služby, která využívá vlastní validátor certifikátů](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Viz také

- [metadata](federation.md)
- [Federace a důvěryhodnost](federation-and-trust.md)
- [Ukázka federace](../samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření federovaného klienta](how-to-create-a-federated-client.md)
- [Práce s certifikáty](working-with-certificates.md)
- [Režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md)
