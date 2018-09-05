---
title: 'Postupy: Vytvoření vlastního ověřovacího modulu tokenu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: cbd45580e84a0723d28bab538bc0ffe388899d61
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724419"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Postupy: Vytvoření vlastního ověřovacího modulu tokenu zabezpečení
Toto téma ukazuje, jak vytvořit ověřovací data tokenu zabezpečení vlastní a jak ji integrovat s Správce tokenů zabezpečení vlastní. Ověřovací data tokenu zabezpečení ověří obsah token zabezpečení, opatřeného příchozí zprávy. Pokud je ověření úspěšné, ověřovacích vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které, při vyhodnocování, vrátí sadu deklarací identity.  
  
 Určený ověřovací data tokenu zabezpečení vlastní ve Windows Communication Foundation (WCF), musíte nejprve vytvořit vlastní přihlašovací údaje a zabezpečení implementace Správce tokenů. Další informace o vytváření vlastních přihlašovacích údajů a zabezpečení Správce tokenů najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Další informace o pověření, Správce tokenů zabezpečení a třídy zprostředkovatele a ověřovací data, najdete v části [architektury zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Chcete-li vytvořit vlastní bezpečnostní ověřovací data tokenu  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> třídy.  
  
2.  Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> metody. Metoda vrátí `true` nebo `false` v závislosti na tom, zda vlastní ověřovací data můžete ověřit příchozí typ tokenu nebo ne.  
  
3.  Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. Tato metoda je potřeba ověřit token obsah odpovídajícím způsobem. Pokud token, který projde krokem ověření, vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí. Následující příklad používá implementaci zásad autorizace, která bude vytvořena v dalším postupu.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Vrátí kolekci objektů zásad autorizace v předchozím kódu <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> metody. WCF neposkytuje veřejné implementace tohoto rozhraní. Následující postup ukazuje, jak na to pro vaše požadavky.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Chcete-li vytvořit vlastní zásady autorizace  
  
1.  Definovat novou implementaci třídy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> rozhraní.  
  
2.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost jen pro čtení. Jedním ze způsobů implementace této vlastnosti je v konstruktoru třídy generovat globálně jedinečný identifikátor (GUID) a vrátit ho pokaždé, když je požadována hodnota této vlastnosti.  
  
3.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost jen pro čtení. Tato vlastnost musí vrátit vystavitele sad deklarací identity, které jsou získány z tokenu. Vystavitel tokenu nebo autoritu, která zodpovídá za ověření tokenu obsah by měl odpovídat vystaviteli. Následující příklad používá deklarace identity vystavitele, který předá do této třídy z vlastní ověřovací data tokenu zabezpečení vytvořené v předchozím postupu. Ověřovací data tokenu zabezpečení vlastní používá sadu deklarací poskytovaných systémem (vrácené <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost) představující vystavitele tokenu uživatelské jméno.  
  
4.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody. Tato metoda naplní instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy (předanou jako argument) s deklarací identity, které jsou založeny na příchozí obsah tokenu zabezpečení. Metoda vrátí `true` po dokončení hodnocení. V případech, při implementaci spoléhá na přítomnost jiných zásad autorizace, které poskytují další informace, které kontext vyhodnocení, tato metoda může vrátit `false` Pokud není k dispozici požadované informace ještě v rámci vyhodnocení. V takovém případě WCF se znovu za vaše rozhodnutí vyzkoušet všechny zásady autorizace pro příchozí zprávy vygenerovat, pokud alespoň jedna z těchto zásad autorizace změnit kontext vyhodnocení volání metody.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) popisuje, jak vytvořit vlastní přihlašovací údaje a vlastní bezpečnostní správce tokenů. Použít vlastní ověřovací data tokenu zabezpečení vytvořené, implementace Správce tokenů zabezpečení je upravit tak, aby vrátit vlastní ověřovací data z <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metody. Pokud požadavek na token zabezpečení je předáno, vrátí metoda ověřovací data.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Ověřovací data tokenu zabezpečení vlastní integrovat Správce tokenů zabezpečení vlastní  
  
1.  Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodu ve vaší implementaci správce tokenů zabezpečení vlastní.  
  
2.  Přidejte logiku do metody, který umožňuje vrátit vaše vlastní ověřovací data tokenu zabezpečení na základě <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Následující příklad vrátí ověřovací data tokenu zabezpečení vlastní, pokud typ tokenu požadavky tokenu je uživatelské jméno (představované <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> vlastnost) a směr zprávy, které jsou požadovány ověřovací data tokenu zabezpečení je vstupu ( reprezentována <xref:System.ServiceModel.Description.MessageDirection.Input> pole).  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
