---
title: 'Postupy: vytvoření WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: c3ce90c74ae61dfcbfc0b05fc17b25fe0118e071
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141690"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Postupy: vytvoření WSFederationHttpBinding

V Windows Communication Foundation (WCF) poskytuje <xref:System.ServiceModel.WSFederationHttpBinding> třídy ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v konfiguraci) mechanismus pro vystavení federované služby. To znamená, že služba, která vyžaduje, aby se klienti ověřovali pomocí tokenu zabezpečení vydaného službou tokenů zabezpečení. V tomto tématu se dozvíte, jak nastavit <xref:System.ServiceModel.WSFederationHttpBinding> v kódu i v konfiguraci. Po vytvoření vazby můžete nastavit koncový bod pro použití této vazby.

 Základní postup je popsaný níže:

1. Vyberte režim zabezpečení. <xref:System.ServiceModel.WSFederationHttpBinding> podporuje `Message`, která poskytuje komplexní zabezpečení na úrovni zpráv, a to i přes několik segmentů směrování a `TransportWithMessageCredential`, což poskytuje lepší výkon v případech, kdy klient a služba mohou vytvořit přímé připojení přes protokol HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> také podporuje `None` jako režim zabezpečení. Tento režim není zabezpečen a je poskytován pouze pro účely ladění. Pokud je koncový bod služby nasazený s <xref:System.ServiceModel.WSFederationHttpBinding> se svým režimem zabezpečení nastaveným na `None`, výsledná vazba klienta (generovaná [nástrojem Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)je <xref:System.ServiceModel.WSHttpBinding> s režimem zabezpečení `None`.

     Na rozdíl od jiných vazeb poskytovaných systémem není při použití `WSFederationHttpBinding`nutné vybrat typ přihlašovacích údajů klienta. Je to proto, že typ přihlašovacích údajů klienta je vždy vystavený token. Služba WCF získá token od zadaného vystavitele a prezentuje tento token službě k ověřování klienta.

2. U federovaných klientů nastavte vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> na adresu URL služby tokenu zabezpečení. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> na vazbu, která se má použít ke komunikaci se službou tokenu zabezpečení.

3. Volitelné. Vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> nastavte na identifikátor URI (Uniform Resource Identifier) typu tokenu. V části federované služby zadejte typ tokenu, který služba očekává. U federovaných klientů zadejte typ tokenu, který klient požaduje od služby tokenu zabezpečení.

     Pokud není zadaný žádný typ tokenu, klienti vygenerují tokeny zabezpečení žádosti WS-Trust (RSTs) bez identifikátoru URI typu tokenu a služby ve výchozím nastavení očekávají pomocí tokenu SAML (Security Assert Markup Language) 1,1.

     Identifikátor URI pro token SAML 1,1 je `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Volitelné. U federovaných služeb nastavte vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> na adresu URL metadat služby tokenu zabezpečení. Koncový bod metadat umožňuje klientům služby vybrat příslušnou dvojici a koncový bod, pokud je služba nakonfigurovaná k publikování metadat. Další informace o publikování metadat naleznete v tématu [publikování metadat](publishing-metadata.md).

 Můžete také nastavit další vlastnosti, včetně typu klíče používaného jako ověřovací klíč v vystaveném tokenu, Sada algoritmů, která se má použít mezi klientem a službou, ať už vyjednávat nebo explicitně zadat pověření služby, všechny konkrétní deklarace identity služby. očekává, že vydaný token bude obsahovat, a všechny další prvky XML, které musí být přidány do žádosti, kterou klient odesílá do služby tokenu zabezpečení.

> [!NOTE]
> Vlastnost `NegotiateServiceCredential` je relevantní pouze v případě, že je `SecurityMode` nastavena na `Message`. Pokud je `SecurityMode` nastaveno na `TransportWithMessageCredential`, bude vlastnost `NegotiateServiceCredential` ignorována.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Konfigurace WSFederationHttpBinding v kódu

1. Vytvořte instanci <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Nastavte vlastnost <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> na <xref:System.ServiceModel.WSFederationHttpSecurityMode> nebo <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> podle potřeby. Pokud je vyžadována jiná sada algoritmů než <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A>, nastavte vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> na hodnotu pořízenou z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Nastavte vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> podle potřeby.

4. Nastavte vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> na <xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey` nebo.`AsymmetricKey` podle potřeby.

5. Nastavte vlastnost <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> na odpovídající hodnotu. Pokud není nastavená žádná hodnota, WCF se nastaví jako výchozí `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, což indikuje tokeny SAML 1,1.

6. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. volitelné ve službě. Vytvořte <xref:System.ServiceModel.EndpointAddress>, který obsahuje informace o adrese a identitě služby tokenu zabezpečení, a přiřaďte instanci <xref:System.ServiceModel.EndpointAddress> k vlastnosti <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A>.

7. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. nepoužívá se ve službě. Vytvořte <xref:System.ServiceModel.Channels.Binding> pro `SecurityTokenService` a přiřaďte instanci <xref:System.ServiceModel.Channels.Binding> k vlastnosti <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A>.

8. Nepoužívá se na klientovi. volitelné ve službě. Vytvořte instanci <xref:System.ServiceModel.EndpointAddress> pro metadata služby tokenu zabezpečení a přiřaďte ji k vlastnosti `IssuerMetadataAddress`.

9. Volitelné na straně klienta i služby. Vytvořte a přidejte jednu nebo více instancí <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> do kolekce vrácené vlastností <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>.

10. Volitelné na straně klienta i služby. Vytvořte a přidejte jednu nebo více instancí <xref:System.Xml.XmlElement> do kolekce vrácené vlastností <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Vytvoření federovaného koncového bodu v konfiguraci

1. Vytvořte [\<WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako podřízený prvek [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu v konfiguračním souboru aplikace.

2. Vytvořte [vazbu\<](../../configure-apps/file-schema/wcf/bindings.md) elementu jako podřízenou položku [\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a nastavte atribut `name` na odpovídající hodnotu.

3. Vytvořte `<security>` element jako podřízený prvek [> elementu\<vazby](../../configure-apps/file-schema/wcf/bindings.md) .

4. Nastavte atribut `mode` u prvku `<security>` na hodnotu `Message` nebo `TransportWithMessageCredential`, jak je požadováno.

5. Vytvořte `<message>` element jako podřízený prvek `<security>` elementu.

6. Volitelné. Nastavte atribut `algorithmSuite` u prvku `<message>` s odpovídající hodnotou. Výchozí hodnota je `Basic256`.

7. Volitelné. Pokud je požadován klíč asymetrického ověření, nastavte atribut `issuedKeyType` `<message>` elementu na `AsymmetricKey`. Výchozí hodnota je `SymmetricKey`.

8. Volitelné. Nastavte atribut `issuedTokenType` u elementu `<message>`.

9. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. volitelné ve službě. Vytvořte prvek `<issuer>` jako podřízený prvek `<message>`.

10. Nastavte atribut `address` na prvek `<issuer>` a zadejte adresu, na které služba tokenů zabezpečení přijímá žádosti o tokeny.

11. Volitelné. Přidejte podřízený element `<identity>` a zadejte identitu služby tokenu zabezpečení.

12. Další informace najdete v tématu [Identita a ověřování služby](service-identity-and-authentication.md).

13. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. nepoužívá se ve službě. Vytvořte [\<vazbu >](../../configure-apps/file-schema/wcf/bindings.md) elementu v části Bindings, kterou lze použít ke komunikaci se službou tokenu zabezpečení. Další informace o vytváření vazby naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Zadejte vazbu vytvořenou v předchozím kroku nastavením atributů `binding` a `bindingConfiguration` elementu `<issuer>`.

15. Nepoužívá se na klientovi. volitelné ve službě. Vytvořte prvek `<issuerMetadata>` jako podřízenou položku prvku <`message`>. Potom v atributu `address` u elementu `<issuerMetadata>` Určete adresu, na které má služba tokenů zabezpečení publikovat svá metadata. Volitelně můžete přidat `<identity>` podřízený element a zadat identitu služby tokenu zabezpečení.

16. Volitelné na straně klienta i služby. Přidejte prvek `<claimTypeRequirements>` jako podřízený prvek `<message>`. Určete povinné a volitelné deklarace identity, na které služba spoléhá, přidáním [\<přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) prvky do prvku `<claimTypeRequirements>` a zadáním typu deklarace s atributem `claimType`. Určete, jestli je daná deklarace identity požadovaná, nebo volitelná nastavením atributu `isOptional`.

## <a name="example"></a>Příklad

Následující ukázka kódu ukazuje kód pro nastavení `WSFederationHttpBinding` imperativně.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Viz také:

- [Federace](federation.md)
- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
