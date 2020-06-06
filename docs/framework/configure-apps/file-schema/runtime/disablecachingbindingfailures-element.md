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
ms.openlocfilehash: 23633cb282b8e59b4df4bcc2cd38717d805a207e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117501"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="5cff3-102">Element \<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="5cff3-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="5cff3-103">Určuje, jestli se má zakázat ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="5cff3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cff3-104">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cff3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5cff3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5cff3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5cff3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cff3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="5cff3-107">Attributes</span></span>  
  
|<span data-ttu-id="5cff3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="5cff3-108">Attribute</span></span>|<span data-ttu-id="5cff3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5cff3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5cff3-110">enabled</span><span class="sxs-lookup"><span data-stu-id="5cff3-110">enabled</span></span>|<span data-ttu-id="5cff3-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5cff3-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="5cff3-112">Určuje, jestli se má zakázat ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-112">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5cff3-113">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="5cff3-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="5cff3-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5cff3-114">Value</span></span>|<span data-ttu-id="5cff3-115">Description</span><span class="sxs-lookup"><span data-stu-id="5cff3-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5cff3-116">0</span><span class="sxs-lookup"><span data-stu-id="5cff3-116">0</span></span>|<span data-ttu-id="5cff3-117">Nepovolujte ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-117">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="5cff3-118">Toto je výchozí chování vazby počínaje .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="5cff3-118">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="5cff3-119">1</span><span class="sxs-lookup"><span data-stu-id="5cff3-119">1</span></span>|<span data-ttu-id="5cff3-120">Zakáže ukládání vazeb do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-120">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="5cff3-121">Toto nastavení se vrátí k chování vazby .NET Framework verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="5cff3-121">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cff3-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5cff3-122">Child Elements</span></span>  
 <span data-ttu-id="5cff3-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="5cff3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cff3-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5cff3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5cff3-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="5cff3-125">Element</span></span>|<span data-ttu-id="5cff3-126">Description</span><span class="sxs-lookup"><span data-stu-id="5cff3-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5cff3-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5cff3-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5cff3-128">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5cff3-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cff3-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cff3-129">Remarks</span></span>  
 <span data-ttu-id="5cff3-130">.NET Framework počínaje verzí 2,0 je výchozím chováním při načítání sestavení ukládání do mezipaměti všech vazeb a selhání načítání.</span><span class="sxs-lookup"><span data-stu-id="5cff3-130">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="5cff3-131">To znamená, že pokud se pokus o načtení sestavení nezdaří, následné požadavky na načtení stejného sestavení okamžitě selžou bez nutnosti najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="5cff3-131">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="5cff3-132">Tento prvek zakáže toto výchozí chování pro chyby vazby, ke kterým dojde, protože sestavení nebylo nalezeno v cestě zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-132">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="5cff3-133">Tyto chyby vyvolávají vyvolání <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="5cff3-133">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="5cff3-134">Některá vazba a selhání načítání nejsou ovlivněny tímto elementem a jsou vždy ukládány do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5cff3-134">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="5cff3-135">K těmto selháním dochází, protože bylo nalezeno sestavení, ale nebylo možné ho načíst.</span><span class="sxs-lookup"><span data-stu-id="5cff3-135">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="5cff3-136">Vyvolávají <xref:System.BadImageFormatException> nebo <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="5cff3-136">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="5cff3-137">Následující seznam obsahuje některé příklady takových selhání.</span><span class="sxs-lookup"><span data-stu-id="5cff3-137">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="5cff3-138">Pokud se pokusíte načíst soubor není platným sestavením, následné pokusy o načtení sestavení selžou i v případě, že je chybný soubor nahrazen správným sestavením.</span><span class="sxs-lookup"><span data-stu-id="5cff3-138">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="5cff3-139">Pokud se pokusíte načíst sestavení, které je uzamčeno systémem souborů, následné pokusy o načtení sestavení selžou i poté, co je sestavení uvolněno systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="5cff3-139">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="5cff3-140">Pokud je jedna nebo více verzí sestavení, které se pokoušíte načíst, v cestě zjišťování, ale konkrétní verze, kterou požadujete, není mimo ně, následné pokusy o načtení této verze selžou, i když je správná verze přesunuta do cesty pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-140">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cff3-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="5cff3-141">Example</span></span>  
 <span data-ttu-id="5cff3-142">Následující příklad ukazuje, jak zakázat ukládání neúspěšných vazeb sestavení do mezipaměti, ke kterým dochází, protože sestavení nebylo nalezeno při zjišťování.</span><span class="sxs-lookup"><span data-stu-id="5cff3-142">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cff3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cff3-143">See also</span></span>

- [<span data-ttu-id="5cff3-144">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5cff3-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5cff3-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5cff3-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5cff3-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="5cff3-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
