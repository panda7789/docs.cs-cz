---
title: 'Postup: vytvoření vlastního ověřovacího programu tokenu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: 7bbe59958f59f76046c0a112463cfa64d09c14d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185593"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Postup: vytvoření vlastního ověřovacího programu tokenu zabezpečení
Toto téma ukazuje, jak vytvořit vlastní ověřovací token zabezpečení a jak jej integrovat s vlastní správce tokenů zabezpečení. Ověřovatel token zabezpečení ověří obsah tokenu zabezpečení, který je součástí příchozí zprávy. Pokud ověření proběhne úspěšně, ověřovatel vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které při vyhodnocení vrátí sadu deklarací identity.  
  
 Chcete-li použít vlastní ověřovací zařízení tokenu zabezpečení v systému Windows Communication Foundation (WCF), musíte nejprve vytvořit vlastní pověření a implementace správce tokenů zabezpečení. Další informace o vytváření vlastních přihlašovacích údajů a správce tokenů zabezpečení naleznete v [tématu Návod: Vytvoření vlastních pověření klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md).
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Vytvoření vlastního ověřovacího programu tokenu zabezpečení  
  
1. Definujte novou třídu <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> odvozenou z třídy.  
  
2. Přepsat metodu. <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> Metoda vrátí `true` `false` nebo v závislosti na tom, zda vlastní ověřovatelé můžete ověřit typ příchozího tokenu nebo ne.  
  
3. Přepsat metodu. <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> Tato metoda potřebuje ověřit obsah tokenu odpovídajícím způsobem. Pokud token předá krok ověření, vrátí <xref:System.IdentityModel.Policy.IAuthorizationPolicy> kolekci instancí. Následující příklad používá vlastní implementaci zásad autorizace, která bude vytvořena v dalším postupu.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Předchozí kód vrátí kolekci zásad <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> autorizace v metodě. WCF neposkytuje veřejné implementace tohoto rozhraní. Následující postup ukazuje, jak to udělat pro vaše vlastní požadavky.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Vytvoření vlastní zásady autorizace  
  
1. Definujte novou třídu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementující rozhraní.  
  
2. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost jen pro čtení. Jedním ze způsobů, jak implementovat tuto vlastnost je generovat globálně jedinečný identifikátor (GUID) v konstruktoru třídy a vrátit ji pokaždé, když je požadována hodnota pro tuto vlastnost.  
  
3. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost jen pro čtení. Tato vlastnost musí vrátit vystavittele sady deklarací, které jsou získány z tokenu. Tento vystavitel by měl odpovídat vystavittele tokenu nebo autority, která je zodpovědná za ověření obsahu tokenu. Následující příklad používá deklaraci vystavittele, která byla předána této třídě z vlastního ověřovacího tokenu zabezpečení vytvořeného v předchozím postupu. Vlastní ověřovací objekt tokenu zabezpečení používá sadu deklarací zajišťovnou systémovou (vrácenou <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastností) k reprezentaci vystavittele tokenu uživatelského jména.  
  
4. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metodu. Tato metoda naplní instanci <xref:System.IdentityModel.Policy.EvaluationContext> třídy (předánjako argument) s deklaracemi, které jsou založeny na příchozí obsah tokenu zabezpečení. Metoda vrátí, `true` když se provádí s hodnocením. V případech, kdy implementace závisí na přítomnosti jiných zásad autorizace, které poskytují `false` další informace pro kontext hodnocení, tato metoda může vrátit, pokud požadované informace ještě není k dispozici v kontextu hodnocení. V takovém případě WCF bude volat metodu znovu po vyhodnocení všech ostatních zásad autorizace generovaných pro příchozí zprávy, pokud alespoň jeden z těchto zásad autorizace změnil kontext hodnocení.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Návod: Vytvoření vlastních pověření klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md) popisuje, jak vytvořit vlastní pověření a vlastní správce tokenů zabezpečení. Chcete-li použít vlastní ověřovací token zabezpečení vytvořený zde, implementace správce tokenů zabezpečení je <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> upravena tak, aby vrátila vlastní ověřovatetel z metody. Metoda vrátí ověřovatetele při předání příslušného požadavku tokenu zabezpečení.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Integrace vlastního ověřovacího nástroje tokenu zabezpečení s vlastním správcem tokenů zabezpečení  
  
1. Přepište <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodu v implementaci správce vlastních tokenů zabezpečení.  
  
2. Přidejte logiku k metodě, která mu umožní vrátit <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> vlastní ověřovač tokenu zabezpečení na základě parametru. Následující příklad vrátí vlastní ověřovací paměťový symbol zabezpečení, pokud je typ tokenu požadavků tokenu uživatelské jméno (reprezentované <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> vlastností) a <xref:System.ServiceModel.Description.MessageDirection.Input> směr zprávy, pro který je požadován ověřovací token zabezpečení, je vstup (reprezentované polem).  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  

## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [Návod: Vytvoření vlastního klienta a pověření služby](walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)
