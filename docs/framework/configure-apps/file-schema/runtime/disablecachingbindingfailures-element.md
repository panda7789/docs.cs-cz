---
title: '&lt;disablecachingbindingfailures –&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422888a595e8fdea01f9cb9d256830467d6822ac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a><span data-ttu-id="d6646-102">&lt;disablecachingbindingfailures –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="d6646-102">&lt;disableCachingBindingFailures&gt; Element</span></span>
<span data-ttu-id="d6646-103">Určuje, jestli chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen ve zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d6646-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="d6646-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="d6646-104">\<configuration> Element</span></span>  
<span data-ttu-id="d6646-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="d6646-105">\<runtime> Element</span></span>  
<span data-ttu-id="d6646-106">\<disablecachingbindingfailures – ></span><span class="sxs-lookup"><span data-stu-id="d6646-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6646-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6646-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6646-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6646-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d6646-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6646-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6646-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6646-110">Attributes</span></span>  
  
|<span data-ttu-id="d6646-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6646-111">Attribute</span></span>|<span data-ttu-id="d6646-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d6646-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6646-113">povoleno</span><span class="sxs-lookup"><span data-stu-id="d6646-113">enabled</span></span>|<span data-ttu-id="d6646-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d6646-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d6646-115">Určuje, jestli chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen ve zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d6646-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d6646-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d6646-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="d6646-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d6646-117">Value</span></span>|<span data-ttu-id="d6646-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d6646-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6646-119">0</span><span class="sxs-lookup"><span data-stu-id="d6646-119">0</span></span>|<span data-ttu-id="d6646-120">Nezakazujte ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d6646-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="d6646-121">Toto je výchozí chování vazby od verze rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d6646-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="d6646-122">1</span><span class="sxs-lookup"><span data-stu-id="d6646-122">1</span></span>|<span data-ttu-id="d6646-123">Zakážete ukládání do mezipaměti vazby, ke kterým dochází, protože sestavení nebyl nalezen pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d6646-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="d6646-124">Toto nastavení se vrátí do chování vazby rozhraní .NET Framework verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="d6646-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6646-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6646-125">Child Elements</span></span>  
 <span data-ttu-id="d6646-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6646-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6646-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6646-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d6646-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6646-128">Element</span></span>|<span data-ttu-id="d6646-129">Popis</span><span class="sxs-lookup"><span data-stu-id="d6646-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d6646-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6646-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d6646-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6646-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6646-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6646-132">Remarks</span></span>  
 <span data-ttu-id="d6646-133">Od verze rozhraní .NET Framework verze 2.0, je výchozí chování pro načtení sestavení do mezipaměti všechny vazby a načítání selhání.</span><span class="sxs-lookup"><span data-stu-id="d6646-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="d6646-134">To znamená pokud se nezdaří pokus o načtení sestavení, další žádost o načtení do stejného sestavení nezdaří okamžitě, bez jakékoli pokus o vyhledání sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6646-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="d6646-135">Tento element zakáže výchozí chování pro vazby, ke kterým dochází, protože sestavení nebyl nalezen v cestě k testování.</span><span class="sxs-lookup"><span data-stu-id="d6646-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="d6646-136">Throw – selhání <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="d6646-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="d6646-137">Některé vazby a načítání selhání nemá vliv tohoto elementu a vždy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d6646-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="d6646-138">Selhání dojít, protože sestavení nebyl nalezen, ale nebylo možné načíst.</span><span class="sxs-lookup"><span data-stu-id="d6646-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="d6646-139">Vyvolají <xref:System.BadImageFormatException> nebo <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="d6646-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="d6646-140">Následující seznam obsahuje některé příklady takových selhání.</span><span class="sxs-lookup"><span data-stu-id="d6646-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="d6646-141">Když se pokusí načíst soubor není platným sestavením, následných pokusů o načtení sestavení selže i v případě chybného souboru se nahradí správná sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6646-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="d6646-142">Při pokusu o načtení sestavení, které je uzamčený systému souborů následné pokusy o načtení sestavení selže i po vydání sestavení pomocí systému souborů.</span><span class="sxs-lookup"><span data-stu-id="d6646-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="d6646-143">Pokud je jeden nebo více verzí sestavení, které se pokoušíte načíst v cestě k testování, ale není mezi nimi konkrétní verzi, kterou jste požádali, následné pokusy o spouštění této verze selže i v případě správnou verzi přesunete do testování cestu.</span><span class="sxs-lookup"><span data-stu-id="d6646-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6646-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6646-144">Example</span></span>  
 <span data-ttu-id="d6646-145">Následující příklad ukazuje, jak zakázat ukládání do mezipaměti selhání vazby sestavení, ke kterým dochází, protože sestavení nebyl nalezen pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="d6646-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6646-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6646-146">See Also</span></span>  
 [<span data-ttu-id="d6646-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d6646-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d6646-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d6646-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d6646-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d6646-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
