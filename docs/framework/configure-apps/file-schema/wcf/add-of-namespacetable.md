---
title: <add> z <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089715"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="d0634-102">\<Přidat > z \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="d0634-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="d0634-103">Představuje prvek konfigurace, který obsahuje obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="d0634-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="d0634-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0634-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d0634-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="d0634-105">\<routing></span></span>  
<span data-ttu-id="d0634-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="d0634-106">\<namespaceTable></span></span>  
<span data-ttu-id="d0634-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d0634-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0634-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0634-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0634-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d0634-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d0634-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d0634-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0634-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d0634-111">Attributes</span></span>  
  
|<span data-ttu-id="d0634-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d0634-112">Attribute</span></span>|<span data-ttu-id="d0634-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d0634-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0634-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="d0634-114">namespace</span></span>|<span data-ttu-id="d0634-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d0634-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="d0634-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="d0634-116">prefix</span></span>|<span data-ttu-id="d0634-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d0634-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0634-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d0634-118">Child Elements</span></span>  
 <span data-ttu-id="d0634-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="d0634-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0634-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d0634-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d0634-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d0634-121">Element</span></span>|<span data-ttu-id="d0634-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d0634-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0634-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="d0634-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="d0634-124">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="d0634-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0634-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0634-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
