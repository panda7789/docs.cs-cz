---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915191"
---
# <a name="wsdlimporter"></a><span data-ttu-id="3c793-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="3c793-101">\<wsdlImporter></span></span>
<span data-ttu-id="3c793-102">Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="3c793-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="3c793-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3c793-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3c793-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="3c793-104">\<client></span></span>  
<span data-ttu-id="3c793-105">\<> metadat</span><span class="sxs-lookup"><span data-stu-id="3c793-105">\<metadata></span></span>  
<span data-ttu-id="3c793-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="3c793-106">\<wsdlImporters></span></span>  
<span data-ttu-id="3c793-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="3c793-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c793-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c793-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c793-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3c793-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3c793-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3c793-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c793-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3c793-111">Attributes</span></span>  
  
|<span data-ttu-id="3c793-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3c793-112">Attribute</span></span>|<span data-ttu-id="3c793-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3c793-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3c793-114">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="3c793-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c793-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3c793-115">Child Elements</span></span>  
 <span data-ttu-id="3c793-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="3c793-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c793-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3c793-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3c793-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="3c793-118">Element</span></span>|<span data-ttu-id="3c793-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3c793-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c793-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="3c793-120">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="3c793-121">Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="3c793-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c793-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c793-122">Remarks</span></span>  
 <span data-ttu-id="3c793-123">Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="3c793-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="3c793-124">Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu.</span><span class="sxs-lookup"><span data-stu-id="3c793-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="3c793-125">Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.</span><span class="sxs-lookup"><span data-stu-id="3c793-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c793-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c793-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="3c793-127">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="3c793-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="3c793-128">Klienti</span><span class="sxs-lookup"><span data-stu-id="3c793-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
