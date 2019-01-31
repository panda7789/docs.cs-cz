---
title: <remove> z <claimTypeRequirements> – element
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 8058a90d61d8f94944d98a26c59bfbe225f611d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259496"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="39587-102">\<Odebrat > z \<claimTypeRequirements > – element</span><span class="sxs-lookup"><span data-stu-id="39587-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="39587-103">Určuje typy deklarací, jenž budou odebrány z federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="39587-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="39587-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39587-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39587-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="39587-105">\<bindings></span></span>  
<span data-ttu-id="39587-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="39587-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="39587-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="39587-107">\<binding></span></span>  
<span data-ttu-id="39587-108">\<security></span><span class="sxs-lookup"><span data-stu-id="39587-108">\<security></span></span>  
<span data-ttu-id="39587-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="39587-109">\<message></span></span>  
<span data-ttu-id="39587-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="39587-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39587-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39587-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39587-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39587-112">Attributes and Elements</span></span>  
 <span data-ttu-id="39587-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39587-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39587-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="39587-114">Attributes</span></span>  
  
|<span data-ttu-id="39587-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="39587-115">Attribute</span></span>|<span data-ttu-id="39587-116">Popis</span><span class="sxs-lookup"><span data-stu-id="39587-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39587-117">claimType</span><span class="sxs-lookup"><span data-stu-id="39587-117">claimType</span></span>|<span data-ttu-id="39587-118">Identifikátor URI, který definuje typ deklarace k odebrání.</span><span class="sxs-lookup"><span data-stu-id="39587-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39587-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39587-119">Child Elements</span></span>  
 <span data-ttu-id="39587-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="39587-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39587-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39587-121">Parent Elements</span></span>  
  
|<span data-ttu-id="39587-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="39587-122">Element</span></span>|<span data-ttu-id="39587-123">Popis</span><span class="sxs-lookup"><span data-stu-id="39587-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39587-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="39587-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="39587-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="39587-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="39587-126">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="39587-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="39587-127">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="39587-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="39587-128">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="39587-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="39587-129">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="39587-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39587-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39587-130">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
