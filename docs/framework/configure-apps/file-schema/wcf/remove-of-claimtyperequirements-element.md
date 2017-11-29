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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 96155ed805d99a3678c5d20d83a490efb9811815
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="d238c-102">&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="d238c-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="d238c-103">Určuje typy deklarací identity k odebrání v federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d238c-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d238c-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d238c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d238c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d238c-105">\<bindings></span></span>  
<span data-ttu-id="d238c-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="d238c-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d238c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="d238c-107">\<binding></span></span>  
<span data-ttu-id="d238c-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="d238c-108">\<security></span></span>  
<span data-ttu-id="d238c-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="d238c-109">\<message></span></span>  
<span data-ttu-id="d238c-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d238c-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d238c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d238c-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d238c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d238c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d238c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d238c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d238c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d238c-114">Attributes</span></span>  
  
|<span data-ttu-id="d238c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d238c-115">Attribute</span></span>|<span data-ttu-id="d238c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d238c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d238c-117">Typ claimType</span><span class="sxs-lookup"><span data-stu-id="d238c-117">claimType</span></span>|<span data-ttu-id="d238c-118">Identifikátor URI, který definuje typ deklarace k odebrání.</span><span class="sxs-lookup"><span data-stu-id="d238c-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d238c-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d238c-119">Child Elements</span></span>  
 <span data-ttu-id="d238c-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d238c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d238c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d238c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d238c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d238c-122">Element</span></span>|<span data-ttu-id="d238c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d238c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d238c-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d238c-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="d238c-125">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d238c-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d238c-126">Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d238c-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d238c-127">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d238c-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d238c-128">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d238c-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d238c-129">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d238c-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d238c-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d238c-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
