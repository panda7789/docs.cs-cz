---
title: <clear><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: e7e3bebd85decbaa4d216743f9bea9e135b87995
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926138"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="c9826-102">\<Vymazat > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="c9826-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="c9826-103">Určuje, že všechny typy deklarací, které mají být odebrány v rámci federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="c9826-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="c9826-104">Tím se zajistí, že kolekce začne být prázdná.</span><span class="sxs-lookup"><span data-stu-id="c9826-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="c9826-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9826-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9826-106">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="c9826-106">\<bindings></span></span>  
<span data-ttu-id="c9826-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="c9826-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="c9826-108">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c9826-108">\<binding></span></span>  
<span data-ttu-id="c9826-109">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c9826-109">\<security></span></span>  
<span data-ttu-id="c9826-110">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="c9826-110">\<message></span></span>  
<span data-ttu-id="c9826-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="c9826-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9826-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9826-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9826-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9826-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c9826-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9826-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9826-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9826-115">Attributes</span></span>  
 <span data-ttu-id="c9826-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9826-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c9826-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c9826-117">Child Elements</span></span>  
 <span data-ttu-id="c9826-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9826-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9826-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c9826-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c9826-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9826-120">Element</span></span>|<span data-ttu-id="c9826-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c9826-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9826-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="c9826-122">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="c9826-123">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="c9826-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="c9826-124">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="c9826-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="c9826-125">Ve federovaném scénáři služby stavují požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="c9826-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="c9826-126">Například příchozí přihlašovací údaje musí mít určitou sadu typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="c9826-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="c9826-127">Každý prvek v této kolekci určuje typy požadovaných a volitelných deklarací, které mají být zobrazeny ve federovaném pověření.</span><span class="sxs-lookup"><span data-stu-id="c9826-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9826-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9826-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
