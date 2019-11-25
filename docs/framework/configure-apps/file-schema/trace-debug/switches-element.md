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
ms.openlocfilehash: 4aeb3cb0cd75f0fb27e3b359b86da61a77b491c7
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088803"
---
# <a name="switches-element"></a><span data-ttu-id="43554-102">\<přepínače > elementu</span><span class="sxs-lookup"><span data-stu-id="43554-102">\<switches> Element</span></span>
<span data-ttu-id="43554-103">Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="43554-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="43554-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="43554-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43554-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="43554-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="43554-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<přepínače >**</span><span class="sxs-lookup"><span data-stu-id="43554-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="43554-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43554-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43554-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43554-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43554-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43554-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43554-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="43554-110">Attributes</span></span>  
 <span data-ttu-id="43554-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="43554-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43554-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43554-112">Child Elements</span></span>  
  
|<span data-ttu-id="43554-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="43554-113">Element</span></span>|<span data-ttu-id="43554-114">Popis</span><span class="sxs-lookup"><span data-stu-id="43554-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43554-115">\<přidat ></span><span class="sxs-lookup"><span data-stu-id="43554-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="43554-116">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="43554-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43554-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43554-117">Parent Elements</span></span>  
  
|<span data-ttu-id="43554-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="43554-118">Element</span></span>|<span data-ttu-id="43554-119">Popis</span><span class="sxs-lookup"><span data-stu-id="43554-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43554-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43554-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="43554-121">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="43554-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43554-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43554-122">Remarks</span></span>  
 <span data-ttu-id="43554-123">Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="43554-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="43554-124">Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch>, můžete ho zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="43554-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="43554-125">Pokud je přepínač <xref:System.Diagnostics.TraceSwitch>, můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv pro výstup aplikace.</span><span class="sxs-lookup"><span data-stu-id="43554-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43554-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="43554-126">Example</span></span>  
 <span data-ttu-id="43554-127">Následující příklad ukazuje, jak použít **\<přepínač >** elementu k nastavení `General`ho přepínače trasování na úroveň <xref:System.Diagnostics.TraceLevel> a povolení přepínače trasování `Data` Boolean.</span><span class="sxs-lookup"><span data-stu-id="43554-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43554-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43554-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="43554-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="43554-129">Trace and Debug Settings Schema</span></span>](index.md)
