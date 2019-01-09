---
title: '&lt;metadata&gt;'
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 119cd4d5b63f8d957bc6db9dd6aabdf9e2beeb64
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147366"
---
# <a name="ltmetadatagt"></a><span data-ttu-id="14502-102">&lt;metadata&gt;</span><span class="sxs-lookup"><span data-stu-id="14502-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="14502-103">Určuje způsob zpracování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="14502-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="14502-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14502-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14502-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="14502-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14502-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14502-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14502-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14502-107">Attributes and Elements</span></span>  
 <span data-ttu-id="14502-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14502-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14502-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="14502-109">Attributes</span></span>  
 <span data-ttu-id="14502-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="14502-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14502-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14502-111">Child Elements</span></span>  
  
|<span data-ttu-id="14502-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="14502-112">Element</span></span>|<span data-ttu-id="14502-113">Popis</span><span class="sxs-lookup"><span data-stu-id="14502-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14502-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="14502-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="14502-115">Určuje všechny nástroje pro import, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="14502-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="14502-116">Import zásady se používá k hledání kontrolních výrazů vlastních zásad o vazbách funkce, jakož i připojit vlastní prvek vazby, který implementuje funkce, které vyžaduje kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="14502-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="14502-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="14502-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="14502-118">Určuje všechny importers WSDL, které importují metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="14502-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="14502-119">Programu pro import WSDL umožňuje importovat metadata a také převést, které informace do různých tříd, které představují smlouvy a informace o koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="14502-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="14502-120">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="14502-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="14502-121">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="14502-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14502-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14502-122">Parent Elements</span></span>  
  
|<span data-ttu-id="14502-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="14502-123">Element</span></span>|<span data-ttu-id="14502-124">Popis</span><span class="sxs-lookup"><span data-stu-id="14502-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14502-125">\<klient ></span><span class="sxs-lookup"><span data-stu-id="14502-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="14502-126">Oddíl klienta definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="14502-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14502-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="14502-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="14502-128">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="14502-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="14502-129">Klienti</span><span class="sxs-lookup"><span data-stu-id="14502-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
