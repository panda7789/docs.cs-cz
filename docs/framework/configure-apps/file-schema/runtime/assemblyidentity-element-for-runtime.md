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
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154306"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="76b4a-102">\<assemblyIdentity> – element pro \<runtime></span><span class="sxs-lookup"><span data-stu-id="76b4a-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="76b4a-103">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="76b4a-103">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="76b4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76b4a-104">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76b4a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76b4a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="76b4a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76b4a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76b4a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="76b4a-107">Attributes</span></span>  
  
|<span data-ttu-id="76b4a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="76b4a-108">Attribute</span></span>|<span data-ttu-id="76b4a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="76b4a-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="76b4a-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="76b4a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="76b4a-111">Název sestavení</span><span class="sxs-lookup"><span data-stu-id="76b4a-111">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="76b4a-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="76b4a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="76b4a-113">Řetězec, který určuje jazyk a zemi/oblast sestavení.</span><span class="sxs-lookup"><span data-stu-id="76b4a-113">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="76b4a-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="76b4a-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="76b4a-115">Hexadecimální hodnota, která určuje silný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="76b4a-115">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="76b4a-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="76b4a-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="76b4a-117">Jedna z hodnot "x86", "amd64", "MSIL" nebo "ia64" s určením architektury procesoru pro sestavení, které obsahuje kód specifický pro procesor.</span><span class="sxs-lookup"><span data-stu-id="76b4a-117">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="76b4a-118">V hodnotách se nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="76b4a-118">The values are not case-sensitive.</span></span> <span data-ttu-id="76b4a-119">Pokud má atribut přiřazenou jinou hodnotu, `<assemblyIdentity>` je ignorován celý prvek.</span><span class="sxs-lookup"><span data-stu-id="76b4a-119">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="76b4a-120">Viz třída <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="76b4a-120">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="76b4a-121">processorArchitecture – atribut</span><span class="sxs-lookup"><span data-stu-id="76b4a-121">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="76b4a-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="76b4a-122">Value</span></span>|<span data-ttu-id="76b4a-123">Description</span><span class="sxs-lookup"><span data-stu-id="76b4a-123">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="76b4a-124">Pouze architektura AMD X86-64.</span><span class="sxs-lookup"><span data-stu-id="76b4a-124">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="76b4a-125">Jenom architektura Intel Itanium.</span><span class="sxs-lookup"><span data-stu-id="76b4a-125">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="76b4a-126">Neutrální s ohledem na procesor a bity na slovo.</span><span class="sxs-lookup"><span data-stu-id="76b4a-126">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="76b4a-127">32 procesor x86, buď nativní, nebo v prostředí Windows on Windows (WOW) na platformě 64.</span><span class="sxs-lookup"><span data-stu-id="76b4a-127">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76b4a-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76b4a-128">Child Elements</span></span>  
 <span data-ttu-id="76b4a-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="76b4a-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76b4a-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76b4a-130">Parent Elements</span></span>  
  
|<span data-ttu-id="76b4a-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="76b4a-131">Element</span></span>|<span data-ttu-id="76b4a-132">Description</span><span class="sxs-lookup"><span data-stu-id="76b4a-132">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="76b4a-133">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="76b4a-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="76b4a-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76b4a-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="76b4a-135">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="76b4a-135">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="76b4a-136">`<dependentAssembly>`Pro každé sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="76b4a-136">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="76b4a-137">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="76b4a-137">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76b4a-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76b4a-138">Remarks</span></span>  
 <span data-ttu-id="76b4a-139">Každý **\<dependentAssembly>** element musí mít jeden **\<assemblyIdentity>** podřízený element.</span><span class="sxs-lookup"><span data-stu-id="76b4a-139">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="76b4a-140">Pokud `processorArchitecture` je přítomen atribut, `<assemblyIdentity>` element se vztahuje pouze na sestavení s odpovídající architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="76b4a-140">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="76b4a-141">Pokud `processorArchitecture` atribut není přítomen, `<assemblyIdentity>` element může platit pro sestavení s libovolnou architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="76b4a-141">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="76b4a-142">Následující příklad ukazuje konfigurační soubor pro dvě sestavení se stejným názvem, která cílí na dvě různé architektury procesorů a jejichž verze nebyly v synchronizaci synchronizovány. Když se aplikace spustí na platformě x86, použije se první `<assemblyIdentity>` prvek a druhý se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="76b4a-142">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="76b4a-143">Pokud je aplikace spuštěna na jiné platformě než x86 nebo ia64, obě jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="76b4a-143">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="76b4a-144">Pokud konfigurační soubor obsahuje prvek bez `<assemblyIdentity>` `processorArchitecture` atributu a neobsahuje prvek, který odpovídá platformě, `processorArchitecture` je použit prvek bez atributu.</span><span class="sxs-lookup"><span data-stu-id="76b4a-144">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76b4a-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="76b4a-145">Example</span></span>  
 <span data-ttu-id="76b4a-146">Následující příklad ukazuje, jak poskytnout informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="76b4a-146">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76b4a-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="76b4a-147">See also</span></span>

- [<span data-ttu-id="76b4a-148">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="76b4a-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="76b4a-149">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="76b4a-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="76b4a-150">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="76b4a-150">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
