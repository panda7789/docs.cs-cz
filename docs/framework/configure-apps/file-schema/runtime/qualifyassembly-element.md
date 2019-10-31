---
title: Element <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115787"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="a8b2c-102">\<element > qualifyAssembly</span><span class="sxs-lookup"><span data-stu-id="a8b2c-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="a8b2c-103">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="a8b2c-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a8b2c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8b2c-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8b2c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a8b2c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="a8b2c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="a8b2c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly >**</span><span class="sxs-lookup"><span data-stu-id="a8b2c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8b2c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8b2c-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8b2c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a8b2c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a8b2c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8b2c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8b2c-111">Attributes</span></span>  
  
|<span data-ttu-id="a8b2c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a8b2c-112">Attribute</span></span>|<span data-ttu-id="a8b2c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a8b2c-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="a8b2c-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a8b2c-115">Určuje částečný název sestavení, jak se zobrazí v kódu.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="a8b2c-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a8b2c-117">Určuje úplný název sestavení, který se zobrazí v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="a8b2c-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8b2c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a8b2c-118">Child Elements</span></span>  
 <span data-ttu-id="a8b2c-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8b2c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8b2c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a8b2c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a8b2c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8b2c-121">Element</span></span>|<span data-ttu-id="a8b2c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a8b2c-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a8b2c-123">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a8b2c-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a8b2c-125">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8b2c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8b2c-126">Remarks</span></span>  
 <span data-ttu-id="a8b2c-127">Volání metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> s použitím částečných názvů sestavení způsobí, že modul CLR (Common Language Runtime) hledá sestavení pouze v základním adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="a8b2c-128">Pomocí elementu **\<qualifyAssembly >** v konfiguračním souboru aplikace poskytněte úplné informace o sestavení (název, verze, token veřejného klíče a jazykové verzi) a způsobí, že modul CLR (Common Language Runtime) vyhledá sestavení v globálním mezipaměť sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="a8b2c-129">Atribut **FullName** musí zahrnovat čtyři pole identity sestavení: název, verze, token veřejného klíče a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="a8b2c-130">Atribut **Partial** musí odkazovat na sestavení částečně.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="a8b2c-131">Je nutné zadat alespoň textový název sestavení (Nejběžnější případ), ale můžete také zahrnout verze, token veřejného klíče nebo jazykovou verzi (nebo libovolnou kombinaci čtyř, ale ne všech čtyř).</span><span class="sxs-lookup"><span data-stu-id="a8b2c-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="a8b2c-132">Parametr **Partial** se musí shodovat s názvem zadaným ve vašem volání.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="a8b2c-133">Například nemůžete zadat `"math"` jako atribut **částečného** atributu do konfiguračního souboru a volat `Assembly.Load("math, Version=3.3.3.3")` ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8b2c-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8b2c-134">Example</span></span>  
 <span data-ttu-id="a8b2c-135">Následující příklad logicky zapne volání `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="a8b2c-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8b2c-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8b2c-136">See also</span></span>

- [<span data-ttu-id="a8b2c-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a8b2c-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a8b2c-138">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="a8b2c-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="a8b2c-139">[Odkazy na částečné sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a8b2c-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
