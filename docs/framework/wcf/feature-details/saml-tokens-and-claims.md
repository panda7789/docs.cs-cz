---
title: Tokeny a deklarace SAML
description: Naučte se, jak WFC používá tokeny SAML k přenosu příkazů, které jsou sadami deklarací, které provedla jedna entita o jiné entitě.
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
ms.openlocfilehash: c054e594af69def96879852a5145675b3123614a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244943"
---
# <a name="saml-tokens-and-claims"></a>Tokeny a deklarace SAML
*Tokeny* SAML (Security Assert Markup Language) představují reprezentace deklarací XML. Ve výchozím nastavení používají tokeny SAML Windows Communication Foundation (WCF) ve federovaném scénáři zabezpečení *tokeny*.  
  
 Tokeny SAML přenášejí příkazy, které jsou sady deklarací, které provedla jedna entita o jiné entitě. Například ve scénářích federovaného zabezpečení jsou příkazy provedeny službou tokenu zabezpečení o uživateli v systému. Služba tokenů zabezpečení podepíše token SAML, aby označovala pravdivost příkazů obsažených v tokenu. Token SAML je navíc spojen s materiálem kryptografického klíče, který uživatel tokenu SAML prokáže jako znalosti. Tento důkaz splňuje předávající stranu, kterou token SAML ve skutečnosti vystavil tomuto uživateli. Například v typickém scénáři:  
  
1. Klient požádá o token SAML ze služby tokenu zabezpečení a ověří tuto službu tokenu zabezpečení pomocí pověření systému Windows.  
  
2. Služba tokenů zabezpečení vydá klientovi token SAML. Token SAML je podepsaný certifikátem přidruženým ke službě tokenu zabezpečení a obsahuje ověřovací klíč zašifrovaný pro cílovou službu.  
  
3. Klient také obdrží kopii *ověřovacího klíče*. Klient pak předloží token SAML Aplikační službě ( *předávající straně*) a podepíše zprávu pomocí tohoto klíčového kontrolního klíče.  
  
4. Podpis přes token SAML informuje předávající stranu, že se token vystavil službou tokenu zabezpečení. Podpis zprávy vytvořený pomocí klíče důkazu oznamuje předávající straně, že byl token vydán klientovi.  
  
## <a name="from-claims-to-samlattributes"></a>Z deklarací identity na SamlAttributes  
 V rámci WCF jsou příkazy v tokenech SAML modelované jako <xref:System.IdentityModel.Tokens.SamlAttribute> objekty, které se dají naplnit přímo z <xref:System.IdentityModel.Claims.Claim> objektů, za předpokladu, že <xref:System.IdentityModel.Claims.Claim> objekt má <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> a <xref:System.IdentityModel.Claims.Claim.Resource%2A> vlastnost je typu <xref:System.String> . Příklad:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> Pokud jsou ve zprávách serializovány tokeny SAML, buď když jsou vydávány službou tokenu zabezpečení, nebo pokud je prezentují klienti ke službám v rámci ověřování, maximální kvóta velikosti zprávy musí být dostatečně velká, aby se vešlo na token SAML a ostatní části zprávy. V normálních případech jsou dostatečné výchozí kvóty velikosti zprávy. V případech, kdy je token SAML velký, protože obsahuje stovky deklarací identity, možná budete muset zvýšit kvótu tak, aby vyhovovala serializovanému tokenu. Další informace najdete v tématu věnovaném [bezpečnostním hlediskům pro data](security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Z SamlAttributes na deklarace identity  
 Pokud jsou ve zprávách obdrženy tokeny SAML, jednotlivé příkazy v tokenu SAML jsou přeměněny na <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objekty, které jsou umístěny do objektu <xref:System.IdentityModel.Policy.AuthorizationContext> . Deklarace z každého příkazu SAML jsou vráceny <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastností třídy <xref:System.IdentityModel.Policy.AuthorizationContext> a lze je prozkoumat, chcete-li určit, zda ověřit a autorizovat uživatele.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [metadata](federation.md)
- [Postupy: Vytvoření federovaného klienta](how-to-create-a-federated-client.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](how-to-configure-credentials-on-a-federation-service.md)
- [Správa deklarací a autorizace s modelem identity](managing-claims-and-authorization-with-the-identity-model.md)
- [Deklarace a tokeny](claims-and-tokens.md)
- [Vytvoření deklarace identity a hodnoty prostředků](claim-creation-and-resource-values.md)
- [Postupy: Vytvoření vlastní deklarace identity](../extending/how-to-create-a-custom-claim.md)
