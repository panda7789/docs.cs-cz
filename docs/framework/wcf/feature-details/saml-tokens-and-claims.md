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
ms.openlocfilehash: 7037daf299d7c750ab398c21c1d7ccb541620701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943078"
---
# <a name="saml-tokens-and-claims"></a>Tokeny a deklarace SAML
Tokeny SAML (Security Assert Markup Language ) představují reprezentace deklarací XML. Ve výchozím nastavení používají tokeny SAML Windows Communication Foundation (WCF) ve federovaném scénářizabezpečení tokeny.  
  
 Tokeny SAML přenášejí příkazy, které jsou sady deklarací, které provedla jedna entita o jiné entitě. Například ve scénářích federovaného zabezpečení jsou příkazy provedeny službou tokenu zabezpečení o uživateli v systému. Služba tokenů zabezpečení podepíše token SAML, aby označovala pravdivost příkazů obsažených v tokenu. Token SAML je navíc spojen s materiálem kryptografického klíče, který uživatel tokenu SAML prokáže jako znalosti. Tento důkaz splňuje předávající stranu, kterou token SAML ve skutečnosti vystavil tomuto uživateli. Například v typickém scénáři:  
  
1. Klient požádá o token SAML ze služby tokenu zabezpečení a ověří tuto službu tokenu zabezpečení pomocí pověření systému Windows.  
  
2. Služba tokenů zabezpečení vydá klientovi token SAML. Token SAML je podepsaný certifikátem přidruženým ke službě tokenu zabezpečení a obsahuje ověřovací klíč zašifrovaný pro cílovou službu.  
  
3. Klient také obdrží kopii *ověřovacího klíče*. Klient pak předloží token SAML Aplikační službě ( *předávající straně*) a podepíše zprávu pomocí tohoto klíčového kontrolního klíče.  
  
4. Podpis přes token SAML informuje předávající stranu, že se token vystavil službou tokenu zabezpečení. Podpis zprávy vytvořený pomocí klíče důkazu oznamuje předávající straně, že byl token vydán klientovi.  
  
## <a name="from-claims-to-samlattributes"></a>Z deklarací identity na SamlAttributes  
 V rámci WCF jsou příkazy v tokenech SAML modelované <xref:System.IdentityModel.Tokens.SamlAttribute> jako objekty, které se dají naplnit <xref:System.IdentityModel.Claims.Claim> přímo z objektů. <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.Right%2A> za předpokladu, že <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> objekt má <xref:System.IdentityModel.Claims.Claim.Resource%2A> vlastnost a vlastnost je Zadejte <xref:System.String>. Příklad:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> Pokud jsou ve zprávách serializovány tokeny SAML, buď když jsou vydávány pomocí služby tokenu zabezpečení, nebo pokud je prezentují klienti ke službám v rámci ověřování, maximální kvóta velikosti zprávy musí být dostatečně velká, aby se mohla pojmout token SAML. ostatní části zprávy V normálních případech jsou dostatečné výchozí kvóty velikosti zprávy. V případech, kdy je token SAML velký, protože obsahuje stovky deklarací identity, možná budete muset zvýšit kvótu tak, aby vyhovovala serializovanému tokenu. Další informace najdete v tématu věnovaném [bezpečnostním hlediskům pro data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Z SamlAttributes na deklarace identity  
 Pokud jsou ve zprávách obdrženy tokeny SAML, jednotlivé příkazy v tokenu SAML jsou přeměněny <xref:System.IdentityModel.Policy.IAuthorizationPolicy> na objekty, které jsou umístěny <xref:System.IdentityModel.Policy.AuthorizationContext>do objektu. Deklarace z každého příkazu SAML jsou vráceny <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastností <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a lze je prozkoumat, chcete-li určit, zda ověřit a autorizovat uživatele.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federace](../../../../docs/framework/wcf/feature-details/federation.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Deklarace identity a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Vytvoření deklarace identity a hodnoty prostředků](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Postupy: Vytvoření vlastní deklarace identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
