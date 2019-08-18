---
title: <add> z <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 32eff2e7bfdf1aee4c7d37a0e06166afba3cb398
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566745"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="96149-102">\<Přidání > \<> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="96149-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="96149-103">Představuje prvek konfigurace, který obsahuje obor názvů pro mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="96149-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="96149-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96149-104">\<system.serviceModel></span></span>  
<span data-ttu-id="96149-105">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="96149-105">\<routing></span></span>  
<span data-ttu-id="96149-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="96149-106">\<namespaceTable></span></span>  
<span data-ttu-id="96149-107">\<add></span><span class="sxs-lookup"><span data-stu-id="96149-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96149-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96149-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96149-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96149-109">Attributes and Elements</span></span>  
 <span data-ttu-id="96149-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96149-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96149-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="96149-111">Attributes</span></span>  
  
|<span data-ttu-id="96149-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="96149-112">Attribute</span></span>|<span data-ttu-id="96149-113">Popis</span><span class="sxs-lookup"><span data-stu-id="96149-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96149-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="96149-114">namespace</span></span>|<span data-ttu-id="96149-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="96149-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="96149-116">prefix</span><span class="sxs-lookup"><span data-stu-id="96149-116">prefix</span></span>|<span data-ttu-id="96149-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="96149-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96149-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96149-118">Child Elements</span></span>  
 <span data-ttu-id="96149-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="96149-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96149-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96149-120">Parent Elements</span></span>  
  
|<span data-ttu-id="96149-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="96149-121">Element</span></span>|<span data-ttu-id="96149-122">Popis</span><span class="sxs-lookup"><span data-stu-id="96149-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96149-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="96149-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="96149-124">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="96149-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96149-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96149-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
