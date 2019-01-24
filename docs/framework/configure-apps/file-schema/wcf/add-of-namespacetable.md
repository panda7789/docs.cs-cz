---
title: '&lt;add&gt; – &lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 1d3b61fa6653b3910e65b95fa96fd0657e72bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632903"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="afca5-102">&lt;add&gt; – &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="afca5-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="afca5-103">Představuje prvek konfigurace, který obsahuje obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="afca5-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="afca5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="afca5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="afca5-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="afca5-105">\<routing></span></span>  
<span data-ttu-id="afca5-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="afca5-106">\<namespaceTable></span></span>  
<span data-ttu-id="afca5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="afca5-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afca5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afca5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afca5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="afca5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="afca5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="afca5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afca5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="afca5-111">Attributes</span></span>  
  
|<span data-ttu-id="afca5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="afca5-112">Attribute</span></span>|<span data-ttu-id="afca5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="afca5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afca5-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="afca5-114">namespace</span></span>|<span data-ttu-id="afca5-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="afca5-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="afca5-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="afca5-116">prefix</span></span>|<span data-ttu-id="afca5-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="afca5-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afca5-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="afca5-118">Child Elements</span></span>  
 <span data-ttu-id="afca5-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="afca5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afca5-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="afca5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="afca5-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="afca5-121">Element</span></span>|<span data-ttu-id="afca5-122">Popis</span><span class="sxs-lookup"><span data-stu-id="afca5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afca5-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="afca5-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="afca5-124">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="afca5-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afca5-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afca5-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
