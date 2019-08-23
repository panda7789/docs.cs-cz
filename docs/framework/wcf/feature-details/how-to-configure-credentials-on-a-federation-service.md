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
ms.openlocfilehash: 792d2f1b113c0743bd91ccf2f7ff894d7f7d319f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912188"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Postupy: Konfigurace pověření ve službě Federation Service
V Windows Communication Foundation (WCF) se vytváření federované služby skládá z následujících hlavních postupů:  
  
1. <xref:System.ServiceModel.WSFederationHttpBinding> Konfigurace nebo podobná vlastní vazba. Další informace o vytváření příslušné vazby naleznete v tématu [How to: Vytvořte WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> Konfigurace, která určuje, jak se ověřují vydané tokeny služby.  
  
 V tomto tématu najdete podrobné informace o druhém kroku. Další informace o tom, jak federované služba funguje, najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Nastavení vlastností IssuedTokenServiceCredential v kódu  
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> Pomocí vlastnosti <xref:System.ServiceModel.Description.ServiceCredentials> třídy vraťteodkaznainstanci.<xref:System.ServiceModel.Security.IssuedTokenServiceCredential> Vlastnost je k dispozici z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnosti <xref:System.ServiceModel.ServiceHostBase> třídy.  
  
2. Nastavte vlastnost na, `true` Pokud mají být ověřovány tokeny vystavené svým držitelem, jako jsou karty CardSpace. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> Výchozí hodnota je `false`.  
  
3. Naplňte kolekci vrácenou <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> vlastností s instancemi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy. Každá instance představuje Vystavitel, ze kterého bude služba ověřovat tokeny.  
  
    > [!NOTE]
    > Na rozdíl od kolekce na straně klienta vracené <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> vlastností není kolekce známých certifikátů kolekcí klíčů. Služba přijímá tokeny, které zadávají zadané certifikáty, bez ohledu na adresu klienta, která odeslala zprávu obsahující vydaný token (podléhá dalším omezením, která jsou popsána dále v tomto tématu).  
  
4. Nastavte vlastnost na jednu z hodnot <xref:System.ServiceModel.Security.X509CertificateValidationMode> výčtu. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> To lze provést pouze v kódu. Výchozí hodnota je <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Pokud je <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> <xref:System.IdentityModel.Selectors.X509CertificateValidator> vlastnost nastavena na, pak k <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> vlastnosti přiřaďte instanci vlastní třídy. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>  
  
6. `ChainTrust` `PeerOrChainTrust`Pokud je nastaven na nebo, nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> vlastnost na odpovídající hodnotu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> výčtu. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Všimněte si, že se režim odvolání nepoužívá `PeerTrust` v `Custom` režimech ověřování nebo.  
  
7. <xref:System.IdentityModel.Tokens.SamlSerializer> V<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> případě potřeby přiřaďte vlastnosti instanci vlastní třídy. Je zapotřebí vlastní serializátor jazyka SAML (Security Assert Markup Language), například pro analýzu vlastních kontrolních výrazů SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Nastavení vlastností IssuedTokenServiceCredential v konfiguraci  
  
1. Vytvoření prvku jako podřízeného prvku <`serviceCredentials`>. `<issuedTokenAuthentication>`  
  
2. Nastavte atribut elementu na, `<issuedTokenAuthentication>` pokud ověřujete token, který `true` byl vystaven svým držitelem, jako je například karta CardSpace. `allowUntrustedRsaIssuers`  
  
3. Vytvořte prvek jako podřízený `<issuedTokenAuthentication>` prvek elementu. `<knownCertificates>`  
  
4. Vytvořte nula nebo více `<add>` prvků jako podřízené položky `<knownCertificates>` prvku a určete `storeLocation`, jak se má certifikát najít pomocí atributů, `storeName`, `x509FindType`a `findValue` .  
  
5. V případě potřeby nastavte `samlSerializer` atribut <`issuedTokenAuthentication`> elementu na název typu vlastní <xref:System.IdentityModel.Tokens.SamlSerializer> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví vlastnosti <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> v kódu.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby federované služby ověřily klienta, musí mít následující informace o vydaném tokenu hodnotu true:  
  
- Pokud digitální podpis vydaného tokenu používá identifikátor klíče zabezpečení RSA, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> musí být `true`vlastnost.  
  
- Když podpis vydaného tokenu používá sériové číslo vystavitele x. 509, identifikátor klíče subjektu x. 509 nebo identifikátor zabezpečení kryptografických otisků x. 509, musí být vydaný token podepsán certifikátem v kolekci, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> kterou vrátila vlastnost <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>třída.  
  
- Pokud je vydaný token podepsaný pomocí certifikátu X. 509, musí certifikát ověřit podle sémantiky zadané hodnotou <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> vlastnosti, a to bez ohledu na to, jestli byl certifikát odeslán do předávající strany <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> jako nebo získaný. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> z vlastnosti. Další informace o ověřování certifikátu X. 509 najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Například nastavení <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> , aby <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> se ověřil jakýkoli vydaný token, jehož `TrustedPeople` podpisový certifikát je v úložišti certifikátů. V takovém případě nastavte <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> vlastnost na buď <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> nebo <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Můžete vybrat jiné režimy, včetně <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Když `Custom` je vybráno, je nutné přiřadit instanci <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy k <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> vlastnosti. Vlastní validátor může ověřit certifikáty pomocí libovolných kritérií, jako je. Další informace najdete v tématu [jak: Vytvořte službu, která využívá vlastní validátor](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certifikátů.  
  
## <a name="see-also"></a>Viz také:

- [Federace](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federace a důvěryhodnost](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Vypnutí zabezpečených relací na WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
