---
title: <remove><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7238c253bfbc3224c8bbd31265e197dd35e56514
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934229"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="d757c-102">\<odebrat > \<elementu > claimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="d757c-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="d757c-103">Určuje typy deklarací, které mají být odebrány v rámci federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="d757c-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d757c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d757c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d757c-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="d757c-105">\<bindings></span></span>  
<span data-ttu-id="d757c-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d757c-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d757c-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="d757c-107">\<binding></span></span>  
<span data-ttu-id="d757c-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d757c-108">\<security></span></span>  
<span data-ttu-id="d757c-109">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="d757c-109">\<message></span></span>  
<span data-ttu-id="d757c-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d757c-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d757c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d757c-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d757c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d757c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d757c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d757c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d757c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d757c-114">Attributes</span></span>  
  
|<span data-ttu-id="d757c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d757c-115">Attribute</span></span>|<span data-ttu-id="d757c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d757c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d757c-117">claimType</span><span class="sxs-lookup"><span data-stu-id="d757c-117">claimType</span></span>|<span data-ttu-id="d757c-118">Identifikátor URI definující typ deklarace, který má být odebrán.</span><span class="sxs-lookup"><span data-stu-id="d757c-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d757c-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d757c-119">Child Elements</span></span>  
 <span data-ttu-id="d757c-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d757c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d757c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d757c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d757c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d757c-122">Element</span></span>|<span data-ttu-id="d757c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d757c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d757c-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d757c-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="d757c-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d757c-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d757c-126">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d757c-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d757c-127">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d757c-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d757c-128">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d757c-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d757c-129">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="d757c-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d757c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d757c-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
