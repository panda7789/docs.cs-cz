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
ms.openlocfilehash: b56c431c0e8dbab7bd4680a6e692d9b4f6e0eec4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="9107d-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="9107d-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="9107d-103">Určuje program pro import zásady, kterými se řídí import kontrolních výrazů vlastních zásad o vazby.</span><span class="sxs-lookup"><span data-stu-id="9107d-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="9107d-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9107d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9107d-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="9107d-105">\<client></span></span>  
<span data-ttu-id="9107d-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="9107d-106">\<metadata></span></span>  
<span data-ttu-id="9107d-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="9107d-107">\<policyImporters></span></span>  
<span data-ttu-id="9107d-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="9107d-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9107d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9107d-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9107d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9107d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9107d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9107d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9107d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9107d-112">Attributes</span></span>  
  
|<span data-ttu-id="9107d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="9107d-113">Attribute</span></span>|<span data-ttu-id="9107d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9107d-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9107d-115">Typ tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="9107d-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9107d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9107d-116">Child Elements</span></span>  
 <span data-ttu-id="9107d-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="9107d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9107d-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9107d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9107d-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="9107d-119">Element</span></span>|<span data-ttu-id="9107d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="9107d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9107d-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="9107d-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="9107d-122">Určuje všechny společnosti importers zásady, které řídí import kontrolních výrazů vlastních zásad o vazby.</span><span class="sxs-lookup"><span data-stu-id="9107d-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9107d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9107d-123">Remarks</span></span>  
 <span data-ttu-id="9107d-124">– Importér zásad se používá k hledání kontrolních výrazů vlastních zásad o vazbu funkce, jakož i připojit vlastní vazby element, který implementuje funkce, které vyžaduje kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="9107d-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9107d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9107d-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="9107d-126">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="9107d-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="9107d-127">Klienti</span><span class="sxs-lookup"><span data-stu-id="9107d-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
