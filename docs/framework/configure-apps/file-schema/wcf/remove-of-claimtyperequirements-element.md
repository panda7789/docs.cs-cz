---
title: '&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49009cb7e988c27ccc426e29c6ac973e553a0f73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="3761d-102">&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="3761d-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="3761d-103">Určuje typy deklarací identity k odebrání v federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="3761d-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="3761d-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3761d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3761d-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3761d-105">\<bindings></span></span>  
<span data-ttu-id="3761d-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="3761d-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="3761d-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="3761d-107">\<binding></span></span>  
<span data-ttu-id="3761d-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3761d-108">\<security></span></span>  
<span data-ttu-id="3761d-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="3761d-109">\<message></span></span>  
<span data-ttu-id="3761d-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3761d-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3761d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3761d-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3761d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3761d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3761d-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3761d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3761d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="3761d-114">Attributes</span></span>  
  
|<span data-ttu-id="3761d-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="3761d-115">Attribute</span></span>|<span data-ttu-id="3761d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3761d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3761d-117">Typ claimType</span><span class="sxs-lookup"><span data-stu-id="3761d-117">claimType</span></span>|<span data-ttu-id="3761d-118">Identifikátor URI, který definuje typ deklarace k odebrání.</span><span class="sxs-lookup"><span data-stu-id="3761d-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3761d-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3761d-119">Child Elements</span></span>  
 <span data-ttu-id="3761d-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="3761d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3761d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3761d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3761d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="3761d-122">Element</span></span>|<span data-ttu-id="3761d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="3761d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3761d-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3761d-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="3761d-125">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="3761d-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="3761d-126">Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="3761d-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="3761d-127">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="3761d-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3761d-128">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3761d-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3761d-129">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="3761d-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3761d-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3761d-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
