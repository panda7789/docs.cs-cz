---
title: "Postupy: vytvoření třídy WSFederationHttpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3314519e89a78f188d78a5e5af641d7c87ee1c46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Postupy: vytvoření třídy WSFederationHttpBinding
V [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], <xref:System.ServiceModel.WSFederationHttpBinding> – třída ([\<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) v konfiguraci) poskytuje mechanismus pro vystavení federované služby. To znamená, služby, která vyžaduje ověření pomocí tokenu zabezpečení vydaného služby tokenů zabezpečení klientů. Toto téma ukazuje, jak nastavit <xref:System.ServiceModel.WSFederationHttpBinding> v kódu a konfigurace. Po vytvoření vazby, můžete nastavit koncový bod pro tuto vazbu používají.  
  
 Základní kroky, které jsou uvedeny následujícím způsobem:  
  
1.  Vyberte režim zabezpečení. <xref:System.ServiceModel.WSFederationHttpBinding> Podporuje `Message`, který poskytuje – koncové zabezpečení na úrovni zpráv, dokonce i v jiných několik segmentů směrování, a `TransportWithMessageCredential`, který poskytuje lepší výkon v případech, kde klient a služba může provádět přímé připojení přes PROTOKOL HTTPS.  
  
    > [!NOTE]
    >  <xref:System.ServiceModel.WSFederationHttpBinding> Také podporuje `None` jako režim zabezpečení. Tento režim není zabezpečená a se poskytuje pouze pro účely ladění. Pokud koncový bod služby se nasazuje s <xref:System.ServiceModel.WSFederationHttpBinding> s režim zabezpečení, který je nastavený na `None`, výsledná klient vazby (vygenerované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) je <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> s režimem zabezpečení z `None`.  
  
     Na rozdíl od jiných vazby poskytované systémem není nutné vyberte typ pověření klienta při použití `WSFederationHttpBinding`. Je to proto typu pověření klienta je vždy vystavený token. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Získá token zabezpečení ze zadaného vystavitele a uvede tento token ke službě pro ověření klienta.  
  
2.  U federovaných klientů, nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> na adresu URL služby tokenů zabezpečení. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> pro vazbu na použití ke komunikaci s služby tokenů zabezpečení.  
  
3.  Volitelné. Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> vlastnost k identifikátor URI (Uniform Resource) tokenu typu. Na federovaným službám zadejte token typ, který služba očekává. U federovaných klientů zadejte typ tokenu požadavky od služby tokenů zabezpečení.  
  
     Pokud není zadán žádný typ. tokenu, klienti generovat WS-Trust žádosti o tokeny zabezpečení (RSTs) bez typ tokenu URI a služby očekávat ověřování klientů pomocí token zabezpečení kontrolní výrazy Markup Language (SAML) 1.1 ve výchozím nastavení.  
  
     Identifikátor URI pro token SAML 1.1 je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1".  
  
