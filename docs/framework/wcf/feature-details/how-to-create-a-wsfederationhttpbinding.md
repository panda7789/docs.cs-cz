---
title: 'Postupy: Vytvoření WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: ccc28c46e8be0b835cf08d372ef85b8a66e989ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595437"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Postupy: Vytvoření WSFederationHttpBinding

V Windows Communication Foundation (WCF) <xref:System.ServiceModel.WSFederationHttpBinding> třída ( [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v konfiguraci) poskytuje mechanismus pro vystavení federované služby. To znamená, že služba, která vyžaduje, aby se klienti ověřovali pomocí tokenu zabezpečení vydaného službou tokenů zabezpečení. V tomto tématu se dozvíte, jak nastavit <xref:System.ServiceModel.WSFederationHttpBinding> jak v kódu, tak v konfiguraci. Po vytvoření vazby můžete nastavit koncový bod pro použití této vazby.

 Základní postup je popsaný níže:

1. Vyberte režim zabezpečení. <xref:System.ServiceModel.WSFederationHttpBinding>Podpora `Message` , která poskytuje komplexní zabezpečení na úrovni zpráv, a to i přes několik segmentů směrování, `TransportWithMessageCredential` což zajišťuje vyšší výkon v případech, kdy klient a služba mohou vytvořit přímé připojení přes protokol HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding>Také podporuje `None` jako režim zabezpečení. Tento režim není zabezpečen a je poskytován pouze pro účely ladění. Je-li koncový bod služby nasazen s <xref:System.ServiceModel.WSFederationHttpBinding> režimem zabezpečení nastaveným na hodnotu `None` , výsledná vazba klienta (generovaná [nástrojem Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)) je <xref:System.ServiceModel.WSHttpBinding> s režimem zabezpečení nástroje `None` .

     Na rozdíl od jiných vazeb poskytovaných systémem není nutné při použití nástroje vybrat typ přihlašovacích údajů klienta `WSFederationHttpBinding` . Je to proto, že typ přihlašovacích údajů klienta je vždy vystavený token. Služba WCF získá token od zadaného vystavitele a prezentuje tento token službě k ověřování klienta.

2. U federovaných klientů nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> vlastnost na adresu URL služby tokenu zabezpečení. Nastavte na <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> vazbu, která se má použít ke komunikaci se službou tokenu zabezpečení.

3. Nepovinný parametr. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> vlastnost na identifikátor URI (Uniform Resource Identifier) typu tokenu. V části federované služby zadejte typ tokenu, který služba očekává. U federovaných klientů zadejte typ tokenu, který klient požaduje od služby tokenu zabezpečení.

     Pokud není zadaný žádný typ tokenu, klienti vygenerují tokeny zabezpečení žádosti WS-Trust (RSTs) bez identifikátoru URI typu tokenu a služby ve výchozím nastavení očekávají pomocí tokenu SAML (Security Assert Markup Language) 1,1.

     Identifikátor URI pro token SAML 1,1 je `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .

4. Nepovinný parametr. U federovaných služeb nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> vlastnost na adresu URL metadat služby tokenu zabezpečení. Koncový bod metadat umožňuje klientům služby vybrat příslušnou dvojici a koncový bod, pokud je služba nakonfigurovaná k publikování metadat. Další informace o publikování metadat naleznete v tématu [publikování metadat](publishing-metadata.md).

 Můžete také nastavit další vlastnosti, včetně typu klíče používaného jako ověřovací klíč v vystaveném tokenu, Sada algoritmů pro použití mezi klientem a službou, zda vyjednávat nebo explicitně zadat pověření služby, všechny konkrétní deklarace identity, které služba očekává, že má vydaný token obsahovat, a všechny další prvky XML, které musí být přidány do žádosti, kterou klient odesílá do služby tokenu zabezpečení.

> [!NOTE]
> `NegotiateServiceCredential`Vlastnost je relevantní pouze v případě, že `SecurityMode` je nastavena na `Message` . Pokud `SecurityMode` je parametr nastaven na hodnotu `TransportWithMessageCredential` , bude `NegotiateServiceCredential` vlastnost ignorována.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Konfigurace WSFederationHttpBinding v kódu

1. Vytvořte instanci <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Nastavte <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.WSFederationHttpSecurityMode> nebo <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> podle potřeby. Pokud je vyžadována jiná sada algoritmů než <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> , nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> vlastnost na hodnotu pořízenou z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .

3. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnost podle potřeby.

4. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> vlastnost na <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` nebo.`AsymmetricKey` podle potřeby.

5. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> vlastnost na odpovídající hodnotu. Pokud není nastavená žádná hodnota, WCF se nastaví jako výchozí `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` , což indikuje tokeny SAML 1,1.

6. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. volitelné ve službě. Vytvořte objekt <xref:System.ServiceModel.EndpointAddress> , který obsahuje informace o adrese a identitě služby tokenu zabezpečení, a přiřaďte <xref:System.ServiceModel.EndpointAddress> instanci k této <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> Vlastnosti.

7. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. nepoužívá se ve službě. Vytvořte <xref:System.ServiceModel.Channels.Binding> pro `SecurityTokenService` a přiřaďte <xref:System.ServiceModel.Channels.Binding> instanci k <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> Vlastnosti.

8. Nepoužívá se na klientovi. volitelné ve službě. Vytvořte <xref:System.ServiceModel.EndpointAddress> instanci pro metadata služby tokenu zabezpečení a přiřaďte ji k `IssuerMetadataAddress` Vlastnosti.

9. Volitelné na straně klienta i služby. Vytvořte a přidejte jednu nebo více <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instancí do kolekce vrácené <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> vlastností.

10. Volitelné na straně klienta i služby. Vytvořte a přidejte jednu nebo více <xref:System.Xml.XmlElement> instancí do kolekce vrácené <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> vlastností.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Vytvoření federovaného koncového bodu v konfiguraci

1. Vytvořte [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako podřízený [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) prvek v konfiguračním souboru aplikace.

2. Vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvek jako podřízený objekt [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a nastavte `name` atribut na odpovídající hodnotu.

3. Vytvořte `<security>` prvek jako podřízený [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvek elementu.

4. Nastavte `mode` atribut `<security>` prvku na hodnotu `Message` nebo `TransportWithMessageCredential` , podle potřeby.

5. Vytvořte `<message>` prvek jako podřízený `<security>` prvek elementu.

6. Nepovinný parametr. Nastavte `algorithmSuite` atribut `<message>` prvku s odpovídající hodnotou. Výchozí formát je `Basic256`.

7. Nepovinný parametr. Pokud je požadován asymetrický klíč ověření, nastavte `issuedKeyType` atribut `<message>` elementu na `AsymmetricKey` . Výchozí formát je `SymmetricKey`.

8. Nepovinný parametr. Nastavte `issuedTokenType` atribut `<message>` prvku.

9. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. volitelné ve službě. Vytvořte `<issuer>` prvek jako podřízený `<message>` prvek elementu.

10. Nastavte `address` atribut na `<issuer>` element a určete adresu, na které služba tokenů zabezpečení přijímá žádosti o tokeny.

11. Nepovinný parametr. Přidejte `<identity>` podřízený element a určete identitu služby tokenu zabezpečení.

12. Další informace najdete v tématu [Identita a ověřování služby](service-identity-and-authentication.md).

13. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. nepoužívá se ve službě. Vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element v části Bindings, který se dá použít ke komunikaci se službou tokenu zabezpečení. Další informace o vytváření vazby naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).

14. Zadejte vazbu vytvořenou v předchozím kroku nastavením `binding` `bindingConfiguration` atributů a `<issuer>` elementu.

15. Nepoužívá se na klientovi. volitelné ve službě. Vytvořte `<issuerMetadata>` prvek jako podřízený `message` prvek <>. Poté v `address` atributu `<issuerMetadata>` elementu zadejte adresu, na které má služba tokenů zabezpečení publikovat svá metadata. Volitelně můžete přidat `<identity>` podřízený element a zadat identitu služby tokenu zabezpečení.

16. Volitelné na straně klienta i služby. Přidejte `<claimTypeRequirements>` prvek jako podřízený `<message>` prvek elementu. Zadejte požadované a volitelné deklarace identity, na kterých služba spoléhá, přidáním [\<add>](../../configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) prvků do `<claimTypeRequirements>` prvku a zadáním typu deklarace identity s `claimType` atributem. Určete, jestli je daná deklarace identity požadovaná, nebo volitelná nastavením `isOptional` atributu.

## <a name="example"></a>Příklad

Následující ukázka kódu ukazuje kód pro `WSFederationHttpBinding` imperativní nastavení.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Viz také

- [metadata](federation.md)
- [Ukázka federace](../samples/federation-sample.md)
- [Postupy: Zakázání zabezpečených relací u třídy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
