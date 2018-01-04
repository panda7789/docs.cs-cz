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
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="7d24c-102">Tokeny a deklarace SAML</span><span class="sxs-lookup"><span data-stu-id="7d24c-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="7d24c-103">Zabezpečení kontrolní výrazy Markup Language (SAML) *tokeny* jsou reprezentace XML deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="7d24c-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="7d24c-104">Ve výchozím nastavení, tokeny SAML [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] se používá ve scénářích federované zabezpečení *vystavené tokeny*.</span><span class="sxs-lookup"><span data-stu-id="7d24c-104">By default, SAML tokens [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="7d24c-105">Tokeny SAML provádění příkazů, které jsou sady deklarací identity provedené jednu entitu o jinou entitou.</span><span class="sxs-lookup"><span data-stu-id="7d24c-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="7d24c-106">Například ve scénářích federované zabezpečení příkazy jsou vytvářeny pomocí služby tokenů zabezpečení o uživateli v systému.</span><span class="sxs-lookup"><span data-stu-id="7d24c-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="7d24c-107">Služby tokenů zabezpečení podepisuje tokeny SAML udávajících pravdivosti příkazy obsažených v tokenu.</span><span class="sxs-lookup"><span data-stu-id="7d24c-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="7d24c-108">Kromě toho je přidružen kryptografických materiál klíče, který uživatel tokenu SAML prokáže znalosti o tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="7d24c-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="7d24c-109">Toto ověření splňuje, že předávající stranu, která byla tokenu SAML, ve skutečnosti vydán pro tohoto uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d24c-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="7d24c-110">Například v Typický scénář:</span><span class="sxs-lookup"><span data-stu-id="7d24c-110">For example, in a typical scenario:</span></span>  
  
1.  <span data-ttu-id="7d24c-111">Klient požaduje tokenu SAML od služby tokenů zabezpečení, ověřování do této služby tokenů zabezpečení pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7d24c-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="7d24c-112">Služby tokenů zabezpečení vydá SAML token klientovi.</span><span class="sxs-lookup"><span data-stu-id="7d24c-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="7d24c-113">SAML token je podepsaný certifikátem přidružené služby tokenů zabezpečení a obsahuje doklad klíč šifrována pro cílovou službu.</span><span class="sxs-lookup"><span data-stu-id="7d24c-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3.  <span data-ttu-id="7d24c-114">Klient také obdrží kopii *doklad klíč*.</span><span class="sxs-lookup"><span data-stu-id="7d24c-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="7d24c-115">Klient pak uvede token SAML, který má služba aplikace ( *předávající strany*) a podepíše zprávu s tímto doklad klíčem.</span><span class="sxs-lookup"><span data-stu-id="7d24c-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4.  <span data-ttu-id="7d24c-116">Podpis přes tokenu SAML poskytuje předávající strany, aby vystavovala služby tokenů zabezpečení token.</span><span class="sxs-lookup"><span data-stu-id="7d24c-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="7d24c-117">Podpis zprávy, které jsou vytvořené pomocí doklad klíč informuje předávající strany, zda byl token vydán klientovi.</span><span class="sxs-lookup"><span data-stu-id="7d24c-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="7d24c-118">Z deklarací identity k SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="7d24c-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="7d24c-119">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], příkazy v tokenech SAML jsou modelovat jako <xref:System.IdentityModel.Tokens.SamlAttribute> objekty, které je možné importovat přímo z <xref:System.IdentityModel.Claims.Claim> objekty, zadaný <xref:System.IdentityModel.Claims.Claim> objekt má <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> a <xref:System.IdentityModel.Claims.Claim.Resource%2A> Vlastnost je typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7d24c-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="7d24c-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7d24c-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  <span data-ttu-id="7d24c-121">Při tokeny SAML se serializují ve zprávách, při vydávání pomocí služby tokenů zabezpečení nebo poté, co se zobrazí klienty pro služby v rámci ověřování, kvóta maximální velikosti zprávy musí být dostatečně velký pro uložení tokenu SAML a ostatní části zprávy.</span><span class="sxs-lookup"><span data-stu-id="7d24c-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="7d24c-122">V případech, normální výchozích kvót velikost zprávy je dostatečné.</span><span class="sxs-lookup"><span data-stu-id="7d24c-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="7d24c-123">V případech, kdy je SAML token velké vzhledem k tomu, že obsahuje stovky deklarace identity, můžete však zvýšit kvóty pro přizpůsobení serializovaný token.</span><span class="sxs-lookup"><span data-stu-id="7d24c-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7d24c-124">[Důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="7d24c-124"> [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="7d24c-125">Z SamlAttributes do deklarací identity</span><span class="sxs-lookup"><span data-stu-id="7d24c-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="7d24c-126">Když ve zprávách přijme tokeny SAML, jsou různé příkazy v tokenu SAML převedena na <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objekty, které se umístí do <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="7d24c-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="7d24c-127">Deklarace identity z každý příkaz SAML se vrátí pomocí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> a můžete prověřit, abyste zjistili, jestli se k ověřování a autorizaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d24c-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d24c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d24c-128">See Also</span></span>  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="7d24c-129">Federace</span><span class="sxs-lookup"><span data-stu-id="7d24c-129">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="7d24c-130">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="7d24c-130">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="7d24c-131">Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="7d24c-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="7d24c-132">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="7d24c-132">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="7d24c-133">Deklarace identity a tokeny</span><span class="sxs-lookup"><span data-stu-id="7d24c-133">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [<span data-ttu-id="7d24c-134">Vytvoření deklarace identity a hodnoty prostředků</span><span class="sxs-lookup"><span data-stu-id="7d24c-134">Claim Creation and Resource Values</span></span>](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [<span data-ttu-id="7d24c-135">Postupy: Vytvoření vlastní deklarace identity</span><span class="sxs-lookup"><span data-stu-id="7d24c-135">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
