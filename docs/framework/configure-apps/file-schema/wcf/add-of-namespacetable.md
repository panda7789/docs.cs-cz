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
ms.openlocfilehash: 5f159e3d92fdc7443cd20cf88300f331b78273ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="de05e-102">&lt;add&gt; – &lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="de05e-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="de05e-103">Představuje konfiguraci elementu, který obsahuje obor názvů jako předpona mapování, která lze poté použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="de05e-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="de05e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="de05e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="de05e-105">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="de05e-105">\<routing></span></span>  
<span data-ttu-id="de05e-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="de05e-106">\<namespaceTable></span></span>  
<span data-ttu-id="de05e-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="de05e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de05e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de05e-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de05e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de05e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de05e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de05e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de05e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="de05e-111">Attributes</span></span>  
  
|<span data-ttu-id="de05e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="de05e-112">Attribute</span></span>|<span data-ttu-id="de05e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="de05e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de05e-114">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="de05e-114">namespace</span></span>|<span data-ttu-id="de05e-115">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="de05e-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="de05e-116">Předpona</span><span class="sxs-lookup"><span data-stu-id="de05e-116">prefix</span></span>|<span data-ttu-id="de05e-117">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="de05e-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de05e-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de05e-118">Child Elements</span></span>  
 <span data-ttu-id="de05e-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="de05e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de05e-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de05e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="de05e-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="de05e-121">Element</span></span>|<span data-ttu-id="de05e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="de05e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de05e-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="de05e-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="de05e-124">Představuje konfigurační oddíl pro definování sady elementů, které obsahují obor názvů pro mapování předpony, které lze použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="de05e-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de05e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="de05e-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
