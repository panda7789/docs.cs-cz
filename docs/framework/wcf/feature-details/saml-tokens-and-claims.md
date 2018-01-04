---
title: Tokeny a deklarace SAML
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
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2b35ba4da503663a2bb92597ed193c408e7c99b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="saml-tokens-and-claims"></a>Tokeny a deklarace SAML
Zabezpečení kontrolní výrazy Markup Language (SAML) *tokeny* jsou reprezentace XML deklarací identity. Ve výchozím nastavení, tokeny SAML [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] se používá ve scénářích federované zabezpečení *vystavené tokeny*.  
  
 Tokeny SAML provádění příkazů, které jsou sady deklarací identity provedené jednu entitu o jinou entitou. Například ve scénářích federované zabezpečení příkazy jsou vytvářeny pomocí služby tokenů zabezpečení o uživateli v systému. Služby tokenů zabezpečení podepisuje tokeny SAML udávajících pravdivosti příkazy obsažených v tokenu. Kromě toho je přidružen kryptografických materiál klíče, který uživatel tokenu SAML prokáže znalosti o tokenu SAML. Toto ověření splňuje, že předávající stranu, která byla tokenu SAML, ve skutečnosti vydán pro tohoto uživatele. Například v Typický scénář:  
  
1.  Klient požaduje tokenu SAML od služby tokenů zabezpečení, ověřování do této služby tokenů zabezpečení pomocí pověření systému Windows.  
  
2.  Služby tokenů zabezpečení vydá SAML token klientovi. SAML token je podepsaný certifikátem přidružené služby tokenů zabezpečení a obsahuje doklad klíč šifrována pro cílovou službu.  
  
3.  Klient také obdrží kopii *doklad klíč*. Klient pak uvede token SAML, který má služba aplikace ( *předávající strany*) a podepíše zprávu s tímto doklad klíčem.  
  
4.  Podpis přes tokenu SAML poskytuje předávající strany, aby vystavovala služby tokenů zabezpečení token. Podpis zprávy, které jsou vytvořené pomocí doklad klíč informuje předávající strany, zda byl token vydán klientovi.  
  
## <a name="from-claims-to-samlattributes"></a>Z deklarací identity k SamlAttributes  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], příkazy v tokenech SAML jsou modelovat jako <xref:System.IdentityModel.Tokens.SamlAttribute> objekty, které je možné importovat přímo z <xref:System.IdentityModel.Claims.Claim> objekty, zadaný <xref:System.IdentityModel.Claims.Claim> objekt má <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> a <xref:System.IdentityModel.Claims.Claim.Resource%2A> Vlastnost je typu <xref:System.String>. Příklad:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  Při tokeny SAML se serializují ve zprávách, při vydávání pomocí služby tokenů zabezpečení nebo poté, co se zobrazí klienty pro služby v rámci ověřování, kvóta maximální velikosti zprávy musí být dostatečně velký pro uložení tokenu SAML a ostatní části zprávy. V případech, normální výchozích kvót velikost zprávy je dostatečné. V případech, kdy je SAML token velké vzhledem k tomu, že obsahuje stovky deklarace identity, můžete však zvýšit kvóty pro přizpůsobení serializovaný token. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Z SamlAttributes do deklarací identity  
 Když ve zprávách přijme tokeny SAML, jsou různé příkazy v tokenu SAML převedena na <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objekty, které se umístí do <xref:System.IdentityModel.Policy.AuthorizationContext>. Deklarace identity z každý příkaz SAML se vrátí pomocí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> a můžete prověřit, abyste zjistili, jestli se k ověřování a autorizaci uživatele.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [Federace](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Deklarace identity a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Vytvoření deklarace identity a hodnoty prostředků](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Postupy: Vytvoření vlastní deklarace identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
