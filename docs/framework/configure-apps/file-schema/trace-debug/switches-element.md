---
title: "&lt;přepínače&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64cf3ba9e5529c4a46b2d5365931a47ad2ab211a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="2809b-102">&lt;přepínače&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="2809b-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="2809b-103">Obsahuje trasování – přepínače a úroveň, kde jsou nastaveny trasování – přepínače.</span><span class="sxs-lookup"><span data-stu-id="2809b-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="2809b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2809b-104">\<configuration></span></span>  
<span data-ttu-id="2809b-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="2809b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2809b-106">\<přepínače ></span><span class="sxs-lookup"><span data-stu-id="2809b-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2809b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2809b-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2809b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2809b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2809b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2809b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2809b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2809b-110">Attributes</span></span>  
 <span data-ttu-id="2809b-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="2809b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2809b-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2809b-112">Child Elements</span></span>  
  
|<span data-ttu-id="2809b-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="2809b-113">Element</span></span>|<span data-ttu-id="2809b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2809b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2809b-115">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="2809b-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="2809b-116">Určuje úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="2809b-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2809b-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2809b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2809b-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2809b-118">Element</span></span>|<span data-ttu-id="2809b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2809b-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2809b-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2809b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="2809b-121">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="2809b-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2809b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2809b-122">Remarks</span></span>  
 <span data-ttu-id="2809b-123">Úroveň trasování přepínače můžete změnit umístěním v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2809b-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="2809b-124">Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch>, můžete ho zapnout a vypnout.</span><span class="sxs-lookup"><span data-stu-id="2809b-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="2809b-125">Pokud je přepínač <xref:System.Diagnostics.TraceSwitch>, můžete přiřadit různé úrovně ji určit typy trasování nebo ladění zprávy výstupy aplikace.</span><span class="sxs-lookup"><span data-stu-id="2809b-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2809b-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="2809b-126">Example</span></span>  
 <span data-ttu-id="2809b-127">Následující příklad ukazuje, jak používat  **\<přepínač >** elementu, který chcete nastavit `General` trasování přepínač tak, aby <xref:System.Diagnostics.TraceLevel> úrovni a povolit `Data` trasování logický přepínač.</span><span class="sxs-lookup"><span data-stu-id="2809b-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2809b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2809b-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="2809b-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="2809b-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
