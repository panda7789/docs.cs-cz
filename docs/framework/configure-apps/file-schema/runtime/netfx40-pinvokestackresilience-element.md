---
title: Element <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116164"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="b18ac-102">Element \<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="b18ac-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="b18ac-103">Určuje, zda modul runtime automaticky opravuje nesprávné deklarace volání platformy za běhu, a to za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="b18ac-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="b18ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b18ac-104">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b18ac-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b18ac-105">Attributes and Elements</span></span>

<span data-ttu-id="b18ac-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b18ac-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b18ac-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b18ac-107">Attributes</span></span>

|<span data-ttu-id="b18ac-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b18ac-108">Attribute</span></span>|<span data-ttu-id="b18ac-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b18ac-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b18ac-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b18ac-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b18ac-111">Určuje, zda modul runtime detekuje nesprávné deklarace vyvolání platformy a automaticky opraví zásobník v době běhu na 32 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="b18ac-111">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="b18ac-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="b18ac-112">enabled Attribute</span></span>

|<span data-ttu-id="b18ac-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b18ac-113">Value</span></span>|<span data-ttu-id="b18ac-114">Description</span><span class="sxs-lookup"><span data-stu-id="b18ac-114">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="b18ac-115">Modul runtime používá rychlejší interop marshaling architekturu představenou v .NET Framework 4, která nedetekuje a neopravují nesprávné deklarace vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="b18ac-115">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="b18ac-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b18ac-116">This is the default.</span></span>|
|`1`|<span data-ttu-id="b18ac-117">Běhový modul používá pomalejší přechody, které zjišťují a opravují nesprávné deklarace vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="b18ac-117">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b18ac-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b18ac-118">Child Elements</span></span>

<span data-ttu-id="b18ac-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="b18ac-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b18ac-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b18ac-120">Parent Elements</span></span>

|<span data-ttu-id="b18ac-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="b18ac-121">Element</span></span>|<span data-ttu-id="b18ac-122">Description</span><span class="sxs-lookup"><span data-stu-id="b18ac-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b18ac-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b18ac-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b18ac-124">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b18ac-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b18ac-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b18ac-125">Remarks</span></span>

<span data-ttu-id="b18ac-126">Tento prvek umožňuje rychlejší obchodování interop marshaling pro odolnost za běhu proti nesprávným deklaracím vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="b18ac-126">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="b18ac-127">Počínaje .NET Framework 4 nabízí zjednodušená interop marshaling architektura výrazné zlepšení výkonu pro přechody ze spravovaného kódu do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b18ac-127">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="b18ac-128">V dřívějších verzích .NET Framework zařazovací vrstva zjistila nesprávnou deklaraci volání platformy na 32ch platformách a automaticky opravila zásobník.</span><span class="sxs-lookup"><span data-stu-id="b18ac-128">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="b18ac-129">Nová architektura zařazování eliminuje tento krok.</span><span class="sxs-lookup"><span data-stu-id="b18ac-129">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="b18ac-130">V důsledku toho jsou přechody velmi rychlé, ale nesprávná deklarace vyvolání platformy může způsobit selhání programu.</span><span class="sxs-lookup"><span data-stu-id="b18ac-130">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="b18ac-131">Aby bylo možné během vývoje snadno detekovat nesprávné deklarace, Vylepšili jsme prostředí pro ladění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b18ac-131">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="b18ac-132">Pomocník pro [pInvokeStackImbalance –](../../../debug-trace-profile/pinvokestackimbalance-mda.md) spravované ladění (MDA) vás upozorní na nesprávné deklarace vyvolání platformy, pokud je vaše aplikace spuštěná s připojeným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="b18ac-132">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="b18ac-133">Pro řešení scénářů, kde vaše aplikace používá komponenty, které nemůžete znovu kompilovat a které mají nesprávné deklarace vyvolání platformy, lze použít `NetFx40_PInvokeStackResilience` prvek.</span><span class="sxs-lookup"><span data-stu-id="b18ac-133">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="b18ac-134">Přidání tohoto elementu do konfiguračního souboru aplikace pomocí `enabled="1"` výslovný do režimu kompatibility s chováním dřívějších verzí .NET Framework, za cenu pomalejších přechodů.</span><span class="sxs-lookup"><span data-stu-id="b18ac-134">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="b18ac-135">Sestavení, která byla zkompilována v předchozích verzích .NET Framework, jsou automaticky přizpůsobena do tohoto režimu kompatibility a nepotřebují tento prvek.</span><span class="sxs-lookup"><span data-stu-id="b18ac-135">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="b18ac-136">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="b18ac-136">Configuration File</span></span>

<span data-ttu-id="b18ac-137">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b18ac-137">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="b18ac-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b18ac-138">Example</span></span>

<span data-ttu-id="b18ac-139">Následující příklad ukazuje, jak se vyjádřit ke zvýšené odolnosti proti nesprávným deklaracím vyvolání platformy pro aplikaci, za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="b18ac-139">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b18ac-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="b18ac-140">See also</span></span>

- [<span data-ttu-id="b18ac-141">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="b18ac-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b18ac-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b18ac-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b18ac-143">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="b18ac-143">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
