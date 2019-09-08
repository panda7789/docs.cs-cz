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
ms.openlocfilehash: 3bd44d197a655b67253ff363ef15937d4c021e08
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797052"
---
# <a name="how-to-create-a-custom-token"></a>Postupy: Vytvoření vlastního tokenu
V tomto tématu se dozvíte, jak vytvořit vlastní token zabezpečení <xref:System.IdentityModel.Tokens.SecurityToken> pomocí třídy a jak ho integrovat s vlastním poskytovatelem a ověřovatelem tokenů zabezpečení. Úplný příklad kódu najdete v ukázce [vlastního tokenu](../samples/custom-token.md) .  
  
 *Token zabezpečení* je v podstatě element XML, který je používán rozhraním zabezpečení Windows Communication Foundation (WCF) k vyjádření deklarací odesilatele v rámci zprávy protokolu SOAP. Zabezpečení WCF poskytuje různé tokeny pro režimy ověřování poskytované systémem. Mezi příklady patří token zabezpečení certifikátu X. 509 reprezentovaný <xref:System.IdentityModel.Tokens.X509SecurityToken> třídou nebo token zabezpečení uživatelského jména reprezentovaný <xref:System.IdentityModel.Tokens.UserNameSecurityToken> třídou.  
  
 V některých případech není režim ověřování nebo pověření podporován zadanými typy. V takovém případě je nutné vytvořit vlastní token zabezpečení, který poskytuje reprezentaci XML vlastního pověření v rámci zprávy protokolu SOAP.  
  
 Následující postupy ukazují, jak vytvořit vlastní token zabezpečení a jak ho integrovat s infrastrukturou zabezpečení WCF. V tomto tématu se vytvoří token platební karty, který se používá k předání informací o platební kartě klienta na server.  
  
 Další informace o vlastních přihlašovacích údajích a správci tokenů [zabezpečení najdete v návodu: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
 Další třídy, které reprezentují tokeny zabezpečení, naleznete v oborunázvů.<xref:System.IdentityModel.Tokens>  
  
## <a name="procedures"></a>Procedury  
 Klientská aplikace musí být poskytována způsobem, který umožňuje zadat informace o kreditních kartách pro infrastrukturu zabezpečení. Tyto informace zpřístupní aplikace vlastní třídou přihlašovacích údajů klienta. Prvním krokem je vytvoření třídy, která představuje informace o kreditních kartách pro vlastní přihlašovací údaje klienta.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Vytvoření třídy, která představuje informace o kreditních kartách v přihlašovacích údajích klienta  
  
1. Definujte novou třídu, která představuje informace o kreditní kartě pro danou aplikaci. Následující příklad pojmenuje třídu `CreditCardInfo`.  
  
2. Přidejte do třídy příslušné vlastnosti, aby aplikace mohla nastavit potřebné informace vyžadované pro vlastní token. V tomto příkladu má třída tři vlastnosti: `CardNumber`, `CardIssuer`a `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Dále musí být vytvořena třída, která představuje vlastní token zabezpečení. Tuto třídu používá poskytovatel tokenů zabezpečení, ověřovatel a třídy serializátoru k předávání informací o tokenu zabezpečení do a z infrastruktury zabezpečení WCF.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Vytvoření vlastní třídy tokenu zabezpečení  
  
1. Definujte novou třídu odvozenou z <xref:System.IdentityModel.Tokens.SecurityToken> třídy. Tento příklad vytvoří třídu s názvem `CreditCardToken`.  
  
2. Přepište <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> vlastnost. Tato vlastnost slouží k získání místního identifikátoru tokenu zabezpečení, který se používá k odkazování na reprezentaci XML tokenu zabezpečení z jiných prvků uvnitř zprávy protokolu SOAP. V tomto příkladu může být identifikátor tokenu předán buď jako parametr konstruktoru, nebo je nová náhodná instance generována pokaždé, když je vytvořena instance tokenu zabezpečení.  
  
3. Implementujte <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> vlastnost. Tato vlastnost vrací kolekci zabezpečovacích klíčů, které představuje instance tokenu zabezpečení. Tyto klíče může služba WCF použít k podepisování nebo šifrování částí zprávy protokolu SOAP. V tomto příkladu token zabezpečení platební karty nemůže obsahovat žádné klíče zabezpečení; Proto implementace vždycky vrátí prázdnou kolekci.  
  
4. Přepište vlastnosti <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A>a. <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> Tyto vlastnosti používá služba WCF k určení platnosti instance tokenu zabezpečení. V tomto příkladu má token zabezpečení platební karty pouze datum vypršení platnosti, takže `ValidFrom` vlastnost vrátí hodnotu <xref:System.DateTime> , která představuje datum a čas vytvoření instance.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Když je vytvořen nový typ tokenu zabezpečení, vyžaduje implementaci <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy. Implementace se používá v konfiguraci elementu vazby zabezpečení, která představuje nový typ tokenu. Třída parametrů tokenu zabezpečení slouží jako šablona, která se používá k vyhledání skutečné instance tokenu zabezpečení při zpracování zprávy. Šablona poskytuje další vlastnosti, které může aplikace použít k určení kritérií, která se musí shodovat s použitým nebo ověřeným tokenem zabezpečení. Následující příklad nepřidá žádné další vlastnosti, takže pouze typ tokenu zabezpečení je porovnán, když infrastruktura WCF vyhledá instanci tokenu zabezpečení, která se má použít nebo ověřit.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Chcete-li vytvořit vlastní třídu parametrů tokenu zabezpečení  
  
1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy.  
  
2. Implementujte <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> metodu. Zkopírujte všechna interní pole definovaná ve vaší třídě, pokud existují. Tento příklad nedefinuje žádná další pole.  
  
3. Implementujte <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> vlastnost, která je jen pro čtení. Tato vlastnost vrátí `true` , zda je možné použít typ tokenu zabezpečení reprezentovaný touto třídou k ověření klienta ke službě. V tomto příkladu se dá token zabezpečení platební karty použít k ověření klienta ke službě.  
  
4. Implementujte <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> vlastnost, která je jen pro čtení. Tato vlastnost vrátí `true` , zda je možné použít typ tokenu zabezpečení reprezentovaný touto třídou k ověření služby klientovi. V tomto příkladu nelze pomocí tokenu zabezpečení platební karty ověřit službu pro klienta.  
  
5. Implementujte <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> vlastnost, která je jen pro čtení. Tato vlastnost vrátí `true` , pokud typ tokenu zabezpečení reprezentovaný touto třídou může být namapován na účet systému Windows. V takovém případě je výsledek ověřování reprezentován <xref:System.Security.Principal.WindowsIdentity> instancí třídy. V tomto příkladu nelze token namapovat na účet systému Windows.  
  
6. Implementujte <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> metodu. Tato metoda je volána rozhraním zabezpečení WCF, pokud vyžaduje odkaz na instanci tokenu zabezpečení reprezentovanou touto třídou parametrů tokenu zabezpečení. Do této metody se jako argumenty předává skutečná instance <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> tokenu zabezpečení, která určuje typ odkazu, který se požaduje. V tomto příkladu se token zabezpečení platební karty podporuje jenom interní odkazy. <xref:System.IdentityModel.Tokens.SecurityToken> Třída má funkce pro vytváření interních odkazů, proto implementace nevyžaduje další kód.  
  
7. Implementujte <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodu. Tato metoda je volána službou WCF k převedení instance třídy parametrů tokenu zabezpečení na instanci <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> třídy. Výsledek je používán zprostředkovateli tokenů zabezpečení k vytvoření příslušné instance tokenu zabezpečení.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokeny zabezpečení jsou přenášeny v rámci zpráv SOAP, což vyžaduje mechanismus překladu mezi reprezentací tokenu zabezpečení v paměti a reprezentací na základě přenosu. WCF používá ke splnění této úlohy serializátor tokenů zabezpečení. Každý vlastní token musí být doprovázen vlastním serializátorem tokenu zabezpečení, který může serializovat a deserializovat vlastní token zabezpečení ze zprávy protokolu SOAP.  
  
> [!NOTE]
> Ve výchozím nastavení jsou povolené odvozené klíče. Pokud vytvoříte vlastní token zabezpečení a použijete ho jako primární token, WCF z něj odvozuje klíč. V takovém případě zavolá vlastní serializátor tokenu zabezpečení, který zapíše <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> vlastní token zabezpečení při serializaci `DerivedKeyToken` na síťový kabel. Při deserializaci tokenu `DerivedKeyToken` na straně příjmu využije serializátor `SecurityTokenReference` jako podřízený prvek nejvyšší úrovně. Pokud vlastní serializátor tokenu zabezpečení nepřidal `SecurityTokenReference` element při serializaci jeho typu klauzule, je vyvolána výjimka.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Vytvoření vlastního serializátoru tokenů zabezpečení  
  
1. Definujte novou třídu odvozenou z <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> třídy.  
  
2. Přepsat metodu, která spoléhá <xref:System.Xml.XmlReader> na pro čtení streamu XML. <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> Metoda vrátí `true` , zda implementace serializátoru může deserializovat token zabezpečení na základě aktuálního prvku. V tomto příkladu Tato metoda ověřuje, zda má aktuální element XML čtecího modulu XML správný název elementu a obor názvů. Pokud tomu tak není, volá implementaci této metody základní třídy pro zpracování XML elementu.  
  
3. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> metody. Tato metoda přečte obsah XML tokenu zabezpečení a vytvoří odpovídající reprezentaci v paměti. Pokud nerozpozná element XML, na kterém je předaný modul XML Reader, zavolá implementaci základní třídy pro zpracování typů tokenů poskytnutých systémem.  
  
4. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> metody. Tato metoda vrátí `true` , zda může převést reprezentaci tokenu v paměti (předaná jako argument) do reprezentace XML. Pokud se nemůže převést, volá implementaci základní třídy.  
  
5. Přepsat <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> metody. Tato metoda převede reprezentace tokenu zabezpečení v paměti na reprezentaci XML. Pokud metoda nemůže převést, volá implementaci základní třídy.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Až dokončíte čtyři předchozí postupy, Integrujte vlastní token zabezpečení se zprostředkovatelem tokenu zabezpečení, ověřovatelem, správcem a přihlašovacími údaji klienta a služby.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Integrace vlastního tokenu zabezpečení s poskytovatelem tokenu zabezpečení  
  
1. Poskytovatel tokenu zabezpečení vytvoří, upraví (v případě potřeby) a vrátí instanci tokenu. Chcete-li vytvořit vlastního zprostředkovatele pro vlastní token zabezpečení, vytvořte třídu, která dědí z <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy. Následující příklad přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metodu pro vrácení instance `CreditCardToken`. Další informace o vlastních poskytovatelích tokenů zabezpečení naleznete [v tématu How to: Vytvořte vlastního poskytovatele](how-to-create-a-custom-security-token-provider.md)tokenů zabezpečení.  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Integrace vlastního tokenu zabezpečení s ověřovacími daty tokenu zabezpečení  
  
1. Ověřovací data tokenu zabezpečení ověřují obsah tokenu zabezpečení při jeho extrakci ze zprávy. Chcete-li vytvořit vlastní ověřovatel pro vlastní token zabezpečení, vytvořte třídu, která dědí z <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> třídy. Následující příklad přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metodu. Další informace o vlastních ověřovacích tokenech tokenu zabezpečení [najdete v tématu How to: Vytvořte vlastní ověřovací data](how-to-create-a-custom-security-token-authenticator.md)tokenu zabezpečení.  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Integrace vlastního tokenu zabezpečení se správcem tokenů zabezpečení  
  
1. Správce tokenů zabezpečení vytvoří odpovídajícího poskytovatele tokenů, ověřovatelů zabezpečení a instancí serializátoru tokenů. Chcete-li vytvořit vlastního správce tokenů, vytvořte třídu, která dědí <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> z třídy. Primární metody třídy používají <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> k vytvoření příslušného poskytovatele a pověření klienta nebo služby. Další informace o vlastních správcích tokenů zabezpečení najdete [v tématu Návod: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Integrace vlastního tokenu zabezpečení s vlastními přihlašovacími údaji klienta a služby  
  
1. Aby bylo možné zadat rozhraní API pro aplikaci, aby bylo možné zadat vlastní informace o tokenu používané vlastní infrastrukturou tokenů zabezpečení, která byla dříve vytvořena pro zadání a ověření vlastního zabezpečení, musí být přidána vlastní pověření klienta a služby. obsah tokenu Následující ukázky ukazují, jak to lze provést. Další informace o vlastních pověřeních klienta a služby najdete v [článku Návod: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Vlastní třída tokenů zabezpečení, která byla vytvořena dříve, slouží k oznámení architektury zabezpečení WCF, že vlastní token zabezpečení musí být použit při komunikaci se službou. Následující postup ukazuje, jak to lze provést.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Integrace vlastního tokenu zabezpečení s vazbou  
  
1. Třída vlastních parametrů tokenu zabezpečení musí být zadána v jedné z kolekcí parametrů tokenů, které jsou zpřístupněny <xref:System.ServiceModel.Channels.SecurityBindingElement> ve třídě. Následující příklad používá kolekci vrácenou `SignedEncrypted`. Kód přidá vlastní token platební karty do každé zprávy odesílané z klienta do služby s jeho obsahem automaticky podepsaný a zašifrovaný.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Toto téma ukazuje různé části kódu, které jsou nezbytné k implementaci a použití vlastního tokenu. Úplný příklad toho, jak se všechny tyto části vejdou do kódu, najdete v části [vlastní token](../samples/custom-token.md).  
  
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
- [Návod: Vytváření vlastních přihlašovacích údajů klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení](how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)
