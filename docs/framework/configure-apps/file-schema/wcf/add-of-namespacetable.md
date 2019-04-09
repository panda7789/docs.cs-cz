---
title: <add> of <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089715"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="271dc-102">\<Přidat > z \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="271dc-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="271dc-103">Představuje prvek konfigurace, který obsahuje obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="271dc-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="271dc-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="271dc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="271dc-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="271dc-105">\<routing></span></span>  
<span data-ttu-id="271dc-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="271dc-106">\<namespaceTable></span></span>  
<span data-ttu-id="271dc-107">\<add></span><span class="sxs-lookup"><span data-stu-id="271dc-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="271dc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="271dc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="271dc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="271dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="271dc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="271dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="271dc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="271dc-111">Attributes</span></span>  
  
|<span data-ttu-id="271dc-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="271dc-112">Attribute</span></span>|<span data-ttu-id="271dc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="271dc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="271dc-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="271dc-114">namespace</span></span>|<span data-ttu-id="271dc-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="271dc-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="271dc-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="271dc-116">prefix</span></span>|<span data-ttu-id="271dc-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="271dc-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="271dc-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="271dc-118">Child Elements</span></span>  
 <span data-ttu-id="271dc-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="271dc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="271dc-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="271dc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="271dc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="271dc-121">Element</span></span>|<span data-ttu-id="271dc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="271dc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="271dc-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="271dc-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="271dc-124">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="271dc-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="271dc-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="271dc-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
