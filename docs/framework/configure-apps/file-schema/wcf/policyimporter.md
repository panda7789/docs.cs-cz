---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4075f7fcb1c65da3d9e2e5e5dab52452ca2c9b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632163"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="9e212-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="9e212-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="9e212-103">Určuje programu pro import zásady, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="9e212-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="9e212-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9e212-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e212-105">\<client></span><span class="sxs-lookup"><span data-stu-id="9e212-105">\<client></span></span>  
<span data-ttu-id="9e212-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="9e212-106">\<metadata></span></span>  
<span data-ttu-id="9e212-107">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="9e212-107">\<policyImporters></span></span>  
<span data-ttu-id="9e212-108">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="9e212-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e212-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e212-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e212-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9e212-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9e212-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9e212-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e212-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9e212-112">Attributes</span></span>  
  
|<span data-ttu-id="9e212-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="9e212-113">Attribute</span></span>|<span data-ttu-id="9e212-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9e212-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9e212-115">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="9e212-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e212-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9e212-116">Child Elements</span></span>  
 <span data-ttu-id="9e212-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="9e212-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e212-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9e212-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9e212-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="9e212-119">Element</span></span>|<span data-ttu-id="9e212-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9e212-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e212-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="9e212-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="9e212-122">Určuje všechny nástroje pro import, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="9e212-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e212-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e212-123">Remarks</span></span>  
 <span data-ttu-id="9e212-124">Import zásady se používá k hledání kontrolních výrazů vlastních zásad o vazbách funkce, jakož i připojit vlastní prvek vazby, který implementuje funkce, které vyžaduje kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="9e212-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e212-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e212-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="9e212-126">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="9e212-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9e212-127">Klienti</span><span class="sxs-lookup"><span data-stu-id="9e212-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
