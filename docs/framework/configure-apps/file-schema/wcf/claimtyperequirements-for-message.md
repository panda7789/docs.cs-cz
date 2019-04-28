---
title: <claimTypeRequirements> pro <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: db6717022bf3af0c4922818668595dd3937e9c71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704404"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="1846a-102">\<claimTypeRequirements > pro \<zpráva ></span><span class="sxs-lookup"><span data-stu-id="1846a-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="1846a-103">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="1846a-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="1846a-104">Kolekce slouží ve službě k určení požadovaných a volitelných deklarací, které musí být v vydaný token, který klient používá pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="1846a-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="1846a-105">Služba zveřejňuje typy požadovaná deklarace identity v metadatech, pokud je povoleno publikování WSDL, ale WCF nevyžaduje, aby vydaný token obsahují typy, které žádost.</span><span class="sxs-lookup"><span data-stu-id="1846a-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="1846a-106">Služby, které chtějí vynutit požadovaná deklarace identity, že typy jsou k dispozici by měl provést pomocí zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="1846a-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="1846a-107">U federovaných klientů Tato kolekce obsahuje seznam povinných a volitelných deklarací identity, která se posílají ve službě security token v požadavku klienta pro vydaný token.</span><span class="sxs-lookup"><span data-stu-id="1846a-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1846a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1846a-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
