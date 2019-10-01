---
title: <add> – element pro <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 2edc890049d62913d693ad61d8d814d012c0f482
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697182"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="6e231-102">> element \<add pro \<switches ></span><span class="sxs-lookup"><span data-stu-id="6e231-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="6e231-103">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="6e231-103">Specifies the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="6e231-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="6e231-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6e231-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e231-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="6e231-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<switches >** ](switches-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e231-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>  
<span data-ttu-id="6e231-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="6e231-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e231-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e231-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e231-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e231-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6e231-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e231-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e231-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e231-111">Attributes</span></span>  
  
|<span data-ttu-id="6e231-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6e231-112">Attribute</span></span>|<span data-ttu-id="6e231-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6e231-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e231-114">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="6e231-114">**name**</span></span>|<span data-ttu-id="6e231-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6e231-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e231-116">Určuje název přepínače.</span><span class="sxs-lookup"><span data-stu-id="6e231-116">Specifies the name of the switch.</span></span> <span data-ttu-id="6e231-117">Hodnota tohoto atributu odpovídá parametru *DisplayName* , který je předán konstruktoru Switch.</span><span class="sxs-lookup"><span data-stu-id="6e231-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="6e231-118">**value**</span><span class="sxs-lookup"><span data-stu-id="6e231-118">**value**</span></span>|<span data-ttu-id="6e231-119">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6e231-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e231-120">Určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="6e231-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e231-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6e231-121">Child Elements</span></span>  
 <span data-ttu-id="6e231-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e231-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e231-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6e231-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e231-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e231-124">Element</span></span>|<span data-ttu-id="6e231-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6e231-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6e231-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e231-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="6e231-127">Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="6e231-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6e231-128">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="6e231-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e231-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e231-129">Remarks</span></span>  
 <span data-ttu-id="6e231-130">Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6e231-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="6e231-131">Pokud je přepínačem <xref:System.Diagnostics.BooleanSwitch>, můžete ho zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="6e231-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="6e231-132">Pokud je přepínačem <xref:System.Diagnostics.TraceSwitch>, můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv pro výstup aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e231-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e231-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e231-133">Example</span></span>  
 <span data-ttu-id="6e231-134">Následující příklad ukazuje, jak použít > prvek **\<add** k nastavení sledovacího přepínačů `General` na úroveň <xref:System.Diagnostics.TraceLevel> a povolení logického přepínače `Data`.</span><span class="sxs-lookup"><span data-stu-id="6e231-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e231-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e231-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="6e231-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="6e231-136">Trace and Debug Settings Schema</span></span>](index.md)
