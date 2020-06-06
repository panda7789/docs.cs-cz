---
title: Element <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153227"
---
# <a name="switches-element"></a><span data-ttu-id="11d2b-102">Element \<switches></span><span class="sxs-lookup"><span data-stu-id="11d2b-102">\<switches> Element</span></span>
<span data-ttu-id="11d2b-103">Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="11d2b-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="11d2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d2b-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11d2b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11d2b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="11d2b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11d2b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11d2b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="11d2b-107">Attributes</span></span>  
 <span data-ttu-id="11d2b-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="11d2b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11d2b-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11d2b-109">Child Elements</span></span>  
  
|<span data-ttu-id="11d2b-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="11d2b-110">Element</span></span>|<span data-ttu-id="11d2b-111">Description</span><span class="sxs-lookup"><span data-stu-id="11d2b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="11d2b-112">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="11d2b-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11d2b-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11d2b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="11d2b-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="11d2b-114">Element</span></span>|<span data-ttu-id="11d2b-115">Description</span><span class="sxs-lookup"><span data-stu-id="11d2b-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="11d2b-116">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11d2b-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="11d2b-117">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="11d2b-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11d2b-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11d2b-118">Remarks</span></span>  
 <span data-ttu-id="11d2b-119">Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="11d2b-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="11d2b-120">Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch> , můžete ho zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="11d2b-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="11d2b-121">Pokud je přepínač <xref:System.Diagnostics.TraceSwitch> , můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv výstupem aplikace.</span><span class="sxs-lookup"><span data-stu-id="11d2b-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11d2b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="11d2b-122">Example</span></span>  
 <span data-ttu-id="11d2b-123">Následující příklad ukazuje, jak použít **\<switch>** prvek pro nastavení `General` přepínače trasování na <xref:System.Diagnostics.TraceLevel> úroveň a povolení `Data` logického sledovacího přepínače.</span><span class="sxs-lookup"><span data-stu-id="11d2b-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11d2b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d2b-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="11d2b-125">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="11d2b-125">Trace and Debug Settings Schema</span></span>](index.md)
