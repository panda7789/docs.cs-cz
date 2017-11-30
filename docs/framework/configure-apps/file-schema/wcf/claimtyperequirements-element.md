---
title: Element &lt;claimTypeRequirements&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0146250c12c9c12e1f204c467a9a454b90e9f47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="d1b70-102">Element &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="d1b70-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="d1b70-103">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d1b70-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="d1b70-104">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d1b70-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d1b70-105">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d1b70-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d1b70-106">Každý podřízený element v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d1b70-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="d1b70-107">Požadavek typ deklarace identity se skládá z identifikátoru URI požadovaného typu deklarace identity v vydaných tokenu společně s určující, zda deklarací identity v vydaný token je vyžadován typ nebo je volitelný parametr typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="d1b70-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b70-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1b70-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="d1b70-109">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d1b70-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d1b70-110">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d1b70-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d1b70-111">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d1b70-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="d1b70-112">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d1b70-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d1b70-113">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="d1b70-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 [<span data-ttu-id="d1b70-114">Vazby</span><span class="sxs-lookup"><span data-stu-id="d1b70-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d1b70-115">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="d1b70-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d1b70-116">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d1b70-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d1b70-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d1b70-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="d1b70-118">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1b70-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="d1b70-119">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d1b70-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
