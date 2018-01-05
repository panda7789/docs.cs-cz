---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2226b4f55025c9dec3fdeb4f9b4f51016ffd3e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="a8338-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="a8338-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="a8338-103">Určuje program pro import zásady, kterými se řídí import kontrolních výrazů vlastních zásad o vazby.</span><span class="sxs-lookup"><span data-stu-id="a8338-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="a8338-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a8338-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8338-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="a8338-105">\<client></span></span>  
<span data-ttu-id="a8338-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="a8338-106">\<metadata></span></span>  
<span data-ttu-id="a8338-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="a8338-107">\<policyImporters></span></span>  
<span data-ttu-id="a8338-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="a8338-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8338-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8338-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8338-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a8338-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a8338-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a8338-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8338-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8338-112">Attributes</span></span>  
  
|<span data-ttu-id="a8338-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a8338-113">Attribute</span></span>|<span data-ttu-id="a8338-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a8338-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a8338-115">Typ tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="a8338-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8338-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a8338-116">Child Elements</span></span>  
 <span data-ttu-id="a8338-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8338-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8338-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a8338-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a8338-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8338-119">Element</span></span>|<span data-ttu-id="a8338-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a8338-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8338-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="a8338-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="a8338-122">Určuje všechny společnosti importers zásady, které řídí import kontrolních výrazů vlastních zásad o vazby.</span><span class="sxs-lookup"><span data-stu-id="a8338-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8338-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8338-123">Remarks</span></span>  
 <span data-ttu-id="a8338-124">– Importér zásad se používá k hledání kontrolních výrazů vlastních zásad o vazbu funkce, jakož i připojit vlastní vazby element, který implementuje funkce, které vyžaduje kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="a8338-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8338-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8338-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="a8338-126">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="a8338-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="a8338-127">Klienti</span><span class="sxs-lookup"><span data-stu-id="a8338-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
