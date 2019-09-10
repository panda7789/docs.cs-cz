---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855225"
---
# <a name="metadata"></a><span data-ttu-id="5b77e-101">\<> metadat</span><span class="sxs-lookup"><span data-stu-id="5b77e-101">\<metadata></span></span>
<span data-ttu-id="5b77e-102">Určuje, jak se můžou zpracovávat metadata služby.</span><span class="sxs-lookup"><span data-stu-id="5b77e-102">Specifies how service metadata can be processed.</span></span>  
  
<span data-ttu-id="5b77e-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b77e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5b77e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5b77e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5b77e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="5b77e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="5b77e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> metadat**</span><span class="sxs-lookup"><span data-stu-id="5b77e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b77e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b77e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b77e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b77e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b77e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b77e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b77e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b77e-110">Attributes</span></span>  
 <span data-ttu-id="5b77e-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="5b77e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b77e-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b77e-112">Child Elements</span></span>  
  
|<span data-ttu-id="5b77e-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b77e-113">Element</span></span>|<span data-ttu-id="5b77e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5b77e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b77e-115">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="5b77e-115">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="5b77e-116">Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="5b77e-116">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="5b77e-117">Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.</span><span class="sxs-lookup"><span data-stu-id="5b77e-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="5b77e-118">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="5b77e-118">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="5b77e-119">Určuje všechny nástroje pro Import WSDL, které importují metadata Web Services Description Language (WSDL) 1,1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="5b77e-119">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="5b77e-120">Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="5b77e-120">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="5b77e-121">Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu.</span><span class="sxs-lookup"><span data-stu-id="5b77e-121">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="5b77e-122">Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.</span><span class="sxs-lookup"><span data-stu-id="5b77e-122">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b77e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b77e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5b77e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b77e-124">Element</span></span>|<span data-ttu-id="5b77e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5b77e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b77e-126">\<client></span><span class="sxs-lookup"><span data-stu-id="5b77e-126">\<client></span></span>](client.md)|<span data-ttu-id="5b77e-127">Oddíl Client definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="5b77e-127">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b77e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b77e-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="5b77e-129">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="5b77e-129">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="5b77e-130">Klienti</span><span class="sxs-lookup"><span data-stu-id="5b77e-130">Clients</span></span>](../../../wcf/feature-details/clients.md)
