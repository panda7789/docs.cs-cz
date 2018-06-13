---
title: '&lt;add&gt; – &lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 5ae672f12a2ef58efc9738624c113855e59e02b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748630"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="dec67-102">&lt;add&gt; – &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="dec67-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="dec67-103">Představuje konfiguraci elementu, který obsahuje obor názvů jako předpona mapování, která lze poté použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="dec67-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="dec67-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dec67-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dec67-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="dec67-105">\<routing></span></span>  
<span data-ttu-id="dec67-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="dec67-106">\<namespaceTable></span></span>  
<span data-ttu-id="dec67-107">\<add></span><span class="sxs-lookup"><span data-stu-id="dec67-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec67-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dec67-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dec67-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dec67-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dec67-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dec67-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dec67-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="dec67-111">Attributes</span></span>  
  
|<span data-ttu-id="dec67-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="dec67-112">Attribute</span></span>|<span data-ttu-id="dec67-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dec67-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dec67-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="dec67-114">namespace</span></span>|<span data-ttu-id="dec67-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dec67-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="dec67-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="dec67-116">prefix</span></span>|<span data-ttu-id="dec67-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dec67-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dec67-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dec67-118">Child Elements</span></span>  
 <span data-ttu-id="dec67-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="dec67-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dec67-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dec67-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dec67-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="dec67-121">Element</span></span>|<span data-ttu-id="dec67-122">Popis</span><span class="sxs-lookup"><span data-stu-id="dec67-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dec67-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="dec67-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="dec67-124">Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="dec67-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dec67-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="dec67-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
