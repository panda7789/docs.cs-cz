---
title: "&lt;Přidat&gt; Element pro &lt;přepínače&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4406caa4da1375bea9809843ca96774e24421d5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="7e029-102">&lt;Přidat&gt; Element pro &lt;přepínače&gt;</span><span class="sxs-lookup"><span data-stu-id="7e029-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="7e029-103">Určuje úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="7e029-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="7e029-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="7e029-104">\<configuration></span></span>  
<span data-ttu-id="7e029-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="7e029-105">\<system.diagnostics></span></span>  
<span data-ttu-id="7e029-106">\<přepínače ></span><span class="sxs-lookup"><span data-stu-id="7e029-106">\<switches></span></span>  
<span data-ttu-id="7e029-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="7e029-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e029-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e029-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e029-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e029-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7e029-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e029-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e029-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e029-111">Attributes</span></span>  
  
|<span data-ttu-id="7e029-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="7e029-112">Attribute</span></span>|<span data-ttu-id="7e029-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7e029-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e029-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="7e029-114">**name**</span></span>|<span data-ttu-id="7e029-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7e029-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="7e029-116">Určuje název přepínače.</span><span class="sxs-lookup"><span data-stu-id="7e029-116">Specifies the name of the switch.</span></span> <span data-ttu-id="7e029-117">Hodnota tohoto atributu odpovídá *displayName* parametr, který je předán přepínač konstruktor.</span><span class="sxs-lookup"><span data-stu-id="7e029-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="7e029-118">**value**</span><span class="sxs-lookup"><span data-stu-id="7e029-118">**value**</span></span>|<span data-ttu-id="7e029-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7e029-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="7e029-120">Určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="7e029-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e029-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7e029-121">Child Elements</span></span>  
 <span data-ttu-id="7e029-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="7e029-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e029-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7e029-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7e029-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e029-124">Element</span></span>|<span data-ttu-id="7e029-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7e029-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7e029-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7e029-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="7e029-127">Obsahuje trasování – přepínače a úroveň, kde jsou nastaveny trasování – přepínače.</span><span class="sxs-lookup"><span data-stu-id="7e029-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7e029-128">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="7e029-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e029-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e029-129">Remarks</span></span>  
 <span data-ttu-id="7e029-130">Úroveň trasování přepínače můžete změnit umístěním v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="7e029-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="7e029-131">Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch>, můžete ho zapnout a vypnout.</span><span class="sxs-lookup"><span data-stu-id="7e029-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="7e029-132">Pokud je přepínač <xref:System.Diagnostics.TraceSwitch>, můžete přiřadit různé úrovně ji určit typy trasování nebo ladění zprávy výstupy aplikace.</span><span class="sxs-lookup"><span data-stu-id="7e029-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e029-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e029-133">Example</span></span>  
 <span data-ttu-id="7e029-134">Následující příklad ukazuje, jak používat  **\<Přidat >** elementu, který chcete nastavit `General` trasování přepínač tak, aby <xref:System.Diagnostics.TraceLevel> úrovni a povolit `Data` trasování logický přepínač.</span><span class="sxs-lookup"><span data-stu-id="7e029-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e029-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e029-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="7e029-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="7e029-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
