---
title: 'Postupy: Vytvoření instance WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: 16b93126157ff129d5e0b815bc951873e7fa760d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778349"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Postupy: Vytvoření instance WSFederationHttpBinding

Ve Windows Communication Foundation (WCF), <xref:System.ServiceModel.WSFederationHttpBinding> třídy ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v konfiguraci) poskytuje mechanismus pro vystavení federované služby. To znamená, že služba, která vyžaduje, aby klienti k ověření pomocí tokenu zabezpečení vydané službou tokenu zabezpečení. Toto téma ukazuje, jak nastavit <xref:System.ServiceModel.WSFederationHttpBinding> v kódu a konfigurace. Jakmile se vytvoří vazba, můžete nastavit koncový bod pro tuto vazbu používají.

 Základní kroky, které jsou uvedeny následovně:

1. Vyberte režim zabezpečení. <xref:System.ServiceModel.WSFederationHttpBinding> Podporuje `Message`, i přes více segmentů směrování, poskytující-koncové zabezpečení na úrovni zpráv a `TransportWithMessageCredential`, která poskytuje lepší výkon v případech, kde klient a služba můžete navázat přímé spojení přes PROTOKOL HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> Také podporuje `None` jako režim zabezpečení. Tento režim není zabezpečený a je k dispozici pouze pro účely ladění. Pokud koncový bod služby se nasazuje s <xref:System.ServiceModel.WSFederationHttpBinding> s jeho režim zabezpečení nastavený na `None`, výsledný klienta vazby (generovaných [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) je <xref:System.ServiceModel.WSHttpBinding> s režim zabezpečení `None`.

     Na rozdíl od jiných vazeb poskytovaných systémem není nutné vybrat typ přihlašovacích údajů klienta při použití `WSFederationHttpBinding`. Je to proto, že typ pověření klienta je vždy vydaný token. WCF získá token ze zadaného vystavitele a představuje tento token ve službě k ověřování klienta.

2. Na federované klientech, nastavena <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> vlastnost na adresu URL služby tokenů zabezpečení. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> vazby používat ke komunikaci se službou tokenu zabezpečení.

3. Volitelné. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> vlastnost k identifikátor URI (Uniform Resource) token typu. Na federovaným službám zadejte typ tokenu, který očekává, že služba. U federovaných klientů určete typ tokenu požadavky klientů od služby tokenů zabezpečení.

     Pokud není zadán žádný typ tokenu, klienti generovat WS-Trust požádat o tokeny zabezpečení (RSTs) bez token typu identifikátoru URI a služby očekávat klienta ověřování pomocí tokenu zabezpečení kontrolní výrazy SAML (Markup Language) 1.1 ve výchozím nastavení.

     Identifikátor URI pro token SAML 1.1 `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Volitelné. Na federovaným službám, nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> vlastnost odeslané na adresu metadat služby tokenů zabezpečení. Koncový bod metadat umožňuje klientům služby vyberte dvojici odpovídající vazby nebo koncového bodu, pokud služba je nakonfigurovaná pro publikování metadat. Další informace o publikování metadat naleznete v tématu [publikování metadat](publishing-metadata.md).

 Můžete také nastavit další vlastnosti, včetně typu klíč použít jako klíč důkazu v vydaný token sadu algoritmů mezi klientem a služby, zda Pokud chcete negotiate, nebo explicitně zadat přihlašovací údaje služby, jakékoliv specifické deklarací služby Očekává se, že vydaný token obsahoval a další elementy XML, které musí být přidáno k žádosti, které klient odešle do služby tokenů zabezpečení.

> [!NOTE]
>  `NegotiateServiceCredential` Vlastnost platí jen při `SecurityMode` je nastavena na `Message`. Pokud `SecurityMode` je nastavena na `TransportWithMessageCredential`, pak bude `NegotiateServiceCredential` vlastnost se ignoruje.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Ke konfiguraci WSFederationHttpBinding v kódu

1. Vytvoření instance <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Nastavte <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSFederationHttpSecurityMode> nebo <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> podle potřeby. Pokud sady algoritmus jiných než <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> je nutné použít, nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> vlastnost na hodnotu z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnosti podle potřeby.

4. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> vlastnost <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` nebo.`AsymmetricKey` podle potřeby.

5. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> k odpovídající hodnotě. Pokud není nastavena žádná hodnota, WCF výchozí `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, což znamená tokeny SAML 1.1.

6. V klientovi požadováno, pokud není zadána žádná lokálního vystavitele; volitelné na službu. Vytvoření <xref:System.ServiceModel.EndpointAddress> , který obsahuje informace o adrese a identitě služby tokenů zabezpečení a přiřadit <xref:System.ServiceModel.EndpointAddress> instance na <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> vlastnost.

7. V klientovi požadováno, pokud není zadána žádná lokálního vystavitele; nepoužívá se ve službě. Vytvořit <xref:System.ServiceModel.Channels.Binding> pro `SecurityTokenService` a přiřaďte <xref:System.ServiceModel.Channels.Binding> instance na <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> vlastnost.

8. Nelze použít na straně klienta; volitelné na službu. Vytvoření <xref:System.ServiceModel.EndpointAddress> instanci metadat služby tokenů zabezpečení a přiřaďte ho `IssuerMetadataAddress` vlastnost.

9. Volitelné na klienta a služby. Vytvořit a přidat jeden nebo více <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instancí na kolekci vrácené poskytovatelem <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> vlastnost.

10. Volitelné na klienta a služby. Vytvořit a přidat jeden nebo více <xref:System.Xml.XmlElement> instancí na kolekci vrácené poskytovatelem <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> vlastnost.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Chcete-li vytvořit federovaný koncový bod v konfiguraci

1. Vytvoření [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako podřízený objekt [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) prvku v konfiguračním souboru aplikace.

2. Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) jako podřízený element [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a nastavit `name` atribut na odpovídající hodnotu.

3. Vytvoření `<security>` element jako podřízený objekt [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu.

4. Nastavte `mode` atribut na `<security>` prvku na hodnotu `Message` nebo `TransportWithMessageCredential`, podle potřeby.

5. Vytvoření `<message>` element jako podřízený objekt `<security>` elementu.

6. Volitelné. Nastavte `algorithmSuite` atribut na `<message>` element s odpovídající hodnotou. Výchozí hodnota je `Basic256`.

7. Volitelné. Pokud asymetrický klíč důkazu je potřeba nastavit `issuedKeyType` atribut `<message>` elementu `AsymmetricKey`. Výchozí hodnota je `SymmetricKey`.

8. Volitelné. Nastavte `issuedTokenType` atribut na `<message>` elementu.

9. V klientovi požadováno, pokud není zadána žádná lokálního vystavitele; volitelné na službu. Vytvoření `<issuer>` element jako podřízený objekt `<message>` elementu.

10. Nastavte `address` atribut `<issuer>` elementu a zadejte adresu, na kterém služba tokenů zabezpečení přijímá žádosti o tokeny.

11. Volitelné. Přidat `<identity>` podřízený element a zadejte identitu služby tokenů zabezpečení

12. Další informace najdete v tématu [identita a ověřování služby](service-identity-and-authentication.md).

13. V klientovi požadováno, pokud není zadána žádná lokálního vystavitele; nepoužívá se ve službě. Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element v oddílu vazby, který slouží ke komunikaci se službou tokenu zabezpečení. Další informace o vytváření vazby najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Zadání vazby vytvořili v předchozím kroku tím, že nastavíte `binding` a `bindingConfiguration` atributy `<issuer>` elementu.

15. Nelze použít na straně klienta; volitelné na službu. Vytvoření `<issuerMetadata>` element jako podřízený objekt <`message`> element. Potom v `address` atribut na `<issuerMetadata>` elementu, zadejte adresu, na které má publikování metadat služby tokenů zabezpečení. Volitelně můžete přidat `<identity>` podřízený element a zadejte identitu služby tokenů zabezpečení.

16. Volitelné na klienta a služby. Přidat `<claimTypeRequirements>` element jako podřízený objekt `<message>` elementu. Zadejte povinné a nepovinné deklarace identity, která služba závisí na přidáním [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) prvků, které se `<claimTypeRequirements>` elementu a určení deklarace identity typu s `claimType` atribut. Určete, jestli má danou deklaraci požadované nebo volitelné tak, že nastavíte `isOptional` atribut.

## <a name="example"></a>Příklad

Následující vzorový kód ukazuje kód pro nastavení `WSFederationHttpBinding` imperativně.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Viz také:

- [Federace](federation.md)
- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)