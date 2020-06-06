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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153916"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="60721-102">Element \<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="60721-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="60721-103">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="60721-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="60721-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60721-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60721-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60721-105">Attributes and Elements</span></span>  
 <span data-ttu-id="60721-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60721-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60721-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="60721-107">Attributes</span></span>  
  
|<span data-ttu-id="60721-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="60721-108">Attribute</span></span>|<span data-ttu-id="60721-109">Popis</span><span class="sxs-lookup"><span data-stu-id="60721-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="60721-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="60721-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="60721-111">Určuje částečný název sestavení, jak se zobrazí v kódu.</span><span class="sxs-lookup"><span data-stu-id="60721-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="60721-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="60721-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="60721-113">Určuje úplný název sestavení, který se zobrazí v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="60721-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60721-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60721-114">Child Elements</span></span>  
 <span data-ttu-id="60721-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="60721-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60721-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60721-116">Parent Elements</span></span>  
  
|<span data-ttu-id="60721-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="60721-117">Element</span></span>|<span data-ttu-id="60721-118">Description</span><span class="sxs-lookup"><span data-stu-id="60721-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="60721-119">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="60721-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="60721-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="60721-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="60721-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="60721-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60721-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60721-122">Remarks</span></span>  
 <span data-ttu-id="60721-123">Volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody pomocí částečných názvů sestavení způsobí, že modul CLR (Common Language Runtime) hledá sestavení pouze v základním adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="60721-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="60721-124">Použijte **\<qualifyAssembly>** element v konfiguračním souboru aplikace k poskytnutí úplných informací o sestavení (název, verze, token veřejného klíče a jazyková verze) a způsobit, že modul CLR (Common Language Runtime) hledá sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="60721-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="60721-125">Atribut **FullName** musí zahrnovat čtyři pole identity sestavení: název, verze, token veřejného klíče a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="60721-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="60721-126">Atribut **Partial** musí odkazovat na sestavení částečně.</span><span class="sxs-lookup"><span data-stu-id="60721-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="60721-127">Je nutné zadat alespoň textový název sestavení (Nejběžnější případ), ale můžete také zahrnout verze, token veřejného klíče nebo jazykovou verzi (nebo libovolnou kombinaci čtyř, ale ne všech čtyř).</span><span class="sxs-lookup"><span data-stu-id="60721-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="60721-128">Parametr **Partial** se musí shodovat s názvem zadaným ve vašem volání.</span><span class="sxs-lookup"><span data-stu-id="60721-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="60721-129">Například nemůžete zadat `"math"` jako atribut **Partial** do konfiguračního souboru a volat `Assembly.Load("math, Version=3.3.3.3")` do kódu.</span><span class="sxs-lookup"><span data-stu-id="60721-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60721-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="60721-130">Example</span></span>  
 <span data-ttu-id="60721-131">Následující příklad logicky přepíná volání `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .</span><span class="sxs-lookup"><span data-stu-id="60721-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60721-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="60721-132">See also</span></span>

- [<span data-ttu-id="60721-133">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="60721-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="60721-134">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="60721-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="60721-135">[Odkazy na částečné sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="60721-135">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
