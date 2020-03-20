---
title: Element <assemblyIdentity> pro <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154306"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="65e93-102">\<assemblyIdentity> \<Element pro> za běhu</span><span class="sxs-lookup"><span data-stu-id="65e93-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="65e93-103">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="65e93-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65e93-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="65e93-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="65e93-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="65e93-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="65e93-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="65e93-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="65e93-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="65e93-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span><span class="sxs-lookup"><span data-stu-id="65e93-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e93-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65e93-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65e93-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65e93-110">Attributes and Elements</span></span>  
 <span data-ttu-id="65e93-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65e93-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65e93-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="65e93-112">Attributes</span></span>  
  
|<span data-ttu-id="65e93-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="65e93-113">Attribute</span></span>|<span data-ttu-id="65e93-114">Popis</span><span class="sxs-lookup"><span data-stu-id="65e93-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="65e93-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="65e93-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="65e93-116">Název sestavení</span><span class="sxs-lookup"><span data-stu-id="65e93-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="65e93-117">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="65e93-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="65e93-118">Řetězec, který určuje jazyk a zemi nebo oblast sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="65e93-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="65e93-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="65e93-120">Šestnáctková hodnota, která určuje silný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="65e93-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="65e93-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="65e93-122">Jedna z hodnot "x86", "amd64", "msil" nebo "ia64", určující architekturu procesoru pro sestavení, které obsahuje kód specifický pro procesor.</span><span class="sxs-lookup"><span data-stu-id="65e93-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="65e93-123">Hodnoty nejsou rozlišována malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="65e93-123">The values are not case-sensitive.</span></span> <span data-ttu-id="65e93-124">Pokud je atribut přiřazen jinou `<assemblyIdentity>` hodnotu, celý prvek je ignorován.</span><span class="sxs-lookup"><span data-stu-id="65e93-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="65e93-125">Viz třída <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="65e93-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="65e93-126">atribut architektury procesoru</span><span class="sxs-lookup"><span data-stu-id="65e93-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="65e93-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="65e93-127">Value</span></span>|<span data-ttu-id="65e93-128">Popis</span><span class="sxs-lookup"><span data-stu-id="65e93-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="65e93-129">Pouze architektura AMD x86-64.</span><span class="sxs-lookup"><span data-stu-id="65e93-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="65e93-130">Pouze architektura Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="65e93-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="65e93-131">Neutrální s ohledem na procesor a bity na slovo.</span><span class="sxs-lookup"><span data-stu-id="65e93-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="65e93-132">32bitový procesor x86, nativní nebo v prostředí Windows v systému Windows (WOW) na 64bitové platformě.</span><span class="sxs-lookup"><span data-stu-id="65e93-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65e93-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="65e93-133">Child Elements</span></span>  
 <span data-ttu-id="65e93-134">Žádné.</span><span class="sxs-lookup"><span data-stu-id="65e93-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65e93-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="65e93-135">Parent Elements</span></span>  
  
|<span data-ttu-id="65e93-136">Element</span><span class="sxs-lookup"><span data-stu-id="65e93-136">Element</span></span>|<span data-ttu-id="65e93-137">Popis</span><span class="sxs-lookup"><span data-stu-id="65e93-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="65e93-138">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="65e93-139">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65e93-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="65e93-140">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="65e93-141">Pro `<dependentAssembly>` každé sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="65e93-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="65e93-142">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="65e93-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65e93-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65e93-143">Remarks</span></span>  
 <span data-ttu-id="65e93-144">Každý \*\* \<prvek dependentAssembly>\*\* musí mít jeden \*\* \<prvek identity identity>\*\* podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="65e93-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="65e93-145">Pokud `processorArchitecture` je atribut přítomen, `<assemblyIdentity>` prvek se vztahuje pouze na sestavení s odpovídající architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="65e93-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="65e93-146">Pokud `processorArchitecture` atribut není k `<assemblyIdentity>` dispozici, prvek lze použít pro sestavení s libovolnou architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="65e93-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="65e93-147">Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, které se zaměřují na dvě různé architektury procesoru a jejichž verze nebyly udržovány v synchronizaci. Když se aplikace spustí na platformě `<assemblyIdentity>` x86, použije se první prvek a druhý je ignorován.</span><span class="sxs-lookup"><span data-stu-id="65e93-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="65e93-148">Pokud se aplikace spustí na jiné platformě než x86 nebo ia64, jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="65e93-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="65e93-149">Pokud konfigurační `<assemblyIdentity>` soubor `processorArchitecture` obsahuje prvek bez atributu a neobsahuje prvek, `processorArchitecture` který odpovídá platformě, prvek bez atributu se používá.</span><span class="sxs-lookup"><span data-stu-id="65e93-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65e93-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="65e93-150">Example</span></span>  
 <span data-ttu-id="65e93-151">Následující příklad ukazuje, jak poskytnout informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e93-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65e93-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="65e93-152">See also</span></span>

- [<span data-ttu-id="65e93-153">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="65e93-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="65e93-154">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="65e93-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="65e93-155">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="65e93-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
