---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855059"
---
# \<policyImporter>
<span data-ttu-id="16d34-101">Určuje dovozce zásad, který řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="16d34-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="16d34-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16d34-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16d34-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="16d34-103">Attributes and Elements</span></span>  
 <span data-ttu-id="16d34-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="16d34-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16d34-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="16d34-105">Attributes</span></span>  
  
|<span data-ttu-id="16d34-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="16d34-106">Attribute</span></span>|<span data-ttu-id="16d34-107">Popis</span><span class="sxs-lookup"><span data-stu-id="16d34-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="16d34-108">Typ tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="16d34-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16d34-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="16d34-109">Child Elements</span></span>  
 <span data-ttu-id="16d34-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="16d34-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16d34-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="16d34-111">Parent Elements</span></span>  
  
|<span data-ttu-id="16d34-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="16d34-112">Element</span></span>|<span data-ttu-id="16d34-113">Description</span><span class="sxs-lookup"><span data-stu-id="16d34-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="16d34-114">Určuje všechny zásady pro import, které řídí import vlastních výrazů zásad o vazbách.</span><span class="sxs-lookup"><span data-stu-id="16d34-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16d34-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16d34-115">Remarks</span></span>  
 <span data-ttu-id="16d34-116">Importér zásad slouží k hledání vlastních kontrolních výrazů zásad o funkcích vazby a také k připojení vlastního elementu vazby, který implementuje funkce vyžadované kontrolním výrazem.</span><span class="sxs-lookup"><span data-stu-id="16d34-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d34-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="16d34-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="16d34-118">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="16d34-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="16d34-119">Klienti</span><span class="sxs-lookup"><span data-stu-id="16d34-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
