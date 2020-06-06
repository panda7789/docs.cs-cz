---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854755"
---
# \<wsdlImporter>
<span data-ttu-id="21073-101">Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="21073-101">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="21073-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21073-102">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21073-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21073-103">Attributes and Elements</span></span>  
 <span data-ttu-id="21073-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21073-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21073-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="21073-105">Attributes</span></span>  
  
|<span data-ttu-id="21073-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="21073-106">Attribute</span></span>|<span data-ttu-id="21073-107">Popis</span><span class="sxs-lookup"><span data-stu-id="21073-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="21073-108">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="21073-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21073-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21073-109">Child Elements</span></span>  
 <span data-ttu-id="21073-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="21073-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21073-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21073-111">Parent Elements</span></span>  
  
|<span data-ttu-id="21073-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="21073-112">Element</span></span>|<span data-ttu-id="21073-113">Description</span><span class="sxs-lookup"><span data-stu-id="21073-113">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="21073-114">Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="21073-114">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21073-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21073-115">Remarks</span></span>  
 <span data-ttu-id="21073-116">Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="21073-116">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="21073-117">Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu.</span><span class="sxs-lookup"><span data-stu-id="21073-117">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="21073-118">Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.</span><span class="sxs-lookup"><span data-stu-id="21073-118">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21073-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="21073-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="21073-120">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="21073-120">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="21073-121">Klienti</span><span class="sxs-lookup"><span data-stu-id="21073-121">Clients</span></span>](../../../wcf/feature-details/clients.md)
