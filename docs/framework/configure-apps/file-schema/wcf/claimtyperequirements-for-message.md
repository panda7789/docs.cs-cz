---
title: '&lt;claimTypeRequirements&gt; pro &lt;message&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 158aad6a6a11bb889df74e1222a8881a1c38803f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="fb6f1-102">&lt;claimTypeRequirements&gt; pro &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="fb6f1-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="fb6f1-103">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="fb6f1-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="fb6f1-104">Kolekce se používá služba zadat všechny požadované a volitelné deklarace, které musí být v vydaných tokenu, které klient používá k přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="fb6f1-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="fb6f1-105">Službu zpřístupní typy požadované deklarací identity v metadatech, pokud je povoleno publikování WSDL ale WCF nevyžaduje vydaný token obsahovat typy zadaný deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="fb6f1-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="fb6f1-106">Služby, které chtějí vynutit požadované deklarace identity, zda jsou k dispozici typy by to pomocí zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="fb6f1-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="fb6f1-107">U federovaných klientů Tato kolekce obsahuje seznam požadované a volitelné deklarací identity, která se posílají služby tokenů zabezpečení v požadavku klienta u vydaných tokenu.</span><span class="sxs-lookup"><span data-stu-id="fb6f1-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6f1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb6f1-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