4.  Volitelné. Na federovaným službám, nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> vlastnost na adresu URL metadat služby tokenů zabezpečení. Koncový bod metadat umožňuje klientům služby vyberte dvojici odpovídající vazby nebo koncového bodu, pokud služba je nakonfigurována pro publikování metadat. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]publikování metadat, najdete v části [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
 Můžete také nastavit další vlastnosti, včetně typu klíč používaný jako doklad klíč v vydaných tokenu, algoritmus suite používat mezi klientem a služby, zda Pokud chcete vyjednávání nebo explicitně zadat přihlašovací údaje služby, deklarací žádné konkrétní službu očekává vystavený token, který má obsahovat a další prvky XML, které musí být přidaný do žádosti, které klient odešle do služby tokenů zabezpečení.  
  
> [!NOTE]
>  `NegotiateServiceCredential` Vlastnost platí pouze při `SecurityMode` je nastaven na `Message`. Pokud `SecurityMode` je nastaven na `TransportWithMessageCredential`, pak se `NegotiateServiceCredential` vlastnost je ignorována.  
  
### <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Ke konfiguraci třídy WSFederationHttpBinding v kódu  
  
1.  Vytvoření instance <xref:System.ServiceModel.WSFederationHttpBinding>.  
  
2.  Nastavte <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSFederationHttpSecurityMode> nebo <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> podle potřeby. Pokud sady algoritmus jinak než <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> je nutné, nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> vlastnost na hodnotu převzaty z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  
  
3.  Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> vlastnost podle potřeby.  
  
4.  Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> vlastnost <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` nebo.`AsymmetricKey` podle potřeby.  
  
5.  Nastavte <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> vlastnost na odpovídající hodnotu. Pokud není nastavena žádná hodnota, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výchozí hodnota je "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1", které označuje tokeny SAML 1.1.  
  
6.  V klientovi požadováno, pokud není zadán žádný místního vystavitele; volitelné služby. Vytvoření <xref:System.ServiceModel.EndpointAddress> obsahující informace o adrese a identitě služby tokenů zabezpečení a přiřaďte <xref:System.ServiceModel.EndpointAddress> instance k <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> vlastnost.  
  
7.  V klientovi požadováno, pokud není zadán žádný místního vystavitele; nepoužívá se na službu. Vytvoření <xref:System.ServiceModel.Channels.Binding> pro `SecurityTokenService` a přiřaďte <xref:System.ServiceModel.Channels.Binding> instance k <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> vlastnost.  
  
8.  Nepoužívá se v klientovi; volitelné služby. Vytvoření <xref:System.ServiceModel.EndpointAddress> instanci pro metadata služby tokenů zabezpečení a přiřadit ji ke `IssuerMetadataAddress` vlastnost.  
  
9. Volitelné na klienta a služby. Vytvořit a přidat jeden nebo víc <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instance ke kolekci vrácené <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> vlastnost.  
  
10. Volitelné na klienta a služby. Vytvořit a přidat jeden nebo víc <xref:System.Xml.XmlElement> instance ke kolekci vrácené <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> vlastnost.  
  
### <a name="to-create-a-federated-endpoint-in-configuration"></a>Chcete-li vytvořit koncový bod federované v konfiguraci  
  
1.  Vytvoření [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako podřízenou [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element v konfiguračním souboru aplikace.  
  
2.  Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) jako podřízený element [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a nastavte `name` atribut na odpovídající hodnotu.  
  
3.  Vytvoření `<security>` jako podřízený element [ \<vazby >](../../../../docs/framework/misc/binding.md) element.  
  
4.  Nastavte `mode` atributu u `<security>` element na hodnotu `Message` nebo `TransportWithMessageCredential`, podle potřeby.  
  
5.  Vytvoření `<message>` jako podřízený element `<security>` elementu.  
  
6.  Volitelné. Nastavte `algorithmSuite` atributu u `<message>` element s odpovídající hodnotou. Výchozí hodnota je `Basic256`.  
  
7.  Volitelné. Pokud doklad asymetrický klíč se vyžaduje, nastavit `issuedKeyType` atribut `<message>` element `AsymmetricKey`. Výchozí hodnota je `SymmetricKey`.  
  
8.  Volitelné. Nastavte `issuedTokenType` atributu u `<message>` elementu.  
  
9. V klientovi požadováno, pokud není zadán žádný místního vystavitele; volitelné služby. Vytvoření `<issuer>` jako podřízený element `<message>` elementu.  
  
10. Nastavte `address` atribut `<issuer>` elementu a zadejte adresu, na kterém přijímá služby tokenů zabezpečení žádostí o token.  
  
11. Volitelné. Přidat `<identity>` podřízený element a zadejte identitu služby tokenů zabezpečení  
  
12. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Služby identit a ověření](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
13. V klientovi požadováno, pokud není zadán žádný místního vystavitele; nepoužívá se na službu. Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element v části vazby, který slouží ke komunikaci s služby tokenů zabezpečení. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Vytvoření vazby, najdete v části [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
14. Zadání vazby vytvořený v předchozím kroku nastavení `binding` a `bindingConfiguration` atributy `<issuer>` elementu.  
  
15. Nepoužívá se v klientovi; volitelné služby. Vytvoření `<issuerMetadata>` jako podřízený element <`message`> elementu. Potom v `address` atributu u `<issuerMetadata>` elementu, zadejte adresu, na které má publikování metadat služby tokenů zabezpečení. Volitelně lze přidat `<identity>` podřízený element a zadejte identitu služby tokenů zabezpečení.  
  
16. Volitelné na klienta a služby. Přidat `<claimTypeRequirements>` jako podřízený element `<message>` elementu. Zadejte požadované a volitelné deklarace identity služba založená na přidáním [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementů `<claimTypeRequirements>` elementu a určení deklarace identity zadejte s `claimType` atribut. Určete, zda je daný deklarace identity požadované nebo volitelné nastavením `isOptional` atribut.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje kód pro nastavení `WSFederationHttpBinding` imperativní.  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)] 
 [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Postupy: zakázání zabezpečených relací u třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
