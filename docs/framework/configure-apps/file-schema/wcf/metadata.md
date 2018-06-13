---
title: '&lt;metadata&gt;'
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 7e314ae56ed7a1b532bb8946fbb28802e72d3e20
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747850"
---
# <a name="ltmetadatagt"></a><span data-ttu-id="60b4e-102">&lt;metadata&gt;</span><span class="sxs-lookup"><span data-stu-id="60b4e-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="60b4e-103">Určuje, jak může být zpracována metadata služby.</span><span class="sxs-lookup"><span data-stu-id="60b4e-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="60b4e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="60b4e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="60b4e-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="60b4e-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b4e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60b4e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60b4e-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60b4e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="60b4e-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60b4e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60b4e-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="60b4e-109">Attributes</span></span>  
 <span data-ttu-id="60b4e-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="60b4e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60b4e-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60b4e-111">Child Elements</span></span>  
  
|<span data-ttu-id="60b4e-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="60b4e-112">Element</span></span>|<span data-ttu-id="60b4e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="60b4e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60b4e-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="60b4e-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="60b4e-115">Určuje všechny společnosti importers zásady, které řídí import kontrolních výrazů vlastních zásad o vazby.</span><span class="sxs-lookup"><span data-stu-id="60b4e-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="60b4e-116">– Importér zásad se používá k hledání kontrolních výrazů vlastních zásad o vazbu funkce, jakož i připojit vlastní vazby element, který implementuje funkce, které vyžaduje kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="60b4e-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="60b4e-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="60b4e-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="60b4e-118">Určuje všechny společnosti importers WSDL, které importovat metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad.</span><span class="sxs-lookup"><span data-stu-id="60b4e-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="60b4e-119">Import metadat a také převést tento informace do různých tříd, které představují kontraktu a informace o koncovém se používá – Importér WSDL.</span><span class="sxs-lookup"><span data-stu-id="60b4e-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="60b4e-120">Selektivně ji můžete importovat informace o kontraktu a koncový bod a vlastnosti, které vystavit všechny chyby při importu a přijímat informace o typu relevantní pro proces importu a převod.</span><span class="sxs-lookup"><span data-stu-id="60b4e-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="60b4e-121">Také podporuje import informace o vazbě a vlastnosti, které poskytují přístup na všechny dokumenty zásad, WSDL dokumenty, rozšíření WSDL a dokumentech schémat XML.</span><span class="sxs-lookup"><span data-stu-id="60b4e-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60b4e-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60b4e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="60b4e-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="60b4e-123">Element</span></span>|<span data-ttu-id="60b4e-124">Popis</span><span class="sxs-lookup"><span data-stu-id="60b4e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60b4e-125">\<klient ></span><span class="sxs-lookup"><span data-stu-id="60b4e-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="60b4e-126">Oddíl klienta definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="60b4e-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60b4e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="60b4e-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="60b4e-128">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="60b4e-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="60b4e-129">Klienti</span><span class="sxs-lookup"><span data-stu-id="60b4e-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
