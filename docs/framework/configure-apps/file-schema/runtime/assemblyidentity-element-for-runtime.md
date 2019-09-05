---
title: <assemblyIdentity> – element pro <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: 7cce12f6fb4b957d740cd590bd84851fa16a117d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252800"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="5a168-102">\<prvek assemblyIdentity > pro \<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="5a168-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="5a168-103">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a168-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="5a168-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a168-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a168-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a168-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5a168-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="5a168-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="5a168-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a168-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="5a168-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> assemblyIdentity**</span><span class="sxs-lookup"><span data-stu-id="5a168-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a168-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a168-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a168-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a168-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a168-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a168-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a168-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a168-112">Attributes</span></span>  
  
|<span data-ttu-id="5a168-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a168-113">Attribute</span></span>|<span data-ttu-id="5a168-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5a168-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5a168-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a168-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a168-116">Název sestavení</span><span class="sxs-lookup"><span data-stu-id="5a168-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="5a168-117">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a168-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5a168-118">Řetězec, který určuje jazyk a zemi/oblast sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a168-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="5a168-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a168-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5a168-120">Hexadecimální hodnota, která určuje silný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a168-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="5a168-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a168-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5a168-122">Jedna z hodnot "x86", "amd64", "MSIL" nebo "ia64" s určením architektury procesoru pro sestavení, které obsahuje kód specifický pro procesor.</span><span class="sxs-lookup"><span data-stu-id="5a168-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="5a168-123">V hodnotách se nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="5a168-123">The values are not case-sensitive.</span></span> <span data-ttu-id="5a168-124">Pokud má atribut přiřazenou jinou hodnotu, je ignorován celý `<assemblyIdentity>` prvek.</span><span class="sxs-lookup"><span data-stu-id="5a168-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="5a168-125">Viz <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="5a168-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="5a168-126">processorArchitecture – atribut</span><span class="sxs-lookup"><span data-stu-id="5a168-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="5a168-127">Value</span><span class="sxs-lookup"><span data-stu-id="5a168-127">Value</span></span>|<span data-ttu-id="5a168-128">Popis</span><span class="sxs-lookup"><span data-stu-id="5a168-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="5a168-129">Pouze architektura AMD X86-64.</span><span class="sxs-lookup"><span data-stu-id="5a168-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="5a168-130">Jenom architektura Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="5a168-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="5a168-131">Neutrální s ohledem na procesor a bity na slovo.</span><span class="sxs-lookup"><span data-stu-id="5a168-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="5a168-132">32 procesor x86, buď nativní, nebo v prostředí Windows on Windows (WOW) na platformě 64.</span><span class="sxs-lookup"><span data-stu-id="5a168-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a168-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a168-133">Child Elements</span></span>  
 <span data-ttu-id="5a168-134">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a168-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a168-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a168-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5a168-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a168-136">Element</span></span>|<span data-ttu-id="5a168-137">Popis</span><span class="sxs-lookup"><span data-stu-id="5a168-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5a168-138">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a168-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5a168-139">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a168-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="5a168-140">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a168-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="5a168-141">Pro každé `<dependentAssembly>` sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="5a168-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="5a168-142">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5a168-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a168-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a168-143">Remarks</span></span>  
 <span data-ttu-id="5a168-144">**Každý\<prvek dependentAssembly >** musí mít jeden  **\<podřízený prvek assemblyIdentity >** .</span><span class="sxs-lookup"><span data-stu-id="5a168-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="5a168-145">Pokud je přítomen `<assemblyIdentity>`atribut, element se vztahuje pouze na sestavení s odpovídající architekturou procesoru. `processorArchitecture`</span><span class="sxs-lookup"><span data-stu-id="5a168-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="5a168-146">Pokud atribut není přítomen, element může platit pro sestavení s libovolnou architekturou procesoru. `<assemblyIdentity>` `processorArchitecture`</span><span class="sxs-lookup"><span data-stu-id="5a168-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="5a168-147">Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, která cílí na dvě různé architektury procesorů a jejichž verze nebyly v synchronizaci synchronizovány. Když se aplikace spustí na platformě x86, použije se `<assemblyIdentity>` první prvek a druhý se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="5a168-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="5a168-148">Pokud je aplikace spuštěna na jiné platformě než x86 nebo ia64, obě jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="5a168-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="5a168-149">Pokud konfigurační soubor obsahuje `<assemblyIdentity>` prvek `processorArchitecture` bez atributu a neobsahuje prvek, který odpovídá platformě `processorArchitecture` , je použit prvek bez atributu.</span><span class="sxs-lookup"><span data-stu-id="5a168-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a168-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a168-150">Example</span></span>  
 <span data-ttu-id="5a168-151">Následující příklad ukazuje, jak poskytnout informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a168-151">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a168-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a168-152">See also</span></span>

- [<span data-ttu-id="5a168-153">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="5a168-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5a168-154">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5a168-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5a168-155">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="5a168-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
