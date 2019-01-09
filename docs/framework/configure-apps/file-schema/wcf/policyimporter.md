---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 22d90ff9d0cd5325300cf42437836f075cbf8c31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148484"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="7ad36-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="7ad36-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="7ad36-103">Určuje programu pro import zásady, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="7ad36-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="7ad36-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7ad36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ad36-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="7ad36-105">\<client></span></span>  
<span data-ttu-id="7ad36-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="7ad36-106">\<metadata></span></span>  
<span data-ttu-id="7ad36-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="7ad36-107">\<policyImporters></span></span>  
<span data-ttu-id="7ad36-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="7ad36-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ad36-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ad36-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ad36-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7ad36-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7ad36-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7ad36-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ad36-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7ad36-112">Attributes</span></span>  
  
|<span data-ttu-id="7ad36-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7ad36-113">Attribute</span></span>|<span data-ttu-id="7ad36-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7ad36-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="7ad36-115">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="7ad36-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ad36-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ad36-116">Child Elements</span></span>  
 <span data-ttu-id="7ad36-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="7ad36-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ad36-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7ad36-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7ad36-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="7ad36-119">Element</span></span>|<span data-ttu-id="7ad36-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7ad36-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ad36-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="7ad36-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="7ad36-122">Určuje všechny nástroje pro import, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="7ad36-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ad36-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ad36-123">Remarks</span></span>  
 <span data-ttu-id="7ad36-124">Import zásady se používá k hledání kontrolních výrazů vlastních zásad o vazbách funkce, jakož i připojit vlastní prvek vazby, který implementuje funkce, které vyžaduje kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="7ad36-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad36-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ad36-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="7ad36-126">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="7ad36-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="7ad36-127">Klienti</span><span class="sxs-lookup"><span data-stu-id="7ad36-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
