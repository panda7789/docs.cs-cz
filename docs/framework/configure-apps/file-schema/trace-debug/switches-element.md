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
ms.openlocfilehash: 92a1c8db43579048945d76082e3ebd2862efd7ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920440"
---
# <a name="switches-element"></a><span data-ttu-id="c723b-102">\<přepne > element.</span><span class="sxs-lookup"><span data-stu-id="c723b-102">\<switches> Element</span></span>
<span data-ttu-id="c723b-103">Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="c723b-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="c723b-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c723b-104">\<configuration></span></span>  
<span data-ttu-id="c723b-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="c723b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c723b-106">\<přepne ></span><span class="sxs-lookup"><span data-stu-id="c723b-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c723b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c723b-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c723b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c723b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c723b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c723b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c723b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c723b-110">Attributes</span></span>  
 <span data-ttu-id="c723b-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c723b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c723b-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c723b-112">Child Elements</span></span>  
  
|<span data-ttu-id="c723b-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="c723b-113">Element</span></span>|<span data-ttu-id="c723b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c723b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c723b-115">\<add></span><span class="sxs-lookup"><span data-stu-id="c723b-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="c723b-116">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c723b-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c723b-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c723b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c723b-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c723b-118">Element</span></span>|<span data-ttu-id="c723b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c723b-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c723b-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c723b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="c723b-121">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c723b-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c723b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c723b-122">Remarks</span></span>  
 <span data-ttu-id="c723b-123">Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c723b-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="c723b-124">Pokud je <xref:System.Diagnostics.BooleanSwitch>přepínač, můžete ho zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="c723b-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="c723b-125">Pokud je <xref:System.Diagnostics.TraceSwitch>přepínač, můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv výstupem aplikace.</span><span class="sxs-lookup"><span data-stu-id="c723b-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c723b-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="c723b-126">Example</span></span>  
 <span data-ttu-id="c723b-127">Následující příklad ukazuje, jak <xref:System.Diagnostics.TraceLevel> použít `Data` `General`  **\<element Switch >** k nastavení přepínače trasování na úroveň a povolit logický trasovací přepínač.</span><span class="sxs-lookup"><span data-stu-id="c723b-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c723b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c723b-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="c723b-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="c723b-129">Trace and Debug Settings Schema</span></span>](index.md)
