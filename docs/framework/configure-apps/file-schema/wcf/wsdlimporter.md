---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 5f3d53111c4d303146701b03d7e7b32833cd9edd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651042"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="82f19-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="82f19-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="82f19-103">Určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="82f19-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="82f19-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="82f19-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="82f19-105">\<client></span><span class="sxs-lookup"><span data-stu-id="82f19-105">\<client></span></span>  
<span data-ttu-id="82f19-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="82f19-106">\<metadata></span></span>  
<span data-ttu-id="82f19-107">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="82f19-107">\<wsdlImporters></span></span>  
<span data-ttu-id="82f19-108">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="82f19-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f19-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82f19-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82f19-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82f19-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82f19-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82f19-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82f19-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="82f19-112">Attributes</span></span>  
  
|<span data-ttu-id="82f19-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="82f19-113">Attribute</span></span>|<span data-ttu-id="82f19-114">Popis</span><span class="sxs-lookup"><span data-stu-id="82f19-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="82f19-115">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="82f19-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82f19-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82f19-116">Child Elements</span></span>  
 <span data-ttu-id="82f19-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="82f19-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82f19-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82f19-118">Parent Elements</span></span>  
  
|<span data-ttu-id="82f19-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="82f19-119">Element</span></span>|<span data-ttu-id="82f19-120">Popis</span><span class="sxs-lookup"><span data-stu-id="82f19-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82f19-121">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="82f19-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="82f19-122">Určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="82f19-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82f19-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82f19-123">Remarks</span></span>  
 <span data-ttu-id="82f19-124">Programu pro import WSDL umožňuje importovat metadata a také převést, které informace do různých tříd, které představují smlouvy a informace o koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="82f19-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="82f19-125">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="82f19-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="82f19-126">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="82f19-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f19-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82f19-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="82f19-128">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="82f19-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="82f19-129">Klienti</span><span class="sxs-lookup"><span data-stu-id="82f19-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
