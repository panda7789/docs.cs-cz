---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 1ff59a3a1a075be4f8024a2a78921d1d50311327
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270794"
---
# <a name="metadata"></a><span data-ttu-id="02170-101">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="02170-101">\<metadata></span></span>
<span data-ttu-id="02170-102">Určuje způsob zpracování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="02170-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="02170-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02170-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="02170-104">\<client></span><span class="sxs-lookup"><span data-stu-id="02170-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02170-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02170-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02170-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02170-106">Attributes and Elements</span></span>  
 <span data-ttu-id="02170-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02170-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02170-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="02170-108">Attributes</span></span>  
 <span data-ttu-id="02170-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="02170-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02170-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02170-110">Child Elements</span></span>  
  
|<span data-ttu-id="02170-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="02170-111">Element</span></span>|<span data-ttu-id="02170-112">Popis</span><span class="sxs-lookup"><span data-stu-id="02170-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02170-113">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="02170-113">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="02170-114">Určuje všechny nástroje pro import, které řídí import kontrolních výrazů vlastních zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="02170-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="02170-115">Import zásady se používá k hledání kontrolních výrazů vlastních zásad o vazbách funkce, jakož i připojit vlastní prvek vazby, který implementuje funkce, které vyžaduje kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="02170-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="02170-116">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="02170-116">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="02170-117">Určuje všechny importers WSDL, které importují metadata webové služby WSDL (Description Language) 1.1 s přílohami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="02170-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="02170-118">Programu pro import WSDL umožňuje importovat metadata a také převést, které informace do různých tříd, které představují smlouvy a informace o koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="02170-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="02170-119">Selektivně mohl importovat informace o smlouvě a koncový bod a vlastnosti, které zveřejnit jakékoli chyby importu a přijímat informace o typu relevantní pro import a převod balíčků.</span><span class="sxs-lookup"><span data-stu-id="02170-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="02170-120">Podporuje také importovat informace o vazbě a vlastnosti, které poskytují přístup k dokumentům zásad, dokumenty WSDL, rozšíření WSDL a dokumentů schématu XML.</span><span class="sxs-lookup"><span data-stu-id="02170-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02170-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02170-121">Parent Elements</span></span>  
  
|<span data-ttu-id="02170-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="02170-122">Element</span></span>|<span data-ttu-id="02170-123">Popis</span><span class="sxs-lookup"><span data-stu-id="02170-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02170-124">\<client></span><span class="sxs-lookup"><span data-stu-id="02170-124">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="02170-125">Oddíl klienta definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="02170-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02170-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02170-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="02170-127">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="02170-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="02170-128">Klienti</span><span class="sxs-lookup"><span data-stu-id="02170-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
