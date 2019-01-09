---
title: '&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7610a8e95996f15133ae58ec33c4afd9e2309cac
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146209"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="349a1-102">&lt;remove&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="349a1-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="349a1-103">Určuje typy deklarací, jenž budou odebrány z federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="349a1-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="349a1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="349a1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="349a1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="349a1-105">\<bindings></span></span>  
<span data-ttu-id="349a1-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="349a1-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="349a1-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="349a1-107">\<binding></span></span>  
<span data-ttu-id="349a1-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="349a1-108">\<security></span></span>  
<span data-ttu-id="349a1-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="349a1-109">\<message></span></span>  
<span data-ttu-id="349a1-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="349a1-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="349a1-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="349a1-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="349a1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="349a1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="349a1-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="349a1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="349a1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="349a1-114">Attributes</span></span>  
  
|<span data-ttu-id="349a1-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="349a1-115">Attribute</span></span>|<span data-ttu-id="349a1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="349a1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="349a1-117">Typ ClaimType</span><span class="sxs-lookup"><span data-stu-id="349a1-117">claimType</span></span>|<span data-ttu-id="349a1-118">Identifikátor URI, který definuje typ deklarace k odebrání.</span><span class="sxs-lookup"><span data-stu-id="349a1-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="349a1-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="349a1-119">Child Elements</span></span>  
 <span data-ttu-id="349a1-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="349a1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="349a1-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="349a1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="349a1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="349a1-122">Element</span></span>|<span data-ttu-id="349a1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="349a1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="349a1-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="349a1-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="349a1-125">Určuje kolekci požadovaných typů deklarací.</span><span class="sxs-lookup"><span data-stu-id="349a1-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="349a1-126">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="349a1-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="349a1-127">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="349a1-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="349a1-128">Například příchozí přihlašovací údaje musí mít sadu typů deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="349a1-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="349a1-129">Každý prvek v této kolekci Určuje typy požadovaných a volitelných deklarací, očekává se objeví federovaného pověření.</span><span class="sxs-lookup"><span data-stu-id="349a1-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="349a1-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="349a1-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
