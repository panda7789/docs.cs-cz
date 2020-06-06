---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855225"
---
# \<metadata>
<span data-ttu-id="599f2-101">Určuje, jak se můžou zpracovávat metadata služby.</span><span class="sxs-lookup"><span data-stu-id="599f2-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="599f2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="599f2-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="599f2-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="599f2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="599f2-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="599f2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="599f2-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="599f2-105">Attributes</span></span>  
 <span data-ttu-id="599f2-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="599f2-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="599f2-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="599f2-107">Child Elements</span></span>  
  
|<span data-ttu-id="599f2-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="599f2-108">Element</span></span>|<span data-ttu-id="599f2-109">Description</span><span class="sxs-lookup"><span data-stu-id="599f2-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="599f2-110">Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="599f2-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="599f2-111">Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.</span><span class="sxs-lookup"><span data-stu-id="599f2-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="599f2-112">Určuje všechny nástroje pro Import WSDL, které importují metadata Web Services Description Language (WSDL) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="599f2-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="599f2-113">Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="599f2-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="599f2-114">Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu.</span><span class="sxs-lookup"><span data-stu-id="599f2-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="599f2-115">Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.</span><span class="sxs-lookup"><span data-stu-id="599f2-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="599f2-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="599f2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="599f2-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="599f2-117">Element</span></span>|<span data-ttu-id="599f2-118">Description</span><span class="sxs-lookup"><span data-stu-id="599f2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="599f2-119">Oddíl Client definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="599f2-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="599f2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="599f2-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="599f2-121">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="599f2-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="599f2-122">Klienti</span><span class="sxs-lookup"><span data-stu-id="599f2-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
