---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 4555dc9c2e0b783de2fb57e47c9aada0d69462e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931303"
---
# <a name="metadata"></a><span data-ttu-id="5fb1f-101">\<> metadat</span><span class="sxs-lookup"><span data-stu-id="5fb1f-101">\<metadata></span></span>
<span data-ttu-id="5fb1f-102">Určuje, jak se můžou zpracovávat metadata služby.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="5fb1f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5fb1f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5fb1f-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="5fb1f-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb1f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fb1f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fb1f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5fb1f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5fb1f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fb1f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="5fb1f-108">Attributes</span></span>  
 <span data-ttu-id="5fb1f-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="5fb1f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5fb1f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5fb1f-110">Child Elements</span></span>  
  
|<span data-ttu-id="5fb1f-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="5fb1f-111">Element</span></span>|<span data-ttu-id="5fb1f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5fb1f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fb1f-113">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="5fb1f-113">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="5fb1f-114">Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="5fb1f-115">Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="5fb1f-116">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="5fb1f-116">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="5fb1f-117">Určuje všechny nástroje pro Import WSDL, které importují metadata Web Services Description Language (WSDL) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="5fb1f-118">Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="5fb1f-119">Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="5fb1f-120">Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5fb1f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5fb1f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5fb1f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5fb1f-122">Element</span></span>|<span data-ttu-id="5fb1f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5fb1f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fb1f-124">\<client></span><span class="sxs-lookup"><span data-stu-id="5fb1f-124">\<client></span></span>](client.md)|<span data-ttu-id="5fb1f-125">Oddíl Client definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="5fb1f-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fb1f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fb1f-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="5fb1f-127">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="5fb1f-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="5fb1f-128">Klienti</span><span class="sxs-lookup"><span data-stu-id="5fb1f-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
