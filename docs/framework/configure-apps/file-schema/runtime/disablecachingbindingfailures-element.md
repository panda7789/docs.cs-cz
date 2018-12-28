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
ms.openlocfilehash: 78ca269dacc33fb441310ad00ba2548826f5403e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610512"
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a><span data-ttu-id="0c50e-102">&lt;disablecachingbindingfailures –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="0c50e-102">&lt;disableCachingBindingFailures&gt; Element</span></span>
<span data-ttu-id="0c50e-103">Určuje, zda chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="0c50e-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="0c50e-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="0c50e-104">\<configuration> Element</span></span>  
<span data-ttu-id="0c50e-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="0c50e-105">\<runtime> Element</span></span>  
<span data-ttu-id="0c50e-106">\<disablecachingbindingfailures – ></span><span class="sxs-lookup"><span data-stu-id="0c50e-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c50e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c50e-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c50e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0c50e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0c50e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0c50e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c50e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0c50e-110">Attributes</span></span>  
  
|<span data-ttu-id="0c50e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0c50e-111">Attribute</span></span>|<span data-ttu-id="0c50e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0c50e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c50e-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="0c50e-113">enabled</span></span>|<span data-ttu-id="0c50e-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0c50e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c50e-115">Určuje, zda chcete zakázat ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="0c50e-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0c50e-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0c50e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="0c50e-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0c50e-117">Value</span></span>|<span data-ttu-id="0c50e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0c50e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c50e-119">0</span><span class="sxs-lookup"><span data-stu-id="0c50e-119">0</span></span>|<span data-ttu-id="0c50e-120">Nezakazujte ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="0c50e-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="0c50e-121">Toto je výchozí chování vazby od verze rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="0c50e-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="0c50e-122">1</span><span class="sxs-lookup"><span data-stu-id="0c50e-122">1</span></span>|<span data-ttu-id="0c50e-123">Zakáže ukládání do mezipaměti vazby, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="0c50e-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="0c50e-124">Toto nastavení se vrátí k chování vazby rozhraní .NET Framework verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="0c50e-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c50e-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0c50e-125">Child Elements</span></span>  
 <span data-ttu-id="0c50e-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="0c50e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c50e-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0c50e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0c50e-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="0c50e-128">Element</span></span>|<span data-ttu-id="0c50e-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0c50e-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0c50e-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c50e-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0c50e-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0c50e-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c50e-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c50e-132">Remarks</span></span>  
 <span data-ttu-id="0c50e-133">Od verze rozhraní .NET Framework verze 2.0, je výchozí chování pro načtení sestavení do mezipaměti všechny vazby a načítání chyb.</span><span class="sxs-lookup"><span data-stu-id="0c50e-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="0c50e-134">To znamená pokud se nezdaří pokus o načtení sestavení, následné žádosti k načtení stejné sestavení selhala okamžitě, bez jakékoli pokusy o nalezení sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c50e-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="0c50e-135">Tento prvek zakazuje výchozí chování pro vazbu, ke kterým dochází, protože sestavení nebyl nalezen v cestě k testování.</span><span class="sxs-lookup"><span data-stu-id="0c50e-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="0c50e-136">Vyvolat tyto chyby <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="0c50e-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="0c50e-137">Některé vazby a načítání selhání nevztahují na tento element a jsou vždy uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="0c50e-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="0c50e-138">Tyto chyby dojít, protože sestavení nebyl nalezen, ale nelze jej načíst.</span><span class="sxs-lookup"><span data-stu-id="0c50e-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="0c50e-139">Generují výjimku <xref:System.BadImageFormatException> nebo <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="0c50e-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="0c50e-140">Následující seznam obsahuje několik příkladů takových selhání.</span><span class="sxs-lookup"><span data-stu-id="0c50e-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="0c50e-141">Při pokusu načíst soubor není platným sestavením, následné pokusy o načtení sestavení se nezdaří, i když chybný soubor nahradí správné sestavení.</span><span class="sxs-lookup"><span data-stu-id="0c50e-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="0c50e-142">Při pokusu o načtení sestavení, které je uzamčen systému souborů, následné pokusy o načtení sestavení se nezdaří, i po sestavení je vydáno systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="0c50e-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="0c50e-143">Pokud je jeden nebo více verzí sestavení, které se pokoušíte načíst v cesta zjišťování, ale konkrétní verzi, které jste požádali, není mezi nimi, následné pokusy načíst tuto verzi se nezdaří, i v případě, že správná verze je přesunut do cesta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="0c50e-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c50e-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c50e-144">Example</span></span>  
 <span data-ttu-id="0c50e-145">Následující příklad ukazuje, jak zakázat ukládání do mezipaměti selhání vazby sestavení, ke kterým dochází, protože nebylo nalezeno sestavení zjišťováním.</span><span class="sxs-lookup"><span data-stu-id="0c50e-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c50e-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c50e-146">See Also</span></span>  
- [<span data-ttu-id="0c50e-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0c50e-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="0c50e-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0c50e-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="0c50e-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="0c50e-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
