---
title: Tokeny a deklarace SAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: 04517e5089f55c2d2b08a492439026d33ed9069d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339837"
---
# <a name="saml-tokens-and-claims"></a>Tokeny a deklarace SAML
Kontrolní výrazy jazyka SAML (Security Markup) *tokeny* jsou XML reprezentací deklarace identity. Ve výchozím nastavení, tokeny SAML Windows Communication Foundation (WCF) používá ve scénářích zabezpečení jsou *tokeny vydané*.  
  
 Tokeny SAML provádět příkazy, které jsou sady deklarací identity od jedné entitě o jiné entity. Například ve scénářích zabezpečení příkazy jsou prováděny služby tokenů zabezpečení o uživateli v systému. Služba tokenů zabezpečení přihlásí token SAML k označení pravdivosti příkazy obsažených v tokenu. Kromě toho SAML token je přidružen kryptografický materiál klíče, který uživatel tokenu SAML prokáže znalosti. Toto ověření splňuje předávající strany, který byl SAML token, ve skutečnosti vydán pro tohoto uživatele. Například v rámci typického scénáře:  
  
1. Klient požádá o SAML token od služby tokenů zabezpečení, ověřování pomocí přihlašovacích údajů Windows na tuto službu tokenů zabezpečení.  
  
2. Služba tokenů zabezpečení vydá SAML token do klienta. SAML token je podepsaný certifikátem související se službou tokenu zabezpečení a obsahuje klíč důkazu šifrována pro cílovou službu.  
  
3. Klient také obdrží kopii *klíč důkazu*. Klient pak poskytne tokenu SAML pro aplikační služby ( *předávající straně*) a podepíše zprávy pomocí tohoto klíče důkazu.  
  
4. Podpis v tokenu SAML říká předávající strany, služba tokenů zabezpečení token vydala. Podpis zprávy, vytvoří se klíč důkazu říká předávající strany, že byl vydán token do klienta.  
  
## <a name="from-claims-to-samlattributes"></a>Z deklarací identity k SamlAttributes  
 Ve službě WCF, jsou příkazy v tokenech SAML nemodelují jako <xref:System.IdentityModel.Tokens.SamlAttribute> objekty, které je možné importovat přímo z <xref:System.IdentityModel.Claims.Claim> objekty, které jsou k dispozici <xref:System.IdentityModel.Claims.Claim> má objekt <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> a <xref:System.IdentityModel.Claims.Claim.Resource%2A> vlastnost je typ <xref:System.String>. Příklad:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  Při tokeny SAML serializují ve zprávách, když jsou vydané služby tokenů zabezpečení nebo když jsou prezentované podle klientům služby ověřování v rámci, kvóta maximální velikosti musí být dostatečně velký pro přizpůsobení tokenu SAML a ostatní části zprávy. V případech, normální postačí výchozí kvóty velikosti zprávy. Ale v případech, kdy je SAML token velké vzhledem k tomu, že obsahuje stovky deklarace identity, budete muset zvýšit kvóty tak, aby vyhovovaly serializovaný token. Další informace najdete v tématu [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Z SamlAttributes pro deklarace identity  
 Když tokeny SAML přijme ve zprávách, různé příkazy v tokenu SAML jsou převedena na <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objekty, které se umístí do <xref:System.IdentityModel.Policy.AuthorizationContext>. Deklarace identity z každého příkazu SAML jsou vráceny pomocí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> a můžete prověřit, abyste zjistili, jestli se má ověřovat a autorizovat uživatele.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federace](../../../../docs/framework/wcf/feature-details/federation.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Správa deklarací a autorizace s modelem identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Deklarace a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Vytvoření nároku a hodnoty prostředků](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Postupy: Vytvoření vlastní deklarace](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
