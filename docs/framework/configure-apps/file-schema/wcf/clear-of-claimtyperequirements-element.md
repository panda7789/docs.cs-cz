---
title: '&lt;clear&gt; elementu &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: ca8ea91f5806a6cedc98729de1c45ab6b5de6afb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747122"
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="d6125-102">&lt;clear&gt; elementu &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="d6125-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="d6125-103">Určuje, že všechny deklarace identity typy odeberou ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d6125-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="d6125-104">Tím se zajistí, že kolekce začne prázdný.</span><span class="sxs-lookup"><span data-stu-id="d6125-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="d6125-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6125-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6125-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d6125-106">\<bindings></span></span>  
<span data-ttu-id="d6125-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="d6125-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d6125-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="d6125-108">\<binding></span></span>  
<span data-ttu-id="d6125-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="d6125-109">\<security></span></span>  
<span data-ttu-id="d6125-110">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="d6125-110">\<message></span></span>  
<span data-ttu-id="d6125-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d6125-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6125-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6125-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6125-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6125-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d6125-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6125-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6125-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6125-115">Attributes</span></span>  
 <span data-ttu-id="d6125-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6125-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6125-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6125-117">Child Elements</span></span>  
 <span data-ttu-id="d6125-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6125-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6125-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6125-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d6125-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6125-120">Element</span></span>|<span data-ttu-id="d6125-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d6125-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6125-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="d6125-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="d6125-123">Určuje kolekci typů požadované deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d6125-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d6125-124">Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d6125-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d6125-125">V případě federovaných stavu služby požadavky na příchozí přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d6125-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d6125-126">Například příchozí pověření musí mít sadu typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d6125-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d6125-127">Každý prvek v této kolekci Určuje typy deklarací identity požadované a volitelné očekávání měla objevit ve federované přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d6125-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6125-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6125-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
