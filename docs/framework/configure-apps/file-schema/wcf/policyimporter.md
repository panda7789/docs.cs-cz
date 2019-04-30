---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 81f38d2a163163ca7255ca546bbddbbb58fa3a1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783178"
---
# <a name="policyimporter"></a><span data-ttu-id="8efec-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="8efec-101">\<policyImporter></span></span>
<span data-ttu-id="8efec-102">Určuje programu pro import zásady, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="8efec-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="8efec-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8efec-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8efec-104">\<client></span><span class="sxs-lookup"><span data-stu-id="8efec-104">\<client></span></span>  
<span data-ttu-id="8efec-105">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="8efec-105">\<metadata></span></span>  
<span data-ttu-id="8efec-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="8efec-106">\<policyImporters></span></span>  
<span data-ttu-id="8efec-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="8efec-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8efec-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8efec-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8efec-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8efec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8efec-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8efec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8efec-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8efec-111">Attributes</span></span>  
  
|<span data-ttu-id="8efec-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="8efec-112">Attribute</span></span>|<span data-ttu-id="8efec-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8efec-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8efec-114">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="8efec-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8efec-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8efec-115">Child Elements</span></span>  
 <span data-ttu-id="8efec-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="8efec-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8efec-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8efec-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8efec-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="8efec-118">Element</span></span>|<span data-ttu-id="8efec-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8efec-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8efec-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="8efec-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="8efec-121">Určuje všechny nástroje pro import, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="8efec-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8efec-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8efec-122">Remarks</span></span>  
 <span data-ttu-id="8efec-123">Import zásady se používá k hledání kontrolních výrazů vlastních zásad o vazbách funkce, jakož i připojit vlastní prvek vazby, který implementuje funkce, které vyžaduje kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="8efec-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efec-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8efec-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="8efec-125">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="8efec-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="8efec-126">Klienti</span><span class="sxs-lookup"><span data-stu-id="8efec-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
