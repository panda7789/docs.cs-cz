---
title: '&lt;Přidat&gt; – Element pro &lt;přepínače&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 3b15cd7759eb36f95b93f2885151e2f6075d92d9
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083337"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="c0491-102">&lt;Přidat&gt; – Element pro &lt;přepínače&gt;</span><span class="sxs-lookup"><span data-stu-id="c0491-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="c0491-103">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c0491-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="c0491-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c0491-104">\<configuration></span></span>  
<span data-ttu-id="c0491-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="c0491-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c0491-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="c0491-106">\<switches></span></span>  
<span data-ttu-id="c0491-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c0491-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0491-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0491-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0491-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0491-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c0491-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0491-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0491-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0491-111">Attributes</span></span>  
  
|<span data-ttu-id="c0491-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0491-112">Attribute</span></span>|<span data-ttu-id="c0491-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c0491-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0491-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="c0491-114">**name**</span></span>|<span data-ttu-id="c0491-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c0491-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0491-116">Určuje název přepínače.</span><span class="sxs-lookup"><span data-stu-id="c0491-116">Specifies the name of the switch.</span></span> <span data-ttu-id="c0491-117">Hodnota tohoto atributu odpovídá *displayName* parametr, který je předán konstruktoru přepínat.</span><span class="sxs-lookup"><span data-stu-id="c0491-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="c0491-118">**value**</span><span class="sxs-lookup"><span data-stu-id="c0491-118">**value**</span></span>|<span data-ttu-id="c0491-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c0491-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0491-120">Určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="c0491-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0491-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0491-121">Child Elements</span></span>  
 <span data-ttu-id="c0491-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0491-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0491-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0491-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c0491-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0491-124">Element</span></span>|<span data-ttu-id="c0491-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c0491-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c0491-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0491-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="c0491-127">Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.</span><span class="sxs-lookup"><span data-stu-id="c0491-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c0491-128">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c0491-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0491-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0491-129">Remarks</span></span>  
 <span data-ttu-id="c0491-130">Úroveň trasování přepínače můžete změnit tak, že ji vložíte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="c0491-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="c0491-131">Pokud je v přepínači <xref:System.Diagnostics.BooleanSwitch>, můžete ji zapnout a vypnout.</span><span class="sxs-lookup"><span data-stu-id="c0491-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="c0491-132">Pokud je v přepínači <xref:System.Diagnostics.TraceSwitch>, můžete přiřadit různé úrovně možné určit typy trasování nebo zprávy ladění aplikace výstupy.</span><span class="sxs-lookup"><span data-stu-id="c0491-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0491-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0491-133">Example</span></span>  
 <span data-ttu-id="c0491-134">Následující příklad ukazuje způsob použití  **\<Přidat >** – element pro nastavení `General` přepínače trasování <xref:System.Diagnostics.TraceLevel> úrovně a povolit `Data` trasování logický přepínač.</span><span class="sxs-lookup"><span data-stu-id="c0491-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0491-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0491-135">See also</span></span>
- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="c0491-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="c0491-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
