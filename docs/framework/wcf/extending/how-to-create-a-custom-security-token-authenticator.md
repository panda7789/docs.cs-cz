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
ms.openlocfilehash: ba554ed23ae039796f51f4a699d368c4a6c0587e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Postupy: Vytvoření vlastního ověřovacího modulu tokenu zabezpečení
Toto téma ukazuje, jak vytvořit ověřovacího modulu tokenu vlastní zabezpečení a postup při integraci s tokenu správce vlastní zabezpečení. Ověřovací data tokenu zabezpečení ověří obsah token zabezpečení, která je součástí příchozí zprávy. Pokud je ověření úspěšné, ověřovacích vrátí kolekci <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instance, při hodnocení, vrátí sadu deklarací identity.  
  
 Použití ověřovacího modulu tokenu vlastní zabezpečení ve Windows Communication Foundation (WCF), musíte nejprve vytvořit vlastní pověření a zabezpečení implementace Správce tokenu. Další informace o vytváření vlastních přihlašovacích údajů a zabezpečení Správce tokenu najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Další informace o pověření, Správce tokenů zabezpečení a třídy zprostředkovatele a ověřovací najdete v tématu [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>K vytvoření ověřovacího modulu tokenu vlastní zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> třídy.  
  
2.  Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> metoda. Vrátí metoda `true` nebo `false` v závislosti na tom, zda vlastní ověřovací můžete ověřit příchozí typ tokenu, nebo ne.  
  
3.  Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metoda. Tato metoda je potřeba ověřit token obsah správně. Pokud je token předá krok ověření, vrátí kolekce <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instance. Následující příklad používá implementaci zásad autorizace, který bude vytvořen v dalším postupu.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Vrátí kolekci zásady autorizace v předchozí kód <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> metoda. WCF neposkytuje veřejné implementace tohoto rozhraní. Následující postup ukazuje, jak to provést pro vaše vlastní požadavky.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Chcete-li vytvořit vlastní zásady autorizace  
  
1.  Definovat nové implementace třídy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> rozhraní.  
  
2.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost určenou jen pro čtení. Jeden způsob, jak implementovat tato vlastnost je generování globálně jedinečný identifikátor (GUID) v konstruktoru třídy a obnoví v něm pokaždé, když je požadována hodnota této vlastnosti.  
  
3.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost určenou jen pro čtení. Tato vlastnost musí vrátit vystavitele sad deklarací identity, které jsou získány z tokenu. Vystavitel tokenu nebo autoritu, která je odpovědná za ověření tokenu obsah by měl odpovídat vystaviteli. Následující příklad používá vystavitele deklarace identity, která předaný Tato třída z vlastního ověřovacího modulu tokenu zabezpečení vytvořené v předchozím postupu. Ověřovací data tokenu zabezpečení vlastní používá sadu deklarací identity poskytované systémem (vrácený <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost) představují Vystavitel tokenu uživatelské jméno.  
  
4.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metoda. Tato metoda naplňuje instance <xref:System.IdentityModel.Policy.EvaluationContext> – třída (předaná jako argument) s deklaracemi identity, které jsou založeny na příchozí obsah tokenu zabezpečení. Vrátí metoda `true` když se provádí s vyhodnocení. V případech při implementaci spoléhá na přítomnost jiné zásady autorizace, které obsahují další informace o kontextu vyhodnocení, tato metoda může vrátit `false` Pokud není k dispozici požadované informace ještě v kontextu vyhodnocení. V takovém případě WCF, bude volat metodu znovu po vyhodnocení všechny zásady autorizace vyvolala pro příchozí zprávy v případě, že nejméně jedna z těchto zásad autorizace Upravit kontext vyhodnocení.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) popisuje, jak vytvořit vlastní pověření a vlastní zabezpečení Správce tokenu. Použít vlastní bezpečnostního znaku vytvořen zde implementaci správce tokenů zabezpečení je upravit tak, aby vrátit vlastní authenticator z <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metoda. Metoda vrátí ověřovací data, pokud je předaná token požadavku na příslušné zabezpečení.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Pro integraci ověřovacího modulu tokenu vlastní zabezpečení Správce tokenů vlastní zabezpečení  
  
1.  Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metoda v implementaci vlastní zabezpečení Správce tokenu.  
  
2.  Způsob povolení ho vrátit vašeho vlastního ověřovacího modulu tokenu zabezpečení na základě přidat logiku <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr. Následující příklad vrací ověřovacího modulu tokenu vlastní zabezpečení, pokud je typ tokenu tokenu požadavky uživatelské jméno (reprezentována <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> vlastnosti) a vstupních (směr zprávy, pro které je požadováno ověřovacího modulu tokenu zabezpečení reprezentována <xref:System.ServiceModel.Description.MessageDirection.Input> pole).  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
