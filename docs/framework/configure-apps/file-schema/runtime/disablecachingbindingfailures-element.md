---
title: Element <disableCachingBindingFailures>
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
ms.openlocfilehash: ba74907e2f6fc2ca14e12a24113fa7654c9b967e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663801"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="04407-102">\<disableCachingBindingFailures> Element</span><span class="sxs-lookup"><span data-stu-id="04407-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="04407-103">Určuje, jestli se má zakázat ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="04407-104">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="04407-104">\<configuration> Element</span></span>  
<span data-ttu-id="04407-105">\<Běhový > element</span><span class="sxs-lookup"><span data-stu-id="04407-105">\<runtime> Element</span></span>  
<span data-ttu-id="04407-106">\<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="04407-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04407-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04407-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04407-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04407-108">Attributes and Elements</span></span>  
 <span data-ttu-id="04407-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04407-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04407-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="04407-110">Attributes</span></span>  
  
|<span data-ttu-id="04407-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="04407-111">Attribute</span></span>|<span data-ttu-id="04407-112">Popis</span><span class="sxs-lookup"><span data-stu-id="04407-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04407-113">enabled</span><span class="sxs-lookup"><span data-stu-id="04407-113">enabled</span></span>|<span data-ttu-id="04407-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="04407-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="04407-115">Určuje, jestli se má zakázat ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="04407-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="04407-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="04407-117">Value</span><span class="sxs-lookup"><span data-stu-id="04407-117">Value</span></span>|<span data-ttu-id="04407-118">Popis</span><span class="sxs-lookup"><span data-stu-id="04407-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04407-119">0</span><span class="sxs-lookup"><span data-stu-id="04407-119">0</span></span>|<span data-ttu-id="04407-120">Nepovolujte ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="04407-121">Toto je výchozí chování vazby počínaje .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="04407-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="04407-122">1</span><span class="sxs-lookup"><span data-stu-id="04407-122">1</span></span>|<span data-ttu-id="04407-123">Zakáže ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="04407-124">Toto nastavení se vrátí k chování vazby .NET Framework verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="04407-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04407-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04407-125">Child Elements</span></span>  
 <span data-ttu-id="04407-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="04407-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04407-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04407-127">Parent Elements</span></span>  
  
|<span data-ttu-id="04407-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="04407-128">Element</span></span>|<span data-ttu-id="04407-129">Popis</span><span class="sxs-lookup"><span data-stu-id="04407-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="04407-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04407-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="04407-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="04407-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04407-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04407-132">Remarks</span></span>  
 <span data-ttu-id="04407-133">.NET Framework počínaje verzí 2,0 je výchozím chováním při načítání sestavení ukládání do mezipaměti všech vazeb a selhání načítání.</span><span class="sxs-lookup"><span data-stu-id="04407-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="04407-134">To znamená, že pokud se pokus o načtení sestavení nezdaří, následné požadavky na načtení stejného sestavení okamžitě selžou bez nutnosti najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="04407-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="04407-135">Tento prvek zakáže toto výchozí chování pro chyby vazby, ke kterým dojde, protože sestavení nebylo nalezeno v cestě zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="04407-136">Tyto chyby vyvolávají <xref:System.IO.FileNotFoundException>vyvolání.</span><span class="sxs-lookup"><span data-stu-id="04407-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="04407-137">Některá vazba a selhání načítání nejsou ovlivněny tímto elementem a jsou vždy ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="04407-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="04407-138">K těmto selháním dochází, protože bylo nalezeno sestavení, ale nebylo možné ho načíst.</span><span class="sxs-lookup"><span data-stu-id="04407-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="04407-139">Vyvolávají <xref:System.BadImageFormatException> nebo .<xref:System.IO.FileLoadException></span><span class="sxs-lookup"><span data-stu-id="04407-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="04407-140">Následující seznam obsahuje některé příklady takových selhání.</span><span class="sxs-lookup"><span data-stu-id="04407-140">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="04407-141">Pokud se pokusíte načíst soubor není platným sestavením, následné pokusy o načtení sestavení selžou i v případě, že je chybný soubor nahrazen správným sestavením.</span><span class="sxs-lookup"><span data-stu-id="04407-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="04407-142">Pokud se pokusíte načíst sestavení, které je uzamčeno systémem souborů, následné pokusy o načtení sestavení selžou i poté, co je sestavení uvolněno systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="04407-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="04407-143">Pokud je jedna nebo více verzí sestavení, které se pokoušíte načíst, v cestě zjišťování, ale konkrétní verze, kterou požadujete, není mimo ně, následné pokusy o načtení této verze selžou, i když je správná verze přesunuta do cesty pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04407-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="04407-144">Example</span></span>  
 <span data-ttu-id="04407-145">Následující příklad ukazuje, jak zakázat ukládání neúspěšných vazeb sestavení do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="04407-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04407-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04407-146">See also</span></span>

- [<span data-ttu-id="04407-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="04407-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="04407-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="04407-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="04407-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="04407-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
