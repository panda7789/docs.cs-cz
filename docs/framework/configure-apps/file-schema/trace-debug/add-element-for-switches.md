---
title: <add> – element pro <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088959"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="51cf9-102">\<add> – element pro \<switches></span><span class="sxs-lookup"><span data-stu-id="51cf9-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="51cf9-103">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="51cf9-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="51cf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51cf9-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51cf9-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51cf9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="51cf9-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="51cf9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51cf9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="51cf9-107">Attributes</span></span>  
  
|<span data-ttu-id="51cf9-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="51cf9-108">Attribute</span></span>|<span data-ttu-id="51cf9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="51cf9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51cf9-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="51cf9-110">**name**</span></span>|<span data-ttu-id="51cf9-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="51cf9-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="51cf9-112">Určuje název přepínače.</span><span class="sxs-lookup"><span data-stu-id="51cf9-112">Specifies the name of the switch.</span></span> <span data-ttu-id="51cf9-113">Hodnota tohoto atributu odpovídá parametru *DisplayName* , který je předán konstruktoru Switch.</span><span class="sxs-lookup"><span data-stu-id="51cf9-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="51cf9-114">**osa**</span><span class="sxs-lookup"><span data-stu-id="51cf9-114">**value**</span></span>|<span data-ttu-id="51cf9-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="51cf9-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="51cf9-116">Určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="51cf9-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51cf9-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51cf9-117">Child Elements</span></span>  
 <span data-ttu-id="51cf9-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="51cf9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51cf9-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51cf9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="51cf9-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="51cf9-120">Element</span></span>|<span data-ttu-id="51cf9-121">Description</span><span class="sxs-lookup"><span data-stu-id="51cf9-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="51cf9-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51cf9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="51cf9-123">Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="51cf9-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="51cf9-124">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="51cf9-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51cf9-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51cf9-125">Remarks</span></span>  
 <span data-ttu-id="51cf9-126">Úroveň trasovacího přepínače můžete změnit tak, že ho umístíte do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="51cf9-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="51cf9-127">Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch> , můžete ho zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="51cf9-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="51cf9-128">Pokud je přepínač <xref:System.Diagnostics.TraceSwitch> , můžete k němu přiřadit různé úrovně, aby bylo možné určit typy trasování nebo ladění zpráv výstupem aplikace.</span><span class="sxs-lookup"><span data-stu-id="51cf9-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cf9-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="51cf9-129">Example</span></span>  
 <span data-ttu-id="51cf9-130">Následující příklad ukazuje, jak použít **\<add>** prvek pro nastavení `General` přepínače trasování na <xref:System.Diagnostics.TraceLevel> úroveň a povolení `Data` logického sledovacího přepínače.</span><span class="sxs-lookup"><span data-stu-id="51cf9-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51cf9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="51cf9-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="51cf9-132">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="51cf9-132">Trace and Debug Settings Schema</span></span>](index.md)
