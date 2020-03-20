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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153916"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="a84ff-102">\<kvalifikujisestavení> prvku</span><span class="sxs-lookup"><span data-stu-id="a84ff-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="a84ff-103">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="a84ff-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="a84ff-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a84ff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a84ff-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a84ff-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a84ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="a84ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="a84ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<kvalifikačnímontážní>**</span><span class="sxs-lookup"><span data-stu-id="a84ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84ff-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a84ff-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a84ff-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a84ff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a84ff-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a84ff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a84ff-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a84ff-111">Attributes</span></span>  
  
|<span data-ttu-id="a84ff-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="a84ff-112">Attribute</span></span>|<span data-ttu-id="a84ff-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a84ff-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="a84ff-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a84ff-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a84ff-115">Určuje částečný název sestavení tak, jak je uveden v kódu.</span><span class="sxs-lookup"><span data-stu-id="a84ff-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="a84ff-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a84ff-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="a84ff-117">Určuje úplný název sestavení tak, jak je uveden v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a84ff-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a84ff-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a84ff-118">Child Elements</span></span>  
 <span data-ttu-id="a84ff-119">Žádné.</span><span class="sxs-lookup"><span data-stu-id="a84ff-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a84ff-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a84ff-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a84ff-121">Element</span><span class="sxs-lookup"><span data-stu-id="a84ff-121">Element</span></span>|<span data-ttu-id="a84ff-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a84ff-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a84ff-123">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a84ff-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a84ff-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a84ff-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a84ff-125">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a84ff-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a84ff-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a84ff-126">Remarks</span></span>  
 <span data-ttu-id="a84ff-127">Volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody pomocí částečných názvů sestavení způsobí, že soubor RUNTIME společného jazyka vyhledá sestavení pouze v základním adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="a84ff-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="a84ff-128">Pomocí prvku \*\* \<qualifyAssembly>\*\* v konfiguračním souboru aplikace můžete poskytnout úplné informace o sestavení (název, verze, token veřejného klíče a jazykovou verzi) a způsobit, že soubor runtime společného jazyka vyhledá sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a84ff-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="a84ff-129">Atribut **fullName** musí obsahovat čtyři pole identity sestavení: název, verze, token veřejného klíče a jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="a84ff-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="a84ff-130">Atribut **partialName** musí částečně odkazovat na sestavení.</span><span class="sxs-lookup"><span data-stu-id="a84ff-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="a84ff-131">Je nutné zadat alespoň textový název sestavení (nejběžnější případ), ale můžete také zahrnout verzi, token veřejného klíče nebo jazykovou verzi (nebo libovolnou kombinaci čtyř, ale ne všech čtyř).</span><span class="sxs-lookup"><span data-stu-id="a84ff-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="a84ff-132">**PartialName** se musí shodovat s názvem zadaným ve vašem volání.</span><span class="sxs-lookup"><span data-stu-id="a84ff-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="a84ff-133">Například nelze zadat `"math"` jako **partialName** atribut v konfiguračním souboru a volání `Assembly.Load("math, Version=3.3.3.3")` v kódu.</span><span class="sxs-lookup"><span data-stu-id="a84ff-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a84ff-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="a84ff-134">Example</span></span>  
 <span data-ttu-id="a84ff-135">Následující příklad logicky změní `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`volání na .</span><span class="sxs-lookup"><span data-stu-id="a84ff-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a84ff-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="a84ff-136">See also</span></span>

- [<span data-ttu-id="a84ff-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a84ff-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a84ff-138">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="a84ff-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="a84ff-139">[Odkazy na částečné sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a84ff-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
