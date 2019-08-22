---
title: Element <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf97cc1ec544c7cf640c43b1b45760fca8cffe89
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663546"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="bb909-102">\<NetFx40_PInvokeStackResilience – element ></span><span class="sxs-lookup"><span data-stu-id="bb909-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="bb909-103">Určuje, zda modul runtime automaticky opravuje nesprávné deklarace volání platformy za běhu, a to za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="bb909-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="bb909-104">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="bb909-104">\<configuration></span></span>\
<span data-ttu-id="bb909-105">\<běhové > </span><span class="sxs-lookup"><span data-stu-id="bb909-105">\<runtime></span></span>\
<span data-ttu-id="bb909-106">\<NetFx40_PInvokeStackResilience ></span><span class="sxs-lookup"><span data-stu-id="bb909-106">\<NetFx40_PInvokeStackResilience></span></span>

## <a name="syntax"></a><span data-ttu-id="bb909-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb909-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb909-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bb909-108">Attributes and Elements</span></span>

<span data-ttu-id="bb909-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bb909-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb909-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb909-110">Attributes</span></span>

|<span data-ttu-id="bb909-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="bb909-111">Attribute</span></span>|<span data-ttu-id="bb909-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bb909-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="bb909-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bb909-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bb909-114">Určuje, zda modul runtime detekuje nesprávné deklarace vyvolání platformy a automaticky opraví zásobník v době běhu na 32 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="bb909-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="bb909-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="bb909-115">enabled Attribute</span></span>

|<span data-ttu-id="bb909-116">Value</span><span class="sxs-lookup"><span data-stu-id="bb909-116">Value</span></span>|<span data-ttu-id="bb909-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bb909-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="bb909-118">Modul runtime používá rychlejší interop marshaling architekturu představenou v .NET Framework 4, která nedetekuje a neopravují nesprávné deklarace vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="bb909-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="bb909-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="bb909-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="bb909-120">Běhový modul používá pomalejší přechody, které zjišťují a opravují nesprávné deklarace vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="bb909-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bb909-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bb909-121">Child Elements</span></span>

<span data-ttu-id="bb909-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="bb909-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bb909-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bb909-123">Parent Elements</span></span>

|<span data-ttu-id="bb909-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb909-124">Element</span></span>|<span data-ttu-id="bb909-125">Popis</span><span class="sxs-lookup"><span data-stu-id="bb909-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="bb909-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb909-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="bb909-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bb909-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb909-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb909-128">Remarks</span></span>

<span data-ttu-id="bb909-129">Tento prvek umožňuje rychlejší obchodování interop marshaling pro odolnost za běhu proti nesprávným deklaracím vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="bb909-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="bb909-130">Počínaje .NET Framework 4 nabízí zjednodušená interop marshaling architektura výrazné zlepšení výkonu pro přechody ze spravovaného kódu do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="bb909-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="bb909-131">V dřívějších verzích .NET Framework zařazovací vrstva zjistila nesprávnou deklaraci volání platformy na 32ch platformách a automaticky opravila zásobník.</span><span class="sxs-lookup"><span data-stu-id="bb909-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="bb909-132">Nová architektura zařazování eliminuje tento krok.</span><span class="sxs-lookup"><span data-stu-id="bb909-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="bb909-133">V důsledku toho jsou přechody velmi rychlé, ale nesprávná deklarace vyvolání platformy může způsobit selhání programu.</span><span class="sxs-lookup"><span data-stu-id="bb909-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="bb909-134">Aby bylo možné během vývoje snadno detekovat nesprávné deklarace, Vylepšili jsme prostředí pro ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb909-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="bb909-135">Pomocník pro [pInvokeStackImbalance –](../../../debug-trace-profile/pinvokestackimbalance-mda.md) spravované ladění (MDA) vás upozorní na nesprávné deklarace vyvolání platformy, pokud je vaše aplikace spuštěná s připojeným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="bb909-135">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="bb909-136">Pro řešení scénářů, kde vaše aplikace používá komponenty, které nemůžete znovu kompilovat a které mají nesprávné deklarace vyvolání platformy, lze `NetFx40_PInvokeStackResilience` použít prvek.</span><span class="sxs-lookup"><span data-stu-id="bb909-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="bb909-137">Přidání tohoto elementu do konfiguračního souboru aplikace pomocí `enabled="1"` výslovný do režimu kompatibility s chováním dřívějších verzí .NET Framework, za cenu pomalejších přechodů.</span><span class="sxs-lookup"><span data-stu-id="bb909-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="bb909-138">Sestavení, která byla zkompilována v předchozích verzích .NET Framework, jsou automaticky přizpůsobena do tohoto režimu kompatibility a nepotřebují tento prvek.</span><span class="sxs-lookup"><span data-stu-id="bb909-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="bb909-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="bb909-139">Configuration File</span></span>

<span data-ttu-id="bb909-140">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb909-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="bb909-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb909-141">Example</span></span>

<span data-ttu-id="bb909-142">Následující příklad ukazuje, jak se vyjádřit ke zvýšené odolnosti proti nesprávným deklaracím vyvolání platformy pro aplikaci, za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="bb909-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bb909-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb909-143">See also</span></span>

- [<span data-ttu-id="bb909-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="bb909-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bb909-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="bb909-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bb909-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="bb909-146">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
