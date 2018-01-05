---
title: "&lt;Netfx40_pinvokestackresilience –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17816ee6134dc6b3074256093c0cba07419baf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a><span data-ttu-id="584e7-102">&lt;Netfx40_pinvokestackresilience –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="584e7-102">&lt;NetFx40_PInvokeStackResilience&gt; Element</span></span>
<span data-ttu-id="584e7-103">Určuje, zda modul runtime automaticky opravy vyvolání nesprávný platformy deklarace v době běhu za cenu pomalejší přechodů mezi spravováno a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="584e7-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="584e7-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="584e7-104">\<configuration></span></span>  
<span data-ttu-id="584e7-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="584e7-105">\<runtime></span></span>  
<span data-ttu-id="584e7-106">< netfx40_pinvokestackresilience – ></span><span class="sxs-lookup"><span data-stu-id="584e7-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="584e7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="584e7-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="584e7-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="584e7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="584e7-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="584e7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="584e7-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="584e7-110">Attributes</span></span>  
  
|<span data-ttu-id="584e7-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="584e7-111">Attribute</span></span>|<span data-ttu-id="584e7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="584e7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="584e7-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="584e7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="584e7-114">Určuje, zda modul runtime zjistí nesprávné platformy vyvolání deklarace a automaticky opravuje zásobníku v době běhu na 32bitové platformy.</span><span class="sxs-lookup"><span data-stu-id="584e7-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="584e7-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="584e7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="584e7-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="584e7-116">Value</span></span>|<span data-ttu-id="584e7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="584e7-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="584e7-118">Modul runtime používá rychlejší zprostředkovatel komunikace s objekty zařazování architektura počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], který nerozpozná a vyvolání platformy nesprávný oprava deklarace.</span><span class="sxs-lookup"><span data-stu-id="584e7-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="584e7-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="584e7-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="584e7-120">Přechody pomalejší runtime používá, které zjistit a opravit nesprávné platformy vyvolání deklarace.</span><span class="sxs-lookup"><span data-stu-id="584e7-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="584e7-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="584e7-121">Child Elements</span></span>  
 <span data-ttu-id="584e7-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="584e7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="584e7-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="584e7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="584e7-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="584e7-124">Element</span></span>|<span data-ttu-id="584e7-125">Popis</span><span class="sxs-lookup"><span data-stu-id="584e7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="584e7-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="584e7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="584e7-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="584e7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="584e7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="584e7-128">Remarks</span></span>  
 <span data-ttu-id="584e7-129">Tento element umožňuje rychlejší zařazování spolupráce pro spuštění odolnost proti nesprávný platformy vyvolání deklarace obchodu.</span><span class="sxs-lookup"><span data-stu-id="584e7-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="584e7-130">Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], poskytuje zjednodušenou interoperabilita zařazování architektura zlepšení výkonu pro přechody ze spravovaného kódu na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="584e7-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="584e7-131">V dřívějších verzích rozhraní .NET Framework zařazování vrstvy zjistila Nesprávná platforma vyvolání deklarace na platformách 32bitová verze a automaticky napravení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="584e7-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="584e7-132">Nové architektury zařazování eliminuje tento krok.</span><span class="sxs-lookup"><span data-stu-id="584e7-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="584e7-133">V důsledku toho jsou velmi rychlé přechody, ale nesprávný platformy vyvolání deklarace může způsobit selhání programu.</span><span class="sxs-lookup"><span data-stu-id="584e7-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="584e7-134">Chcete-li snadno rozpoznat nesprávné prohlášení během vývoje, bylo vylepšeno ladění prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="584e7-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="584e7-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Pomocník spravovaného ladění (MDA) upozorní nesprávný platformy vyvolání deklarace když aplikace běží s ladicím programem připojen.</span><span class="sxs-lookup"><span data-stu-id="584e7-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="584e7-136">Adresa scénářů, kde vaše aplikace používá komponenty nelze znovu zkompiluje, a že jste nesprávný vyvolání platformy deklarace, můžete použít `NetFx40_PInvokeStackResilience` elementu.</span><span class="sxs-lookup"><span data-stu-id="584e7-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="584e7-137">Přidání tohoto prvku do konfiguračního souboru aplikace s `enabled="1"` požádá do režimu kompatibility s chováním starší verze rozhraní .NET Framework za cenu přechody pomalejší.</span><span class="sxs-lookup"><span data-stu-id="584e7-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="584e7-138">Sestavení, které sestavili jsme pro starší verze rozhraní .NET Framework se automaticky vyjádřit výslovný souhlas do tohoto režimu kompatibility a není nutné tento element.</span><span class="sxs-lookup"><span data-stu-id="584e7-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="584e7-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="584e7-139">Configuration File</span></span>  
 <span data-ttu-id="584e7-140">Tento element může použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="584e7-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="584e7-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="584e7-141">Example</span></span>  
 <span data-ttu-id="584e7-142">Následující příklad ukazuje způsob, který se přidá do Zvýšená odolnost proti nesprávný vyvolání platformy deklarace pro aplikaci za cenu pomalejší přechodů mezi spravovaných a nespravovaných kódu.</span><span class="sxs-lookup"><span data-stu-id="584e7-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="584e7-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="584e7-143">See Also</span></span>  
 [<span data-ttu-id="584e7-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="584e7-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="584e7-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="584e7-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="584e7-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="584e7-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
