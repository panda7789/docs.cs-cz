---
title: <add> z <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850392"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="ca536-102">\<add> z \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="ca536-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="ca536-103">Představuje prvek konfigurace, který obsahuje obor názvů pro mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="ca536-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ca536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca536-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca536-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca536-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ca536-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca536-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca536-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca536-107">Attributes</span></span>  
  
|<span data-ttu-id="ca536-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ca536-108">Attribute</span></span>|<span data-ttu-id="ca536-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ca536-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca536-110">namespace</span><span class="sxs-lookup"><span data-stu-id="ca536-110">namespace</span></span>|<span data-ttu-id="ca536-111">Řetězec obsahující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ca536-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="ca536-112">směr</span><span class="sxs-lookup"><span data-stu-id="ca536-112">prefix</span></span>|<span data-ttu-id="ca536-113">Řetězec obsahující předponu pro tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ca536-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca536-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca536-114">Child Elements</span></span>  
 <span data-ttu-id="ca536-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="ca536-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca536-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca536-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ca536-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca536-117">Element</span></span>|<span data-ttu-id="ca536-118">Description</span><span class="sxs-lookup"><span data-stu-id="ca536-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="ca536-119">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="ca536-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca536-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca536-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
