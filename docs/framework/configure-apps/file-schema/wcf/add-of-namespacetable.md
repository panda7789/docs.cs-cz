---
title: "&lt;add&gt; – &lt;namespaceTable&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394657abcebb42192fb7a8b57b0402bcacf37693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="e1f60-102">&lt;add&gt; – &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="e1f60-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="e1f60-103">Představuje konfiguraci elementu, který obsahuje obor názvů jako předpona mapování, která lze poté použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="e1f60-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="e1f60-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e1f60-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e1f60-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="e1f60-105">\<routing></span></span>  
<span data-ttu-id="e1f60-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="e1f60-106">\<namespaceTable></span></span>  
<span data-ttu-id="e1f60-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="e1f60-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f60-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1f60-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1f60-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e1f60-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1f60-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e1f60-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1f60-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e1f60-111">Attributes</span></span>  
  
|<span data-ttu-id="e1f60-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e1f60-112">Attribute</span></span>|<span data-ttu-id="e1f60-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e1f60-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1f60-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="e1f60-114">namespace</span></span>|<span data-ttu-id="e1f60-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e1f60-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="e1f60-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="e1f60-116">prefix</span></span>|<span data-ttu-id="e1f60-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e1f60-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1f60-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e1f60-118">Child Elements</span></span>  
 <span data-ttu-id="e1f60-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1f60-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1f60-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e1f60-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1f60-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1f60-121">Element</span></span>|<span data-ttu-id="e1f60-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e1f60-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1f60-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="e1f60-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="e1f60-124">Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="e1f60-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1f60-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1f60-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
