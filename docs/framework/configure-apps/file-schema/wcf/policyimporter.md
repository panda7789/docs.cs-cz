---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 273bd0d5e68a661c639b82264b440b83d8127427
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933794"
---
# <a name="policyimporter"></a><span data-ttu-id="1a288-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="1a288-101">\<policyImporter></span></span>
<span data-ttu-id="1a288-102">Určuje dovozce zásad, který řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="1a288-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="1a288-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1a288-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a288-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="1a288-104">\<client></span></span>  
<span data-ttu-id="1a288-105">\<> metadat</span><span class="sxs-lookup"><span data-stu-id="1a288-105">\<metadata></span></span>  
<span data-ttu-id="1a288-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="1a288-106">\<policyImporters></span></span>  
<span data-ttu-id="1a288-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="1a288-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a288-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a288-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a288-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1a288-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a288-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1a288-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a288-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1a288-111">Attributes</span></span>  
  
|<span data-ttu-id="1a288-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1a288-112">Attribute</span></span>|<span data-ttu-id="1a288-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1a288-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="1a288-114">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="1a288-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a288-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1a288-115">Child Elements</span></span>  
 <span data-ttu-id="1a288-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="1a288-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a288-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1a288-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1a288-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a288-118">Element</span></span>|<span data-ttu-id="1a288-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1a288-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a288-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="1a288-120">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="1a288-121">Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="1a288-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a288-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a288-122">Remarks</span></span>  
 <span data-ttu-id="1a288-123">Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.</span><span class="sxs-lookup"><span data-stu-id="1a288-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a288-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a288-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="1a288-125">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="1a288-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="1a288-126">Klienti</span><span class="sxs-lookup"><span data-stu-id="1a288-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
