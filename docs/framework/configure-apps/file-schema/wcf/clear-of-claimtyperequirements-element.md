---
title: <clear> z <claimTypeRequirements> – element
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 35d0391951204bd352918d3004f0cc4f9480b0e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090316"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="59334-102">\<Vymazat > z \<claimTypeRequirements > – element</span><span class="sxs-lookup"><span data-stu-id="59334-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="59334-103">Určuje, že všechny typy deklarací, jenž budou odebrány z federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="59334-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="59334-104">Tím se zajistí, že začne prázdnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="59334-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="59334-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59334-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="59334-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="59334-106">\<bindings></span></span>  
<span data-ttu-id="59334-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="59334-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="59334-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="59334-108">\<binding></span></span>  
<span data-ttu-id="59334-109">\<security></span><span class="sxs-lookup"><span data-stu-id="59334-109">\<security></span></span>  
<span data-ttu-id="59334-110">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="59334-110">\<message></span></span>  
<span data-ttu-id="59334-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="59334-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59334-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59334-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59334-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59334-113">Attributes and Elements</span></span>  
 <span data-ttu-id="59334-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59334-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59334-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="59334-115">Attributes</span></span>  
 <span data-ttu-id="59334-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="59334-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59334-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59334-117">Child Elements</span></span>  
 <span data-ttu-id="59334-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="59334-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59334-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59334-119">Parent Elements</span></span>  
  
|<span data-ttu-id="59334-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="59334-120">Element</span></span>|<span data-ttu-id="59334-121">Popis</span><span class="sxs-lookup"><span data-stu-id="59334-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59334-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="59334-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="59334-123">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="59334-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="59334-124">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="59334-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="59334-125">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="59334-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="59334-126">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="59334-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="59334-127">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="59334-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59334-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59334-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
