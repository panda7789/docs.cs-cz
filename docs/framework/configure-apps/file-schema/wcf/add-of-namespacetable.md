---
title: <add> z <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850392"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="680b5-102">\<Přidání > \<> oboru názvů</span><span class="sxs-lookup"><span data-stu-id="680b5-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="680b5-103">Představuje prvek konfigurace, který obsahuje obor názvů pro mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="680b5-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
<span data-ttu-id="680b5-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="680b5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="680b5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="680b5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="680b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="680b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="680b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> oboru názvů**](namespacetable.md)</span><span class="sxs-lookup"><span data-stu-id="680b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)</span></span>\
<span data-ttu-id="680b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="680b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="680b5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="680b5-109">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="680b5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="680b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="680b5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="680b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="680b5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="680b5-112">Attributes</span></span>  
  
|<span data-ttu-id="680b5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="680b5-113">Attribute</span></span>|<span data-ttu-id="680b5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="680b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="680b5-115">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="680b5-115">namespace</span></span>|<span data-ttu-id="680b5-116">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="680b5-116">A string containing the namespace.</span></span>|  
|<span data-ttu-id="680b5-117">prefix</span><span class="sxs-lookup"><span data-stu-id="680b5-117">prefix</span></span>|<span data-ttu-id="680b5-118">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="680b5-118">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="680b5-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="680b5-119">Child Elements</span></span>  
 <span data-ttu-id="680b5-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="680b5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="680b5-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="680b5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="680b5-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="680b5-122">Element</span></span>|<span data-ttu-id="680b5-123">Popis</span><span class="sxs-lookup"><span data-stu-id="680b5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="680b5-124">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="680b5-124">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="680b5-125">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="680b5-125">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="680b5-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="680b5-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
