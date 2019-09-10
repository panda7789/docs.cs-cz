---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855059"
---
# <a name="policyimporter"></a><span data-ttu-id="e63c9-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="e63c9-101">\<policyImporter></span></span>
<span data-ttu-id="e63c9-102">Určuje dovozce zásad, který řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="e63c9-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
<span data-ttu-id="e63c9-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e63c9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e63c9-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e63c9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e63c9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="e63c9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="e63c9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> metadat**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="e63c9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="e63c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<policyImporters >** ](policyimporters.md)</span><span class="sxs-lookup"><span data-stu-id="e63c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)</span></span>  
<span data-ttu-id="e63c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<policyImporter >**</span><span class="sxs-lookup"><span data-stu-id="e63c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63c9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e63c9-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e63c9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e63c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e63c9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e63c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e63c9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e63c9-112">Attributes</span></span>  
  
|<span data-ttu-id="e63c9-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e63c9-113">Attribute</span></span>|<span data-ttu-id="e63c9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e63c9-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e63c9-115">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="e63c9-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e63c9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e63c9-116">Child Elements</span></span>  
 <span data-ttu-id="e63c9-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="e63c9-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e63c9-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e63c9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e63c9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e63c9-119">Element</span></span>|<span data-ttu-id="e63c9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e63c9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e63c9-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="e63c9-121">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="e63c9-122">Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="e63c9-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e63c9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e63c9-123">Remarks</span></span>  
 <span data-ttu-id="e63c9-124">Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.</span><span class="sxs-lookup"><span data-stu-id="e63c9-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63c9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e63c9-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="e63c9-126">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="e63c9-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e63c9-127">Klienti</span><span class="sxs-lookup"><span data-stu-id="e63c9-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
