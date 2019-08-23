---
title: <add> z <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e2a2e26099f2d31116e4a89297fc1ac984c480d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920077"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="6fd3f-102">\<Přidání > \<> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="6fd3f-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="6fd3f-103">Představuje prvek konfigurace, který obsahuje obor názvů pro mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="6fd3f-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="6fd3f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6fd3f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6fd3f-105">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="6fd3f-105">\<routing></span></span>  
<span data-ttu-id="6fd3f-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="6fd3f-106">\<namespaceTable></span></span>  
<span data-ttu-id="6fd3f-107">\<add></span><span class="sxs-lookup"><span data-stu-id="6fd3f-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd3f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fd3f-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fd3f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6fd3f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6fd3f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6fd3f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fd3f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6fd3f-111">Attributes</span></span>  
  
|<span data-ttu-id="6fd3f-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6fd3f-112">Attribute</span></span>|<span data-ttu-id="6fd3f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6fd3f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6fd3f-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="6fd3f-114">namespace</span></span>|<span data-ttu-id="6fd3f-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6fd3f-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="6fd3f-116">prefix</span><span class="sxs-lookup"><span data-stu-id="6fd3f-116">prefix</span></span>|<span data-ttu-id="6fd3f-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6fd3f-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fd3f-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6fd3f-118">Child Elements</span></span>  
 <span data-ttu-id="6fd3f-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="6fd3f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fd3f-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6fd3f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6fd3f-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="6fd3f-121">Element</span></span>|<span data-ttu-id="6fd3f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6fd3f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fd3f-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="6fd3f-123">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="6fd3f-124">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="6fd3f-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fd3f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fd3f-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
