---
title: <add> – element pro <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: d7500620aed1165ff365fee8529230ba252dbc4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120091"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="e3a45-102">\<Přidat > – Element pro \<přepínače ></span><span class="sxs-lookup"><span data-stu-id="e3a45-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="e3a45-103">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e3a45-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="e3a45-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e3a45-104">\<configuration></span></span>  
<span data-ttu-id="e3a45-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="e3a45-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e3a45-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="e3a45-106">\<switches></span></span>  
<span data-ttu-id="e3a45-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e3a45-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a45-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3a45-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3a45-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3a45-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e3a45-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3a45-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3a45-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3a45-111">Attributes</span></span>  
  
|<span data-ttu-id="e3a45-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e3a45-112">Attribute</span></span>|<span data-ttu-id="e3a45-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a45-113">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="e3a45-114">name</span><span class="sxs-lookup"><span data-stu-id="e3a45-114">name</span></span>**|<span data-ttu-id="e3a45-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e3a45-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3a45-116">Určuje název přepínače.</span><span class="sxs-lookup"><span data-stu-id="e3a45-116">Specifies the name of the switch.</span></span> <span data-ttu-id="e3a45-117">Hodnota tohoto atributu odpovídá *displayName* parametr, který je předán konstruktoru přepínat.</span><span class="sxs-lookup"><span data-stu-id="e3a45-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|**<span data-ttu-id="e3a45-118">value</span><span class="sxs-lookup"><span data-stu-id="e3a45-118">value</span></span>**|<span data-ttu-id="e3a45-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e3a45-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3a45-120">Určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="e3a45-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3a45-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e3a45-121">Child Elements</span></span>  
 <span data-ttu-id="e3a45-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="e3a45-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3a45-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e3a45-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e3a45-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3a45-124">Element</span></span>|<span data-ttu-id="e3a45-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e3a45-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e3a45-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3a45-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="e3a45-127">Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.</span><span class="sxs-lookup"><span data-stu-id="e3a45-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e3a45-128">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e3a45-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3a45-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3a45-129">Remarks</span></span>  
 <span data-ttu-id="e3a45-130">Úroveň trasování přepínače můžete změnit tak, že ji vložíte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="e3a45-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="e3a45-131">Pokud je v přepínači <xref:System.Diagnostics.BooleanSwitch>, můžete ji zapnout a vypnout.</span><span class="sxs-lookup"><span data-stu-id="e3a45-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="e3a45-132">Pokud je v přepínači <xref:System.Diagnostics.TraceSwitch>, můžete přiřadit různé úrovně možné určit typy trasování nebo zprávy ladění aplikace výstupy.</span><span class="sxs-lookup"><span data-stu-id="e3a45-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3a45-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3a45-133">Example</span></span>  
 <span data-ttu-id="e3a45-134">Následující příklad ukazuje způsob použití  **\<Přidat >** – element pro nastavení `General` přepínače trasování <xref:System.Diagnostics.TraceLevel> úrovně a povolit `Data` trasování logický přepínač.</span><span class="sxs-lookup"><span data-stu-id="e3a45-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3a45-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3a45-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="e3a45-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e3a45-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
