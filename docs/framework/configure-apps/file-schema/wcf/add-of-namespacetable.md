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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f08f4b46c6e6290602fc78a2f06954b9cf0b07d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="3bbfd-102">&lt;add&gt; – &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="3bbfd-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="3bbfd-103">Představuje konfiguraci elementu, který obsahuje obor názvů jako předpona mapování, která lze poté použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="3bbfd-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="3bbfd-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3bbfd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3bbfd-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="3bbfd-105">\<routing></span></span>  
<span data-ttu-id="3bbfd-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="3bbfd-106">\<namespaceTable></span></span>  
<span data-ttu-id="3bbfd-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="3bbfd-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbfd-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bbfd-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bbfd-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3bbfd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3bbfd-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3bbfd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bbfd-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3bbfd-111">Attributes</span></span>  
  
|<span data-ttu-id="3bbfd-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3bbfd-112">Attribute</span></span>|<span data-ttu-id="3bbfd-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3bbfd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bbfd-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="3bbfd-114">namespace</span></span>|<span data-ttu-id="3bbfd-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3bbfd-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="3bbfd-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="3bbfd-116">prefix</span></span>|<span data-ttu-id="3bbfd-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3bbfd-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bbfd-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3bbfd-118">Child Elements</span></span>  
 <span data-ttu-id="3bbfd-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="3bbfd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bbfd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3bbfd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3bbfd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="3bbfd-121">Element</span></span>|<span data-ttu-id="3bbfd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3bbfd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bbfd-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="3bbfd-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="3bbfd-124">Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="3bbfd-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bbfd-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bbfd-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
