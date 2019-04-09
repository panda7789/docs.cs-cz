---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 1f34486296465b3ea0b5b05bd9492062c85ad8c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134430"
---
# <a name="wsdlimporter"></a><span data-ttu-id="6b78c-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="6b78c-101">\<wsdlImporter></span></span>
<span data-ttu-id="6b78c-102">Určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="6b78c-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="6b78c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b78c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b78c-104">\<client></span><span class="sxs-lookup"><span data-stu-id="6b78c-104">\<client></span></span>  
<span data-ttu-id="6b78c-105">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="6b78c-105">\<metadata></span></span>  
<span data-ttu-id="6b78c-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="6b78c-106">\<wsdlImporters></span></span>  
<span data-ttu-id="6b78c-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="6b78c-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b78c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b78c-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b78c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b78c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6b78c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6b78c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b78c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b78c-111">Attributes</span></span>  
  
|<span data-ttu-id="6b78c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b78c-112">Attribute</span></span>|<span data-ttu-id="6b78c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6b78c-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6b78c-114">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="6b78c-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b78c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b78c-115">Child Elements</span></span>  
 <span data-ttu-id="6b78c-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="6b78c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b78c-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b78c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6b78c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b78c-118">Element</span></span>|<span data-ttu-id="6b78c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6b78c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b78c-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="6b78c-120">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="6b78c-121">Určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="6b78c-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b78c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b78c-122">Remarks</span></span>  
 <span data-ttu-id="6b78c-123">Programu pro import WSDL umožňuje importovat metadata a také převést, které informace do různých tříd, které představují smlouvy a informace o koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="6b78c-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="6b78c-124">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="6b78c-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="6b78c-125">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="6b78c-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b78c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b78c-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="6b78c-127">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="6b78c-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="6b78c-128">Klienti</span><span class="sxs-lookup"><span data-stu-id="6b78c-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
