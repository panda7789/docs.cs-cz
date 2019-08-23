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
ms.openlocfilehash: 9728c908331d5eabcff04d094e7fcbe42f636963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911210"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Postupy: Vytvoření instance WSFederationHttpBinding

V Windows Communication Foundation (WCF) <xref:System.ServiceModel.WSFederationHttpBinding> třída ([\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v konfiguraci) poskytuje mechanismus pro vystavení federované služby. To znamená, že služba, která vyžaduje, aby se klienti ověřovali pomocí tokenu zabezpečení vydaného službou tokenů zabezpečení. <xref:System.ServiceModel.WSFederationHttpBinding> V tomto tématu se dozvíte, jak nastavit jak v kódu, tak v konfiguraci. Po vytvoření vazby můžete nastavit koncový bod pro použití této vazby.

 Základní postup je popsaný níže:

1. Vyberte režim zabezpečení. Podporuje službu, která poskytuje komplexní zabezpečení na úrovni zpráv, a `TransportWithMessageCredential`to i přes několik segmentů směrování, což zajišťuje vyšší výkon v případech, kdy klient a služba mohou vytvořit přímé připojení. `Message` <xref:System.ServiceModel.WSFederationHttpBinding> HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> Také podporuje`None` jako režim zabezpečení. Tento režim není zabezpečen a je poskytován pouze pro účely ladění. Je-li koncový bod služby nasazen s <xref:System.ServiceModel.WSFederationHttpBinding> režimem zabezpečení nastaveným na `None`hodnotu, výsledná vazba klienta (generovaná <xref:System.ServiceModel.WSHttpBinding> [nástrojem Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) je v režimu zabezpečení `None`.

     Na rozdíl od jiných vazeb poskytovaných systémem není nutné při použití nástroje `WSFederationHttpBinding`vybrat typ přihlašovacích údajů klienta. Je to proto, že typ přihlašovacích údajů klienta je vždy vystavený token. Služba WCF získá token od zadaného vystavitele a prezentuje tento token službě k ověřování klienta.

2. U federovaných klientů nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> vlastnost na adresu URL služby tokenu zabezpečení. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> Nastavte na vazbu, která se má použít ke komunikaci se službou tokenu zabezpečení.

3. Volitelný parametr. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Nastavte vlastnost na identifikátor URI (Uniform Resource Identifier) typu tokenu. V části federované služby zadejte typ tokenu, který služba očekává. U federovaných klientů zadejte typ tokenu, který klient požaduje od služby tokenu zabezpečení.

     Pokud není zadaný žádný typ tokenu, klienti vygenerují tokeny zabezpečení žádosti WS-Trust (RSTs) bez identifikátoru URI typu tokenu a služby ve výchozím nastavení očekávají pomocí tokenu SAML (Security Assert Markup Language) 1,1.

     Identifikátor URI pro token SAML 1,1 je `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Volitelný parametr. U federovaných služeb nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> vlastnost na adresu URL metadat služby tokenu zabezpečení. Koncový bod metadat umožňuje klientům služby vybrat příslušnou dvojici a koncový bod, pokud je služba nakonfigurovaná k publikování metadat. Další informace o publikování metadat naleznete v tématu [publikování metadat](publishing-metadata.md).

 Můžete také nastavit další vlastnosti, včetně typu klíče používaného jako ověřovací klíč v vystaveném tokenu, Sada algoritmů, která se má použít mezi klientem a službou, ať už vyjednávat nebo explicitně zadat pověření služby, všechny konkrétní deklarace identity služby. očekává, že vydaný token bude obsahovat, a všechny další prvky XML, které musí být přidány do žádosti, kterou klient odesílá do služby tokenu zabezpečení.

> [!NOTE]
> Vlastnost je relevantní pouze v případě, `SecurityMode` že je nastavena `Message`na. `NegotiateServiceCredential` Pokud `SecurityMode` je `NegotiateServiceCredential` parametr nastaven `TransportWithMessageCredential`na hodnotu, bude vlastnost ignorována.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Konfigurace WSFederationHttpBinding v kódu

1. Vytvořte instanci <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Nastavte vlastnost na <xref:System.ServiceModel.WSFederationHttpSecurityMode> nebo<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> podle potřeby. <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> Pokud je vyžadována jiná sada algoritmů než <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> , <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> nastavte vlastnost na hodnotu pořízenou z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> Nastavte vlastnost podle potřeby.

4. <xref:System.IdentityModel.Tokens.SecurityKeyType> Nastavte vlastnost na`SymmetricKey` nebo. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>`AsymmetricKey` podle potřeby.

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Nastavte vlastnost na odpovídající hodnotu. Pokud není nastavená žádná hodnota, WCF se `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`nastaví jako výchozí, což indikuje tokeny SAML 1,1.

6. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. volitelné ve službě. Vytvořte objekt <xref:System.ServiceModel.EndpointAddress> , který obsahuje informace o adrese a identitě služby tokenu zabezpečení, a <xref:System.ServiceModel.EndpointAddress> přiřaďte instanci <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> k této vlastnosti.

7. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. nepoužívá se ve službě. Vytvořte <xref:System.ServiceModel.Channels.Binding> <xref:System.ServiceModel.Channels.Binding> pro a přiřaďte instanci k Vlastnosti.<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> `SecurityTokenService`

8. Nepoužívá se na klientovi. volitelné ve službě. Vytvořte instanci pro metadata služby tokenu zabezpečení a přiřaďte ji `IssuerMetadataAddress` k vlastnosti. <xref:System.ServiceModel.EndpointAddress>

9. Volitelné na straně klienta i služby. Vytvořte a přidejte jednu nebo více <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instancí do kolekce vrácené <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> vlastností.

10. Volitelné na straně klienta i služby. Vytvořte a přidejte jednu nebo více <xref:System.Xml.XmlElement> instancí do kolekce vrácené <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> vlastností.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Vytvoření federovaného koncového bodu v konfiguraci

1. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) Vytvořte WSFederationHttpBinding > jako podřízený prvek > elementu v konfiguračním souboru aplikace. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)

2. Vytvořte vazbu > elementu jako podřízenou položku pro [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a nastavte `name` atribut na odpovídající hodnotu. [ \<](../../../../docs/framework/misc/binding.md)

3. Vytvořte prvek jako podřízený [ \<prvek > vazby.](../../../../docs/framework/misc/binding.md) `<security>`

4. `mode` Nastavte atribut `<security>` prvkuna`TransportWithMessageCredential`hodnotu nebo, podle potřeby. `Message`

5. Vytvořte prvek jako podřízený `<security>` prvek elementu. `<message>`

6. Volitelný parametr. `algorithmSuite` Nastavte atribut `<message>` prvku s odpovídající hodnotou. Výchozí hodnota je `Basic256`.

7. Volitelný parametr. Pokud je požadován asymetrický klíč ověření, nastavte `issuedKeyType` atribut `<message>` elementu na `AsymmetricKey`. Výchozí hodnota je `SymmetricKey`.

8. Volitelný parametr. `issuedTokenType` Nastavte atribut`<message>` prvku.

9. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. volitelné ve službě. Vytvořte prvek jako podřízený `<message>` prvek elementu. `<issuer>`

10. `address` Nastavte atribut`<issuer>` na element a určete adresu, na které služba tokenů zabezpečení přijímá žádosti o tokeny.

11. Volitelný parametr. `<identity>` Přidejte podřízený element a určete identitu služby tokenu zabezpečení.

12. Další informace najdete v tématu [Identita a ověřování služby](service-identity-and-authentication.md).

13. Vyžaduje se na klientovi, pokud není zadaný žádný místní Vystavitel. nepoužívá se ve službě. Vytvořte [vazbu > elementu v části Bindings, kterou lze použít ke komunikaci se službou tokenu zabezpečení. \<](../../../../docs/framework/misc/binding.md) Další informace o vytváření vazby naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Zadejte vazbu vytvořenou v předchozím kroku nastavením `binding` atributů `<issuer>` a `bindingConfiguration` elementu.

15. Nepoužívá se na klientovi. volitelné ve službě. Vytvořte prvek jako podřízený prvek <`message`>. `<issuerMetadata>` Poté v `address` atributu `<issuerMetadata>` elementu zadejte adresu, na které má služba tokenů zabezpečení publikovat svá metadata. Volitelně můžete přidat `<identity>` podřízený element a zadat identitu služby tokenu zabezpečení.

16. Volitelné na straně klienta i služby. Přidejte prvek jako podřízený `<message>` prvek elementu. `<claimTypeRequirements>` Určete povinné a volitelné deklarace identity, na které služba spoléhá, přidáním [ \<> prvků přidat](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) do `<claimTypeRequirements>` prvku `claimType` a zadáním typu deklarace identity s atributem. Určete, jestli je daná deklarace identity požadovaná, nebo volitelná `isOptional` nastavením atributu.

## <a name="example"></a>Příklad

Následující ukázka kódu ukazuje kód pro `WSFederationHttpBinding` imperativní nastavení.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Viz také:

- [Federace](federation.md)
- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Postupy: Vypnutí zabezpečených relací na WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
