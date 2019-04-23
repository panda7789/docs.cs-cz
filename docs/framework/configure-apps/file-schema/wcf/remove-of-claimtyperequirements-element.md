---
title: <remove> z <claimTypeRequirements> – element
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 9ab1162ff5d86b8a9d43dae79ebf9c9321119206
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119701"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="d321c-102">\<Odebrat > z \<claimTypeRequirements > – element</span><span class="sxs-lookup"><span data-stu-id="d321c-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="d321c-103">Určuje typy deklarací, jenž budou odebrány z federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="d321c-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d321c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d321c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d321c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d321c-105">\<bindings></span></span>  
<span data-ttu-id="d321c-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d321c-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d321c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d321c-107">\<binding></span></span>  
<span data-ttu-id="d321c-108">\<security></span><span class="sxs-lookup"><span data-stu-id="d321c-108">\<security></span></span>  
<span data-ttu-id="d321c-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="d321c-109">\<message></span></span>  
<span data-ttu-id="d321c-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d321c-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d321c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d321c-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d321c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d321c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d321c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d321c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d321c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d321c-114">Attributes</span></span>  
  
|<span data-ttu-id="d321c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d321c-115">Attribute</span></span>|<span data-ttu-id="d321c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d321c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d321c-117">claimType</span><span class="sxs-lookup"><span data-stu-id="d321c-117">claimType</span></span>|<span data-ttu-id="d321c-118">Identifikátor URI, který definuje typ deklarace k odebrání.</span><span class="sxs-lookup"><span data-stu-id="d321c-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d321c-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d321c-119">Child Elements</span></span>  
 <span data-ttu-id="d321c-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d321c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d321c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d321c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d321c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d321c-122">Element</span></span>|<span data-ttu-id="d321c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d321c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d321c-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d321c-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="d321c-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="d321c-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d321c-126">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d321c-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d321c-127">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d321c-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d321c-128">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d321c-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d321c-129">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="d321c-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d321c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d321c-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
