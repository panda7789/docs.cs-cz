---
title: 'Postupy: vytváření vlastních ověřovacích dat tokenu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: b8e964b1124bb19faa79b0dc5e4ecebd83a56acf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797063"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Postupy: vytváření vlastních ověřovacích dat tokenu zabezpečení
V tomto tématu se dozvíte, jak vytvořit vlastní ověřovací data tokenu zabezpečení a jak je integrovat s vlastním správcem tokenů zabezpečení. Ověřovací data tokenu zabezpečení ověřují obsah tokenu zabezpečení, který je k dispozici v příchozí zprávě. Pokud je ověření úspěšné, ověřovatel vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí, které při vyhodnocování vrátí sadu deklarací.  
  
 Pokud chcete použít vlastní ověřovací data tokenu zabezpečení v Windows Communication Foundation (WCF), musíte nejdřív vytvořit vlastní přihlašovací údaje a implementace správce tokenů zabezpečení. Další informace o vytváření vlastních přihlašovacích údajů a Správce tokenů zabezpečení najdete [v tématu Názorný postup: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Vytvoření vlastního ověřovacího ověření tokenu zabezpečení  
  
1. Definujte novou třídu odvozenou z <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> třídy.  
  
2. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> metody. Metoda vrátí `true` nebo `false` v závislosti na tom, zda vlastní ověřovatel může ověřit typ příchozího tokenu nebo ne.  
  
3. Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. Tato metoda potřebuje odpovídajícím způsobem ověřit obsah tokenu. Pokud token projde kroku ověření, vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instancí. V následujícím příkladu se používá implementace vlastní zásady autorizace, která se vytvoří v dalším postupu.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Předchozí kód vrátí kolekci autorizačních zásad v <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> metodě. WCF neposkytuje veřejnou implementaci tohoto rozhraní. Následující postup ukazuje, jak to udělat pro vaše vlastní požadavky.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Vytvoření vlastní zásady autorizace  
  
1. Definujte novou třídu implementující <xref:System.IdentityModel.Policy.IAuthorizationPolicy> rozhraní.  
  
2. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost, která je jen pro čtení. Jedním ze způsobů implementace této vlastnosti je vygenerování globálně jedinečného identifikátoru (GUID) v konstruktoru třídy a jeho vrácení při každém požadavku na hodnotu této vlastnosti.  
  
3. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost, která je jen pro čtení. Tato vlastnost musí vracet Vystavitel sady deklarací, které jsou získány z tokenu. Tento Vydavatel by měl odpovídat vystaviteli tokenu nebo autoritě zodpovědné za ověřování obsahu tokenu. Následující příklad používá deklaraci identity vystavitele, která byla předána této třídě z vlastního ověřovacího tokenu zabezpečení vytvořeného v předchozím postupu. Vlastní ověřovací data tokenu zabezpečení používá systémovou sadu deklarací identity (vrácená <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastností), která představuje vystavitele tokenu uživatelského jména.  
  
4. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metodu. Tato metoda naplní instanci <xref:System.IdentityModel.Policy.EvaluationContext> třídy (předanou jako argument) s deklaracemi, které jsou založeny na příchozím obsahu tokenu zabezpečení. Metoda vrátí `true` , když je provedena s vyhodnocením. V případech, kdy implementace spoléhá na přítomnost jiných zásad autorizace, které poskytují dodatečné informace kontextu vyhodnocení, může tato metoda vracet `false` , pokud požadované informace ještě nejsou přítomny v kontextu vyhodnocení. V takovém případě bude WCF zavolat metodu znovu po vyhodnocení všech dalších autorizačních zásad generovaných pro příchozí zprávu, pokud alespoň jedna z těchto zásad autorizace změnila kontext vyhodnocení.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Návod: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md) klienta a služby popisuje, jak vytvářet vlastní přihlašovací údaje a vlastní Správce tokenů zabezpečení. Pokud chcete použít vlastní ověřovací data tokenu zabezpečení, je implementace správce tokenů zabezpečení upravena tak, aby vracela vlastní ověřovatel z <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metody. Metoda vrátí ověřovatel, pokud je předán příslušný požadavek na token zabezpečení.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Integrace vlastního ověřovacího tokenu zabezpečení pomocí vlastního správce tokenů zabezpečení  
  
1. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> Přepsat metodu ve vlastní implementaci správce tokenů zabezpečení.  
  
2. Přidejte do metody logiku, která mu umožní vrátit vlastní ověřovací data tokenu zabezpečení na základě <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Následující příklad vrátí vlastní ověřovací data tokenu zabezpečení, pokud je typ tokenu požadavků na token uživatelské jméno (reprezentované <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> vlastností) a směr zprávy, pro který se požaduje ověřovací data tokenu zabezpečení, je vstup ( reprezentované <xref:System.ServiceModel.Description.MessageDirection.Input> polem).  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
 
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [Návod: Vytváření vlastních přihlašovacích údajů klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)
