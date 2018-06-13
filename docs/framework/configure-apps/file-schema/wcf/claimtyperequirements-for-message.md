---
title: '&lt;claimTypeRequirements&gt; pro &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: f4460311f5478f441b819bc8a48540d6feea69b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754542"
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="1fb98-102">&lt;claimTypeRequirements&gt; pro &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="1fb98-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="1fb98-103">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="1fb98-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="1fb98-104">Kolekce se používá služba zadat všechny požadované a volitelné deklarace, které musí být v vydaných tokenu, které klient používá k přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="1fb98-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="1fb98-105">Službu zpřístupní typy požadované deklarací identity v metadatech, pokud je povoleno publikování WSDL ale WCF nevyžaduje vydaný token obsahovat typy zadaný deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="1fb98-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="1fb98-106">Služby, které chtějí vynutit požadované deklarace identity, zda jsou k dispozici typy by to pomocí zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="1fb98-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="1fb98-107">U federovaných klientů Tato kolekce obsahuje seznam požadované a volitelné deklarací identity, která se posílají služby tokenů zabezpečení v požadavku klienta u vydaných tokenu.</span><span class="sxs-lookup"><span data-stu-id="1fb98-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb98-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fb98-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
