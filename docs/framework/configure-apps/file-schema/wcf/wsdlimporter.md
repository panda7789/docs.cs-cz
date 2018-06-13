---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 33c2b0e4286ce746f745e4aebe10fd4bbd96810f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754899"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="684da-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="684da-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="684da-103">Určuje všechny společnosti importers WSDL, která importuje metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad.</span><span class="sxs-lookup"><span data-stu-id="684da-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="684da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="684da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="684da-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="684da-105">\<client></span></span>  
<span data-ttu-id="684da-106">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="684da-106">\<metadata></span></span>  
<span data-ttu-id="684da-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="684da-107">\<wsdlImporters></span></span>  
<span data-ttu-id="684da-108">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="684da-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684da-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="684da-109">Syntax</span></span>  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="684da-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="684da-110">Attributes and Elements</span></span>  
 <span data-ttu-id="684da-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="684da-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="684da-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="684da-112">Attributes</span></span>  
  
|<span data-ttu-id="684da-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="684da-113">Attribute</span></span>|<span data-ttu-id="684da-114">Popis</span><span class="sxs-lookup"><span data-stu-id="684da-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="684da-115">Typ tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="684da-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="684da-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="684da-116">Child Elements</span></span>  
 <span data-ttu-id="684da-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="684da-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="684da-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="684da-118">Parent Elements</span></span>  
  
|<span data-ttu-id="684da-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="684da-119">Element</span></span>|<span data-ttu-id="684da-120">Popis</span><span class="sxs-lookup"><span data-stu-id="684da-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="684da-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="684da-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="684da-122">Určuje všechny společnosti importers WSDL, která importuje metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad.</span><span class="sxs-lookup"><span data-stu-id="684da-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="684da-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="684da-123">Remarks</span></span>  
 <span data-ttu-id="684da-124">Import metadat a také převést tento informace do různých tříd, které představují kontraktu a informace o koncovém se používá – Importér WSDL.</span><span class="sxs-lookup"><span data-stu-id="684da-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="684da-125">Selektivně ji můžete importovat informace o kontraktu a koncový bod a vlastnosti, které vystavit všechny chyby při importu a přijímat informace o typu relevantní pro proces importu a převod.</span><span class="sxs-lookup"><span data-stu-id="684da-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="684da-126">Také podporuje import informace o vazbě a vlastnosti, které poskytují přístup na všechny dokumenty zásad, WSDL dokumenty, rozšíření WSDL a dokumentech schémat XML.</span><span class="sxs-lookup"><span data-stu-id="684da-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684da-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="684da-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="684da-128">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="684da-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="684da-129">Klienti</span><span class="sxs-lookup"><span data-stu-id="684da-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
