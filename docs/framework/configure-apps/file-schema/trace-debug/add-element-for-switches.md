---
title: '&lt;Přidat&gt; – Element pro &lt;přepínače&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0a1a2c9ec34c43eb1b9559d90a8da0d70193c19e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109521"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="8c30d-102">&lt;Přidat&gt; – Element pro &lt;přepínače&gt;</span><span class="sxs-lookup"><span data-stu-id="8c30d-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="8c30d-103">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="8c30d-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="8c30d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8c30d-104">\<configuration></span></span>  
<span data-ttu-id="8c30d-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8c30d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8c30d-106">\<přepínače ></span><span class="sxs-lookup"><span data-stu-id="8c30d-106">\<switches></span></span>  
<span data-ttu-id="8c30d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="8c30d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c30d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c30d-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c30d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c30d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8c30d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c30d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c30d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c30d-111">Attributes</span></span>  
  
|<span data-ttu-id="8c30d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="8c30d-112">Attribute</span></span>|<span data-ttu-id="8c30d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8c30d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c30d-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="8c30d-114">**name**</span></span>|<span data-ttu-id="8c30d-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8c30d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="8c30d-116">Určuje název přepínače.</span><span class="sxs-lookup"><span data-stu-id="8c30d-116">Specifies the name of the switch.</span></span> <span data-ttu-id="8c30d-117">Hodnota tohoto atributu odpovídá *displayName* parametr, který je předán konstruktoru přepínat.</span><span class="sxs-lookup"><span data-stu-id="8c30d-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="8c30d-118">**value**</span><span class="sxs-lookup"><span data-stu-id="8c30d-118">**value**</span></span>|<span data-ttu-id="8c30d-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8c30d-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="8c30d-120">Určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="8c30d-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c30d-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c30d-121">Child Elements</span></span>  
 <span data-ttu-id="8c30d-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8c30d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c30d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c30d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8c30d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c30d-124">Element</span></span>|<span data-ttu-id="8c30d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8c30d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8c30d-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c30d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="8c30d-127">Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.</span><span class="sxs-lookup"><span data-stu-id="8c30d-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8c30d-128">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="8c30d-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c30d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c30d-129">Remarks</span></span>  
 <span data-ttu-id="8c30d-130">Úroveň trasování přepínače můžete změnit tak, že ji vložíte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="8c30d-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="8c30d-131">Pokud je v přepínači <xref:System.Diagnostics.BooleanSwitch>, můžete ji zapnout a vypnout.</span><span class="sxs-lookup"><span data-stu-id="8c30d-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="8c30d-132">Pokud je v přepínači <xref:System.Diagnostics.TraceSwitch>, můžete přiřadit různé úrovně možné určit typy trasování nebo zprávy ladění aplikace výstupy.</span><span class="sxs-lookup"><span data-stu-id="8c30d-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c30d-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c30d-133">Example</span></span>  
 <span data-ttu-id="8c30d-134">Následující příklad ukazuje způsob použití  **\<Přidat >** – element pro nastavení `General` přepínače trasování <xref:System.Diagnostics.TraceLevel> úrovně a povolit `Data` trasování logický přepínač.</span><span class="sxs-lookup"><span data-stu-id="8c30d-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c30d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c30d-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="8c30d-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="8c30d-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
