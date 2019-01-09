---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 43c1a50c740cd9c75ee641e4ac4d0fa8ea3ca36b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144987"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="15736-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="15736-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="15736-103">Určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="15736-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="15736-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="15736-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="15736-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="15736-105">\<client></span></span>  
<span data-ttu-id="15736-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="15736-106">\<metadata></span></span>  
<span data-ttu-id="15736-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="15736-107">\<wsdlImporters></span></span>  
<span data-ttu-id="15736-108">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="15736-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15736-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15736-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15736-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="15736-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15736-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="15736-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15736-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="15736-112">Attributes</span></span>  
  
|<span data-ttu-id="15736-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="15736-113">Attribute</span></span>|<span data-ttu-id="15736-114">Popis</span><span class="sxs-lookup"><span data-stu-id="15736-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="15736-115">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="15736-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15736-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="15736-116">Child Elements</span></span>  
 <span data-ttu-id="15736-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="15736-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15736-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="15736-118">Parent Elements</span></span>  
  
|<span data-ttu-id="15736-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="15736-119">Element</span></span>|<span data-ttu-id="15736-120">Popis</span><span class="sxs-lookup"><span data-stu-id="15736-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15736-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="15736-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="15736-122">Určuje všechny importers WSDL, které Importuje metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="15736-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15736-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15736-123">Remarks</span></span>  
 <span data-ttu-id="15736-124">Programu pro import WSDL umožňuje importovat metadata a také převést, které informace do různých tříd, které představují smlouvy a informace o koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="15736-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="15736-125">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="15736-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="15736-126">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="15736-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15736-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="15736-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="15736-128">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="15736-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="15736-129">Klienti</span><span class="sxs-lookup"><span data-stu-id="15736-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
