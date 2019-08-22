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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4aa90a378630c9aff74923d8e8600aed15a77a5e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663506"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="88e55-102">\<qualifyAssembly – element ></span><span class="sxs-lookup"><span data-stu-id="88e55-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="88e55-103">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="88e55-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="88e55-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="88e55-104">\<configuration></span></span>  
<span data-ttu-id="88e55-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="88e55-105">\<runtime></span></span>  
<span data-ttu-id="88e55-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="88e55-106">\<assemblyBinding></span></span>  
<span data-ttu-id="88e55-107">\<qualifyAssembly ></span><span class="sxs-lookup"><span data-stu-id="88e55-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e55-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88e55-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88e55-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88e55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88e55-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88e55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88e55-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="88e55-111">Attributes</span></span>  
  
|<span data-ttu-id="88e55-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="88e55-112">Attribute</span></span>|<span data-ttu-id="88e55-113">Popis</span><span class="sxs-lookup"><span data-stu-id="88e55-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="88e55-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="88e55-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="88e55-115">Určuje částečný název sestavení, jak se zobrazí v kódu.</span><span class="sxs-lookup"><span data-stu-id="88e55-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="88e55-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="88e55-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="88e55-117">Určuje úplný název sestavení, který se zobrazí v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="88e55-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88e55-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="88e55-118">Child Elements</span></span>  
 <span data-ttu-id="88e55-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="88e55-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88e55-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="88e55-120">Parent Elements</span></span>  
  
|<span data-ttu-id="88e55-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="88e55-121">Element</span></span>|<span data-ttu-id="88e55-122">Popis</span><span class="sxs-lookup"><span data-stu-id="88e55-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="88e55-123">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="88e55-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="88e55-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88e55-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="88e55-125">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="88e55-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88e55-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88e55-126">Remarks</span></span>  
 <span data-ttu-id="88e55-127"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Volání metody pomocí částečných názvů sestavení způsobí, že modul CLR (Common Language Runtime) hledá sestavení pouze v základním adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="88e55-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="88e55-128">Použijte **qualifyAssembly > element v konfiguračním souboru aplikace k poskytnutí úplných informací o sestavení (název, verze, token veřejného klíče a jazyková verze) a způsobí, že modul CLR (Common Language Runtime) vyhledá sestavení v \<** globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="88e55-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="88e55-129">Atribut **FullName** musí zahrnovat čtyři pole identity sestavení: název, verze, token veřejného klíče a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="88e55-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="88e55-130">Atribut **Partial** musí odkazovat na sestavení částečně.</span><span class="sxs-lookup"><span data-stu-id="88e55-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="88e55-131">Je nutné zadat alespoň textový název sestavení (Nejběžnější případ), ale můžete také zahrnout verze, token veřejného klíče nebo jazykovou verzi (nebo libovolnou kombinaci čtyř, ale ne všech čtyř).</span><span class="sxs-lookup"><span data-stu-id="88e55-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="88e55-132">Parametr **Partial** se musí shodovat s názvem zadaným ve vašem volání.</span><span class="sxs-lookup"><span data-stu-id="88e55-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="88e55-133">Například nemůžete zadat `"math"` jako atribut **Partial** do konfiguračního souboru a volat `Assembly.Load("math, Version=3.3.3.3")` do kódu.</span><span class="sxs-lookup"><span data-stu-id="88e55-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e55-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="88e55-134">Example</span></span>  
 <span data-ttu-id="88e55-135">Následující příklad logicky přepíná volání `Assembly.Load("math")` do. `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`</span><span class="sxs-lookup"><span data-stu-id="88e55-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88e55-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88e55-136">See also</span></span>

- [<span data-ttu-id="88e55-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="88e55-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="88e55-138">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="88e55-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="88e55-139">[Odkazy na částečné sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="88e55-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
