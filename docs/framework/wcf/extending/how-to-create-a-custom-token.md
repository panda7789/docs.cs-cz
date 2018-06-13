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
ms.openlocfilehash: 2198d5548b09ba05eeb11466a6fd2d3a1262de94
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809206"
---
# <a name="how-to-create-a-custom-token"></a>Postupy: Vytvoření vlastního tokenu
Toto téma ukazuje, jak vytvořit vlastní zabezpečovací tokenu pomocí <xref:System.IdentityModel.Tokens.SecurityToken> třídy a jak integrovat s zprostředkovatele tokenu vlastní zabezpečovací a ověřovací data. Kompletní příklad najdete v článku [vlastní tokenu](../../../../docs/framework/wcf/samples/custom-token.md) ukázka.  
  
 A *token zabezpečení* je v podstatě elementu XML, který je používán zabezpečení systému Windows Communication Foundation (WCF) představují deklarace identity o odesílateli v zprávu protokolu SOAP. Zabezpečení WCF poskytuje různé tokeny pro režimy ověřování poskytované systémem. Mezi příklady patří token zabezpečení certifikátu X.509 reprezentována <xref:System.IdentityModel.Tokens.X509SecurityToken> třídu nebo token zabezpečení uživatelské jméno reprezentována <xref:System.IdentityModel.Tokens.UserNameSecurityToken> – třída.  
  
 Zadané typy nepodporuje někdy režim ověřování nebo pověření. V takovém případě je potřeba vytvořit token zabezpečení vlastní zajistit reprezentaci XML vlastní pověření uvnitř zprávu protokolu SOAP.  
  
 Následující postupy ukazují, jak vytvořit token vlastní zabezpečení a postup při integraci s Infrastruktura zabezpečení WCF. Toto téma vytvoří platební karty token, který slouží k předávání informací o platební karty klienta k serveru.  
  
 Další informace o vlastní pověření a Správce tokenů zabezpečení najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Najdete v článku <xref:System.IdentityModel.Tokens> obor názvů pro více tříd, které představují tokeny zabezpečení.  
  
 Další informace o pověření, Správce tokenů zabezpečení a třídy zprostředkovatele a ověřovací najdete v tématu [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
 Klientská aplikace je třeba zadat způsob, jak určit informace o platební karty pro zabezpečení infrastruktury. Tyto informace je k dispozici pro aplikaci třídou přihlašovací údaje vlastního klienta. Prvním krokem je vytvoření třídy představující informace o kreditní kartě pro přihlašovací údaje vlastního klienta.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Chcete-li vytvořit třídu, která představuje informace o kreditní kartě uvnitř pověření klienta  
  
1.  Definujte novou třídu, která představuje údaje platební karty pro aplikaci. Následující příklad názvy třídy `CreditCardInfo`.  
  
2.  Přidejte příslušné vlastnosti do třídy tak, aby umožnily že aplikace nastavit nezbytné informace požadované pro vlastní token. V tomto příkladu třída má tři vlastnosti: `CardNumber`, `CardIssuer`, a `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 V dalším kroku je nutné vytvořit třídu, která představuje token, který vlastní zabezpečení. Tato třída se používá poskytovatele tokenu zabezpečení, authenticator a třídy serializátor předávat informace o tokenu zabezpečení do a z Infrastruktura zabezpečení WCF.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Pro vytvoření třídy tokenu vlastní zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Tokens.SecurityToken> třídy. Tento příklad vytvoří třídu s názvem `CreditCardToken`.  
  
2.  Přepsání <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> vlastnost. Tato vlastnost slouží k získání místní identifikátor tokenu zabezpečení, který se používá k bod k reprezentaci XML tokenu zabezpečení z dalších prvků uvnitř zprávu protokolu SOAP. V tomto příkladu identifikátor tokenu lze buď předat ji jako parametr konstruktoru nebo novou náhodných je generována pokaždé, když se vytvoří instance tokenu zabezpečení.  
  
3.  Implementace <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> vlastnost. Tato vlastnost vrátí kolekci klíčů zabezpečení, které představuje instanci tokenu zabezpečení. Tyto klíče může sloužit k podepisování nebo šifrování částí zprávu SOAP WCF. V tomto příkladu platební karty token zabezpečení nemůže obsahovat žádné klíče zabezpečení; proto implementace vždy vrátí prázdnou kolekci.  
  
4.  Přepsání <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> a <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> vlastnosti. Tyto vlastnosti jsou používány WCF pro určení platnosti instance tokenu zabezpečení. V tomto příkladu platební karty token zabezpečení obsahuje pouze datum vypršení platnosti, proto `ValidFrom` vlastnost vrátí <xref:System.DateTime> představující datum a čas vytvoření instance.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Když nového zabezpečení se vytvoří typ tokenu, vyžaduje implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy. Implementace se používá v konfiguraci zabezpečení vazby element představující nový typ tokenu. Třída parametry token zabezpečení slouží jako šablonu, která se používá k porovnání instance tokenu zabezpečení pro při zpracování zprávy. Šablona nabízí další vlastnosti, které aplikace můžete použít k určení kritéria, která musí odpovídat tokenu zabezpečení k použití nebo ověření. Následující příklad nepřidává žádné další vlastnosti, takže jenom zabezpečení typ tokenu je nalezena shoda při hledání infrastruktury WCF pro instanci tokenu zabezpečení nebo ověření.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Pro vytvoření třídy tokenu parametry vlastní zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy.  
  
2.  Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> metoda. Zkopírujte všechny interní pole definovaná v třídě, pokud existuje. Tento příklad nedefinuje žádné další pole.  
  
3.  Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> vlastnost určenou jen pro čtení. Tato vlastnost vrací `true` Pokud typ tokenu zabezpečení, který je reprezentován Tato třída slouží k ověření klienta pro službu. V tomto příkladu platební karty token zabezpečení slouží k ověření klienta pro službu.  
  
4.  Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> vlastnost určenou jen pro čtení. Tato vlastnost vrací `true` Pokud typ tokenu zabezpečení, který je reprezentován Tato třída slouží k ověření služby klienta. V tomto příkladu platební karty token zabezpečení nelze použít k ověření služby klienta.  
  
5.  Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> vlastnost určenou jen pro čtení. Tato vlastnost vrací `true` Pokud typ tokenu zabezpečení, který je reprezentována této třídy lze mapovat na účet systému Windows. Pokud ano, je reprezentována výsledek ověřování <xref:System.Security.Principal.WindowsIdentity> instance třídy. V tomto příkladu token nelze mapovat na účet systému Windows.  
  
6.  Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> metoda. Tato metoda je volána rámcem zabezpečení WCF, pokud se vyžaduje odkaz na instanci tokenu zabezpečení reprezentovaný touto třídou Parametry tokenu zabezpečení. Obě skutečné zabezpečení tokenu instance a <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> určující typ odkazu na element, který je vyžadován jsou předaná této metodě jako argumenty. V tomto příkladu jsou podporovány pouze interní odkazy platební karty token zabezpečení. <xref:System.IdentityModel.Tokens.SecurityToken> Třída má funkce k vytvoření interní odkazy; proto implementace nevyžaduje žádný další kód.  
  
7.  Implementace <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metoda. Tato metoda je volána službou WCF k převedení instance třídy Parametry tokenu zabezpečení do instance <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> třídy. Výsledek slouží poskytovatelé tokenů zabezpečení pro vytvoření instance tokenu příslušné zabezpečení.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokeny zabezpečení, se přenáší uvnitř protokolu SOAP zprávy, které vyžaduje mechanismus překlad mezi reprezentace tokenu zabezpečení v paměti a na síťové vyjádření. WCF používá serializátoru tokenů zabezpečení k provedení této úlohy. Každý vlastní token musí být doplněn vlastní zabezpečovací tokenu serializátoru, který lze serializaci a deserializaci token zabezpečení vlastní zprávu protokolu SOAP.  
  
> [!NOTE]
>  Odvozené klíče jsou ve výchozím nastavení povolené. Pokud vytvoříte vlastní zabezpečovací token a použít jako primární token, WCF odvozena z něj klíč. Při to uděláte, zavolá serializátoru tokenů zabezpečení vlastní k zápisu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> pro token vlastní zabezpečení při serializaci `DerivedKeyToken` k drátové síti. Na koncové straně příjmu, při deserializaci token vypnutí přenosu `DerivedKeyToken` serializátor očekává `SecurityTokenReference` element jako podřízený objekt nejvyšší úrovně v rámci samotného. Pokud serializátoru tokenů zabezpečení vlastní nebyla přidána `SecurityTokenReference` elementu při serializaci typ klauzule, je vyvolána výjimka.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Chcete-li vytvořit vlastní zabezpečovací serializátor  
  
1.  Definovat nové třídy odvozené od <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> třídy.  
  
2.  Přepsání <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> metodu, která využívá <xref:System.Xml.XmlReader> číst datový proud XML. Vrátí metoda `true` Pokud implementace serializátor může deserializovat token zabezpečení na základě zadané jeho aktuálního elementu. V tomto příkladu tato metoda zkontroluje, zda čtecí modul XML je aktuální – element XML má správný element názvem a oborem názvů. Pokud není, volá základní třída implementace této metody pro zpracování XML elementu.  
  
3.  Přepsání <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> metoda. Tato metoda načítá obsah XML tokenu zabezpečení a vytvoří odpovídající reprezentace v paměti pro ni. Pokud nebyl rozpoznán elementu XML, na kterém je stálý předané čtecí modul XML, zavolá implementace základní třída pro zpracování typy tokenů poskytované systémem.  
  
4.  Přepsání <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> metoda. Tato metoda vrátí hodnotu `true` Pokud token reprezentace v paměti (předaná jako argument) může převést k reprezentaci XML. Pokud nemůže převést, zavolá implementaci základní třídy.  
  
5.  Přepsání <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> metoda. Tato metoda převede reprezentaci tokenu zabezpečení v paměti na reprezentaci XML. Pokud tato metoda nemůže převést, zavolá implementaci základní třídy.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Po dokončení předchozí čtyři postupů, integrate token zabezpečení vlastní poskytovatele tokenu zabezpečení, authenticator, správce a přihlašovací údaje klienta a služby.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Pro integraci token zabezpečení vlastní poskytovatele tokenu zabezpečení  
  
1.  Zprostředkovatel tokenu zabezpečení vytvoří, změní (v případě potřeby) a vrací instanci třídy token. Pokud chcete vytvořit vlastní poskytovatele pro token vlastní zabezpečení, vytvořte třídu, která dědí z <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy. Následující příklad přepíše <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metoda vrátí instanci `CreditCardToken`. Další informace o poskytovatele tokenů vlastní zabezpečení najdete v tématu [postupy: vytvoření vlastního poskytovatele tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Pro integraci token zabezpečení vlastního ověřovacího modulu tokenu zabezpečení  
  
1.  Ověřovacího modulu tokenu zabezpečení ověří obsah token zabezpečení, když je extrahována ze zprávy. Pokud chcete vytvořit vlastní ověřovací token vlastní zabezpečení, vytvořte třídu, která dědí z <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> třídy. Následující příklad přepíše <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metoda. Další informace o ověřovací data tokenu vlastní zabezpečení najdete v tématu [postupy: vytvoření vlastní ověřovací Token zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Pro integraci token zabezpečení vlastní Správce tokenů zabezpečení  
  
1.  Správce tokenů zabezpečení vytvoří odpovídající zprostředkovatel tokenu, nástroj pro ověření zabezpečení a instance serializátoru tokenů. Pokud chcete vytvořit vlastní Správce tokenů, vytvořte třídu, která dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy. Primární metody použití třídy <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> vytvoření příslušného poskytovatele a klienta služby Windows nebo pověření. Další informace o správcích tokenu zabezpečení vlastní najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Pro integraci token vlastní zabezpečení vlastního klienta a pověření služby  
  
1.  Vlastního klienta a pověření služby musí být přidaný do poskytují rozhraní API pro aplikace umožňující zadání vlastní tokenu informace, které se používá vlastní zabezpečovací tokenu infrastruktura předtím vytvořili pro účely poskytování a ověření vlastní zabezpečení Token obsah. Následující ukázky ukazují, jak to lze provést. Další informace o vlastních klienta a pověření služby najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Třídě tokenu parametry vlastní zabezpečení vytvořené dříve se používá rozhraní zabezpečení WCF říct, že token zabezpečení vlastní musí použít při komunikaci se službou. Následující postup ukazuje, jak to lze provést.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Pro integraci token zabezpečení vlastní vazby  
  
1.  Třída tokenu parametry vlastní zabezpečení se musí zadat v jednom z tokenu parametry kolekce, které jsou zveřejněné na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Následující příklad používá kolekce vrácené `SignedEncrypted`. Kód přidá vlastní token platební karty do všech zpráv odeslaných z klienta do služby s jeho obsahem automaticky podepsat a zašifrovat.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 Toto téma ukazuje různé části kódu, nezbytné k implementaci a použití vlastního tokenu. Zobrazíte kompletní příklad toho, jak tyto údaje kódu zapadají najdete [vlastní Token](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.SecurityToken>  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>  
 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
