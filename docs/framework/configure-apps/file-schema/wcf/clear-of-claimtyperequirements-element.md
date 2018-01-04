---
title: '&lt;clear&gt; elementu &lt;claimTypeRequirements&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71cc4516362691484408ae2f81dfee462bd560d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="6f7f0-102">&lt;clear&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="6f7f0-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="6f7f0-103">Určuje, že všechny deklarace identity typy odeberou ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="6f7f0-104">Tím se zajistí, že kolekce začne prázdný.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="6f7f0-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f7f0-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-106">\<bindings></span></span>  
<span data-ttu-id="6f7f0-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="6f7f0-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-108">\<binding></span></span>  
<span data-ttu-id="6f7f0-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-109">\<security></span></span>  
<span data-ttu-id="6f7f0-110">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-110">\<message></span></span>  
<span data-ttu-id="6f7f0-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7f0-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f7f0-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f7f0-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6f7f0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6f7f0-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f7f0-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="6f7f0-115">Attributes</span></span>  
 <span data-ttu-id="6f7f0-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="6f7f0-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f7f0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6f7f0-117">Child Elements</span></span>  
 <span data-ttu-id="6f7f0-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="6f7f0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f7f0-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6f7f0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6f7f0-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="6f7f0-120">Element</span></span>|<span data-ttu-id="6f7f0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6f7f0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f7f0-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="6f7f0-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="6f7f0-123">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="6f7f0-124">Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="6f7f0-125">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="6f7f0-126">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="6f7f0-127">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="6f7f0-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f7f0-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f7f0-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
