---
title: Element <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725bd715f6e70dff08929e58d588a3d8561d5011
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224231"
---
# <a name="netfx40pinvokestackresilience-element"></a><span data-ttu-id="c9548-102">\<Netfx40_pinvokestackresilience – > – Element</span><span class="sxs-lookup"><span data-stu-id="c9548-102">\<NetFx40_PInvokeStackResilience> Element</span></span>
<span data-ttu-id="c9548-103">Určuje, zda modul runtime automaticky opravy nesprávné volání nespravovaného kódu deklarace v době běhu, za cenu pomalejší přechody mezi spravováno a nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c9548-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="c9548-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c9548-104">\<configuration></span></span>  
<span data-ttu-id="c9548-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="c9548-105">\<runtime></span></span>  
<span data-ttu-id="c9548-106">< netfx40_pinvokestackresilience – ></span><span class="sxs-lookup"><span data-stu-id="c9548-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9548-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9548-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9548-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9548-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c9548-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9548-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9548-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9548-110">Attributes</span></span>  
  
|<span data-ttu-id="c9548-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c9548-111">Attribute</span></span>|<span data-ttu-id="c9548-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c9548-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c9548-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c9548-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9548-114">Určuje, zda modul runtime zjistí nesprávné platformu vyvolání deklarace a automaticky opravuje zásobníku za běhu na 32bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="c9548-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c9548-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="c9548-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c9548-116">Value</span><span class="sxs-lookup"><span data-stu-id="c9548-116">Value</span></span>|<span data-ttu-id="c9548-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c9548-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="c9548-118">Modul runtime používá rychlejší zprostředkovatele komunikace s objekty zařazování architektura zavedený [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], které není možné zjistit a oprava nesprávné volání nespravovaného kódu deklarace.</span><span class="sxs-lookup"><span data-stu-id="c9548-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="c9548-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="c9548-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="c9548-120">Modul runtime používá pomalejší přechody zjistit a opravit nesprávný platformu vyvolání deklarace.</span><span class="sxs-lookup"><span data-stu-id="c9548-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9548-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c9548-121">Child Elements</span></span>  
 <span data-ttu-id="c9548-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9548-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9548-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c9548-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c9548-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9548-124">Element</span></span>|<span data-ttu-id="c9548-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c9548-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9548-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9548-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c9548-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c9548-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9548-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9548-128">Remarks</span></span>  
 <span data-ttu-id="c9548-129">Tento prvek umožňuje obchodu rychlejší zařazování spolupráce pro za běhu odolnost proti nesprávné platformu vyvolání deklarace.</span><span class="sxs-lookup"><span data-stu-id="c9548-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="c9548-130">Počínaje [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], efektivní spolupráce zařazování architektura poskytuje významné výkonnostní zlepšení pro přechody ze spravovaného kódu do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c9548-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="c9548-131">V dřívějších verzích rozhraní .NET Framework zařazování vrstvy zjistil nesprávný platformu vyvolání deklarace na 32bitových platformách a automaticky opravit, zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c9548-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="c9548-132">Nová architektura zařazování eliminuje tento krok.</span><span class="sxs-lookup"><span data-stu-id="c9548-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="c9548-133">V důsledku toho přechody jsou velmi rychlé zpracování, ale nesprávné nespravovaného kódu deklarace může způsobit selhání programu.</span><span class="sxs-lookup"><span data-stu-id="c9548-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="c9548-134">Chcete-li snadno zjistit nesprávná deklarace během vývoje, jsme vylepšili ladění prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9548-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="c9548-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) pomocníka spravovaného ladění (MDA) upozorní nesprávné platformy vyvoláte deklarace když vaše aplikace běží s připojeným ladícím nástrojem.</span><span class="sxs-lookup"><span data-stu-id="c9548-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="c9548-136">K řešení scénářů, kde vaše aplikace používá komponenty, nelze znovu zkompilovat a, že máte nesprávné vyvolání platformy deklarace, můžete použít `NetFx40_PInvokeStackResilience` elementu.</span><span class="sxs-lookup"><span data-stu-id="c9548-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="c9548-137">Přidání tohoto prvku do konfiguračního souboru aplikace s `enabled="1"` požádá o do režimu kompatibility s chováním dřívějších verzích rozhraní .NET Framework za cenu pomalejší přechodů.</span><span class="sxs-lookup"><span data-stu-id="c9548-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="c9548-138">Sestavení, která byla zkompilována proti dřívějších verzích rozhraní .NET Framework, vyloučí se automaticky do tohoto režimu kompatibility a není nutné tento element.</span><span class="sxs-lookup"><span data-stu-id="c9548-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c9548-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="c9548-139">Configuration File</span></span>  
 <span data-ttu-id="c9548-140">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9548-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9548-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9548-141">Example</span></span>  
 <span data-ttu-id="c9548-142">Následující příklad ukazuje způsob, jakým do zvýšení odolnosti proti nesprávné vyvolání platformy deklarace pro aplikaci za cenu pomalejší přechody mezi spravovaného a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c9548-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9548-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9548-143">See also</span></span>

- [<span data-ttu-id="c9548-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="c9548-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="c9548-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c9548-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c9548-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="c9548-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
