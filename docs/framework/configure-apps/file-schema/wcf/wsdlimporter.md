---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854755"
---
# <a name="wsdlimporter"></a><span data-ttu-id="55bec-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="55bec-101">\<wsdlImporter></span></span>
<span data-ttu-id="55bec-102">Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="55bec-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="55bec-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55bec-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55bec-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="55bec-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="55bec-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="55bec-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="55bec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> metadat**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="55bec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="55bec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsdlImporters >** ](wsdlimporters.md)</span><span class="sxs-lookup"><span data-stu-id="55bec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)</span></span>  
<span data-ttu-id="55bec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<WsdlImporter nalezl >**</span><span class="sxs-lookup"><span data-stu-id="55bec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55bec-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55bec-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55bec-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="55bec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55bec-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="55bec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55bec-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="55bec-112">Attributes</span></span>  
  
|<span data-ttu-id="55bec-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="55bec-113">Attribute</span></span>|<span data-ttu-id="55bec-114">Popis</span><span class="sxs-lookup"><span data-stu-id="55bec-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="55bec-115">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="55bec-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55bec-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="55bec-116">Child Elements</span></span>  
 <span data-ttu-id="55bec-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="55bec-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55bec-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="55bec-118">Parent Elements</span></span>  
  
|<span data-ttu-id="55bec-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="55bec-119">Element</span></span>|<span data-ttu-id="55bec-120">Popis</span><span class="sxs-lookup"><span data-stu-id="55bec-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55bec-121">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="55bec-121">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="55bec-122">Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="55bec-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55bec-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55bec-123">Remarks</span></span>  
 <span data-ttu-id="55bec-124">Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="55bec-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="55bec-125">Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu.</span><span class="sxs-lookup"><span data-stu-id="55bec-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="55bec-126">Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.</span><span class="sxs-lookup"><span data-stu-id="55bec-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55bec-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55bec-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="55bec-128">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="55bec-128">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="55bec-129">Klienti</span><span class="sxs-lookup"><span data-stu-id="55bec-129">Clients</span></span>](../../../wcf/feature-details/clients.md)
