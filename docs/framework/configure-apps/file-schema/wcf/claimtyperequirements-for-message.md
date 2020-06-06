---
title: <claimTypeRequirements>for<message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: db6717022bf3af0c4922818668595dd3937e9c71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704404"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="00db9-102">\<claimTypeRequirements>for\<message></span><span class="sxs-lookup"><span data-stu-id="00db9-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="00db9-103">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="00db9-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="00db9-104">Služba tuto kolekci používá k určení požadovaných a volitelných deklarací identity, které musí být v vystaveném tokenu, který klient používá pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="00db9-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="00db9-105">Služba zveřejňuje požadované typy deklarací identity v metadatech, pokud je povoleno publikování WSDL, ale WCF nevyžaduje, aby vydaný token obsahoval zadané typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="00db9-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="00db9-106">K dispozici jsou služby, které chtějí vymáhat požadované typy deklarací identity, a to pomocí zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="00db9-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="00db9-107">V federovaných klientech obsahuje tato kolekce seznam požadovaných a volitelných deklarací identity, které se odesílají do služby tokenu zabezpečení v žádosti klienta o vydaný token.</span><span class="sxs-lookup"><span data-stu-id="00db9-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00db9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="00db9-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
