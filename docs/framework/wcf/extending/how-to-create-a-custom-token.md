---
title: 'Postupy: Vytvoření vlastního tokenu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: 9fae195247dea4cbd049f7157f04e87bb97d6f4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304659"
---
# <a name="how-to-create-a-custom-token"></a>Postupy: Vytvoření vlastního tokenu
Toto téma ukazuje, jak vytvořit vlastní bezpečnostní token pomocí <xref:System.IdentityModel.Tokens.SecurityToken> třídy a jak ji integrovat s vlastního zprostředkovatele tokenů zabezpečení a ověřovací data. Příklad úplného kódu najdete v článku [vlastní Token](../../../../docs/framework/wcf/samples/custom-token.md) vzorku.  
  
 A *token zabezpečení* je v podstatě element XML, který se používá zabezpečení rozhraním Windows Communication Foundation (WCF) k reprezentaci deklarace identity o odesílateli uvnitř zprávy protokolu SOAP. Zabezpečení WCF poskytuje různé tokeny pro režimy ověřování poskytované systémem. Mezi příklady patří token zabezpečení certifikátu X.509 reprezentována <xref:System.IdentityModel.Tokens.X509SecurityToken> zastoupení třídy nebo token zabezpečení uživatelské jméno <xref:System.IdentityModel.Tokens.UserNameSecurityToken> třídy.  
  
 Někdy k režim ověřování nebo přihlašovacích údajů nepodporuje poskytnutých typů. V takovém případě je potřeba vytvořit vlastní bezpečnostní token poskytnout reprezentaci v jazyce XML vlastní přihlašovací údaje, které uvnitř zprávy protokolu SOAP.  
  
 Následující postupy ukazují, jak vytvořit vlastní bezpečnostní token a jak ji integrovat s vaší stávající infrastrukturou zabezpečení WCF. Toto téma vytvoří token platební karty, který se používá k předávání informací o platební kartě klienta na server.  
  
 Další informace o vlastní přihlašovací údaje a Správce tokenů zabezpečení najdete v tématu [názorný postup: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Zobrazit <xref:System.IdentityModel.Tokens> obor názvů pro další třídy, které představují tokeny zabezpečení.  
  
## <a name="procedures"></a>Procedury  
 Klientská aplikace musí být součástí způsob, jak určit informace o platební kartě pro zabezpečení infrastruktury. Tyto informace je k dispozici pro aplikaci pomocí vlastních klientských přihlašovacích údajů třídy. Prvním krokem je vytvoření třídy představující informace o platební kartě pro vlastní klientské přihlašovací údaje.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Chcete-li vytvořit třídu, která představuje informace o platební kartě uvnitř přihlašovacích údajů klienta  
  
1. Definujte novou třídu, která představuje informace o platební kartě pro aplikaci. Následující příklad názvy třídy `CreditCardInfo`.  
  
2. Přidejte příslušné vlastnosti do třídy tak, aby umožnily že aplikace nastavit potřebné informace požadované pro vlastní token. V tomto příkladu třída má tři vlastnosti: `CardNumber`, `CardIssuer`, a `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 V dalším kroku je nutné vytvořit třídu, která představuje token, který vlastní zabezpečení. Tato třída se používá tak, že poskytovatel tokenu zabezpečení, authenticator a serializátor třídy k předávání informací o tokenu zabezpečení do a z Infrastruktura zabezpečení WCF.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Chcete-li vytvořit vlastní bezpečnostní token třídy  
  
1. Definovat nové třídy odvozené od <xref:System.IdentityModel.Tokens.SecurityToken> třídy. Tento příklad vytvoří třídu s názvem `CreditCardToken`.  
  
2. Přepsat <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> vlastnost. Tato vlastnost slouží k získání místní identifikátor tokenu zabezpečení, který se používá tak, aby odkazoval na reprezentaci XML pro token zabezpečení z jiných elementů v rámci zprávu protokolu SOAP. V tomto příkladu identifikátoru tokenu lze buď předat ji jako parametr konstruktoru nebo nový náhodný je generována pokaždé, když je vytvořena instance tokenu zabezpečení.  
  
3. Implementace <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> vlastnost. Tato vlastnost vrátí kolekci klíčů zabezpečení, které představuje instance tokenu zabezpečení. Tyto klíče slouží WCF k podepisování nebo šifrování části zprávy protokolu SOAP. V tomto příkladu token zabezpečení platební karty nesmí obsahovat žádné zabezpečení klíče; proto implementace vždy vrátí prázdnou kolekci.  
  
4. Přepsat <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> a <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> vlastnosti. Tyto vlastnosti jsou používány WCF pro určení platnosti instance tokenu zabezpečení. V tomto příkladu platební karty token zabezpečení má pouze datum vypršení platnosti, proto `ValidFrom` vrátí vlastnost <xref:System.DateTime> , která představuje datum a čas vytvoření instance.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Pokud nový bezpečnostní token typ je vytvořen, vyžaduje implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy. Implementace se používá v konfigurace elementu vazby zabezpečení představující nový typ tokenu. Třída parametrů tokenu zabezpečení slouží jako šablonu, která slouží k určení instance tokenu zabezpečení pro při zpracování zprávy. Šablona nabízí další vlastnosti, které aplikace může použít k určení kritéria, která používají nebo se musí ověřit musí odpovídat tokenu zabezpečení. Následující příklad nepřidává žádné další vlastnosti, takže pouze požadované zabezpečení i typ tokenu je nalezena shoda, když infrastruktura WCF hledá instance tokenu zabezpečení v použití nebo ověřit.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Pro vytvoření třídy parametrů tokenu zabezpečení vlastní  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy.  
  
2. Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> metody. Zkopírujte všechny vnitřní pole definovaná ve třídě, pokud existuje. V tomto příkladu nedefinuje žádné další pole.  
  
3. Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> vlastnost jen pro čtení. Tato vlastnost vrátí `true` Pokud typ tokenu zabezpečení, který je reprezentovaný touto třídou slouží k ověření klienta ke službě. V tomto příkladu token zabezpečení platební karta slouží k ověření klienta ke službě.  
  
4. Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> vlastnost jen pro čtení. Tato vlastnost vrátí `true` Pokud typ tokenu zabezpečení, který je reprezentovaný touto třídou slouží k ověření služby ke klientovi. V tomto příkladu platební karty token zabezpečení nelze použít k ověření služby ke klientovi.  
  
5. Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> vlastnost jen pro čtení. Tato vlastnost vrátí `true` Pokud typ tokenu zabezpečení, který je reprezentovaný touto třídou je možné mapovat na účet Windows. Pokud ano, je reprezentována výsledek ověřování <xref:System.Security.Principal.WindowsIdentity> instance třídy. V tomto příkladu tokenu nelze mapovat na účet Windows.  
  
6. Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> metody. Tato metoda je volána rozhraním zabezpečení WCF, pokud se vyžaduje odkaz na instance tokenu zabezpečení reprezentovaný touto třídou parametrů tokenu zabezpečení. Zabezpečení token instance a <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> , který určuje typ odkazu, které jsou požadovány jsou předány do této metody jako argumenty. V tomto příkladu jsou podporovány pouze interní odkazy token zabezpečení platební karty. <xref:System.IdentityModel.Tokens.SecurityToken> Třída má funkce k vytvoření interní odkazů; proto implementace nevyžaduje další kód.  
  
7. Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metody. Tato metoda je volána službou WCF k převedení instance třídy parametrů tokenu zabezpečení do instance <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> třídy. Výsledek podle poskytovatele tokenů zabezpečení slouží k vytvoření instance tokenu zabezpečení.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokeny zabezpečení přenosu uvnitř zprávy protokolu SOAP, které vyžaduje mechanismus překlad mezi reprezentace token zabezpečení v paměti a na síťové vyjádření. Tento úkol provést pomocí WCF serializátoru tokenů zabezpečení. Každé vlastní token musí být doplněny serializátor vlastní zabezpečení, která může serializovat a deserializovat vlastní bezpečnostní token z zprávy protokolu SOAP.  
  
> [!NOTE]
>  Ve výchozím nastavení jsou povolené odvozených klíčů. Pokud vytvoříte vlastní bezpečnostní token a použijte ho jako primární token, WCF od něj odvozený klíč. V průběhu, volá vlastní bezpečnostní token serializátoru pro zápis <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> pro vlastní bezpečnostní token při serializaci `DerivedKeyToken` k přenosu. Na straně příjemce při deserializaci tokenu vypnout přenášený `DerivedKeyToken` Serializační procedura `SecurityTokenReference` element jako podřízený nejvyšší úrovně v rámci sebe sama. Pokud vlastní bezpečnostní token serializátor nebyl přidán `SecurityTokenReference` element při serializaci její typ klauzuli, je vyvolána výjimka.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Chcete-li vytvořit vlastní bezpečnostní serializátor  
  
1. Definovat nové třídy odvozené od <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> třídy.  
  
2. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> metody, které spoléhá na <xref:System.Xml.XmlReader> číst datový proud XML. Metoda vrátí `true` Pokud serializátor implementace může deserializovat token zabezpečení na základě zadané jeho aktuálního elementu. V tomto příkladu tato metoda zkontroluje, zda čtecí funkce XML je aktuální – element XML má správný element názvem a oborem názvů. Pokud tomu tak není, volá implementaci základní třídy tuto metodu za účelem zpracování elementu XML.  
  
3. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> metody. Tato metoda načte obsah XML tokenu zabezpečení a vytvoří pro ni vhodné vyjádření v paměti. Pokud nebylo rozpoznáno elementu XML, na kterém stojí předaným čtecí funkce XML, volá implementaci základní třídy pro zpracování tokenu typy poskytované systémem.  
  
4. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> metody. Tato metoda vrátí `true` Pokud token reprezentací v paměti (předanou jako argument) může převést na reprezentaci XML. Pokud nelze převést, volá implementaci základní třídy.  
  
5. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> metody. Tato metoda převede reprezentaci token zabezpečení v paměti na reprezentaci XML. Pokud tato metoda nemůže převést, volá implementaci základní třídy.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Po dokončení čtyři předchozích postupů, integrate token zabezpečení vlastního zprostředkovatele tokenů zabezpečení, authenticator, správce a přihlašovací údaje klienta a služby.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Integrovat token zabezpečení vlastního zprostředkovatele tokenů zabezpečení  
  
1. Poskytovatel tokenu zabezpečení vytvoří, upraví (v případě potřeby) a vrátí instance tokenu. Vytvoření vlastního zprostředkovatele pro vlastní bezpečnostní token, vytvořte třídu, která dědí z <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy. Následující příklad přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metoda vrátí instanci `CreditCardToken`. Další informace o poskytovatelích vlastní bezpečnostní token, naleznete v tématu [jak: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Integrovat vlastní bezpečnostní token ověřovací data tokenu zabezpečení  
  
1. Ověřovací data tokenu zabezpečení ověřuje obsah tokenu zabezpečení, když je extrahován ze zprávy. Pokud chcete vytvořit vlastní ověřovací data pro vlastní bezpečnostní token, vytvořte třídu, která dědí z <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> třídy. Následující příklad přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. Další informace o ověřovací data tokenu zabezpečení vlastní najdete v tématu [jak: Vytvořit ověřovací data tokenu zabezpečení vlastní](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Vlastní bezpečnostní token integrovat Správce tokenů zabezpečení  
  
1. Správce tokenů zabezpečení vytvoří odpovídající zprostředkovatel tokenů, ověřovací data zabezpečení a instance serializátoru tokenů. Chcete-li vytvořit vlastní Správce tokenů, vytvořte třídu, která dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy. Primární metody třídy <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> k vytvoření odpovídající zprostředkovatele a přihlašovací údaje klienta nebo službě. Další informace o správcích vlastní bezpečnostní token, naleznete v tématu [názorný postup: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Vlastní bezpečnostní token integrovat vlastního klienta a pověření služby  
  
1. Vlastního klienta a pověření služby musí být přidaný do poskytují rozhraní API pro aplikace, aby umožňoval zadání vlastní informace o tokenu, který se používá vlastní bezpečnostní token infrastruktura dříve vytvořené k zajištění a ověření vlastní bezpečnostní Token obsah. Následující ukázky ukazují, jak to lze provést. Další informace o vlastního klienta a pověření služby najdete v tématu [názorný postup: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Třída parametrů tokenu zabezpečení vlastní vytvořené dříve slouží k informování rozhraní framework zabezpečení WCF, že vlastní bezpečnostní token musí být použito při komunikaci se službou. Následující postup ukazuje, jak to lze provést.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Integrovat vlastní tokenu s vazbou  
  
1. Třída parametrů tokenu zabezpečení vlastní musí být zadána v jednom z parametrů tokenu kolekce, které jsou zveřejněné na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Následující příklad používá kolekci vrácené poskytovatelem `SignedEncrypted`. Kód přidá do všech zpráv odeslaných z klienta ke službě s jeho obsahem automaticky podepsaný a zašifrovaný token vlastní platební karty.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Toto téma popisuje různé části kódu nezbytné k implementaci a použití vlastní token. Pokud chcete zobrazit úplný příklad toho, jak všechny tyto části kódu navzájem propojené, podívejte se na téma [vlastní Token](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.SecurityToken>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>
- <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>
- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvořit vlastní bezpečnostní ověřovací data tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
