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
ms.openlocfilehash: 6a4741c6a4745bdba00fdb525b39b70d0b15e005
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704853"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="fa734-102">\<qualifyassembly – > – Element</span><span class="sxs-lookup"><span data-stu-id="fa734-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="fa734-103">Určuje úplný název sestavení, které se mají dynamicky načíst při použití částečný název.</span><span class="sxs-lookup"><span data-stu-id="fa734-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
 <span data-ttu-id="fa734-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fa734-104">\<configuration></span></span>  
<span data-ttu-id="fa734-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="fa734-105">\<runtime></span></span>  
<span data-ttu-id="fa734-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="fa734-106">\<assemblyBinding></span></span>  
<span data-ttu-id="fa734-107">\<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="fa734-107">\<qualifyAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa734-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa734-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa734-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fa734-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fa734-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fa734-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa734-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="fa734-111">Attributes</span></span>  
  
|<span data-ttu-id="fa734-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="fa734-112">Attribute</span></span>|<span data-ttu-id="fa734-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fa734-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="fa734-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fa734-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="fa734-115">Částečný název sestavení, určuje, jak se zobrazí v kódu.</span><span class="sxs-lookup"><span data-stu-id="fa734-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="fa734-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fa734-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="fa734-117">Určuje úplný název sestavení, jak se zobrazí v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa734-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa734-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fa734-118">Child Elements</span></span>  
 <span data-ttu-id="fa734-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="fa734-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa734-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fa734-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fa734-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="fa734-121">Element</span></span>|<span data-ttu-id="fa734-122">Popis</span><span class="sxs-lookup"><span data-stu-id="fa734-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="fa734-123">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa734-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="fa734-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa734-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fa734-125">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fa734-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa734-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa734-126">Remarks</span></span>  
 <span data-ttu-id="fa734-127">Volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda názvů částečného sestavení způsobí, že modul common language runtime vyhledat sestavení pouze v základní adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="fa734-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="fa734-128">Použití  **\<qualifyassembly – >** prvku v konfiguračním souboru aplikace zadejte informace o úplné sestavení (název, verzi, token veřejného klíče a jazykovou verzi) a způsobit, že modul common language runtime pro hledání pro sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa734-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="fa734-129">**FullName** atribut musí obsahovat čtyři pole Identita sestavení: název, verzi, token veřejného klíče a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="fa734-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="fa734-130">**PartialName** atribut částečně musí odkazovat na sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa734-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="fa734-131">Je potřeba určit nejmíň textový název sestavení (nejběžnější případy), ale může také obsahovat verzi, token veřejného klíče, nebo jazykové verze (nebo libovolnou kombinaci čtyři, ale ne všechny čtyři).</span><span class="sxs-lookup"><span data-stu-id="fa734-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="fa734-132">**PartialName** musí odpovídat názvu zadané ve volání.</span><span class="sxs-lookup"><span data-stu-id="fa734-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="fa734-133">Například nelze zadat `"math"` jako **partialName** atribut v konfiguračním souboru a volání `Assembly.Load("math, Version=3.3.3.3")` ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="fa734-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa734-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa734-134">Example</span></span>  
 <span data-ttu-id="fa734-135">Následující příklad změní logicky volání `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span><span class="sxs-lookup"><span data-stu-id="fa734-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa734-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa734-136">See also</span></span>

- [<span data-ttu-id="fa734-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="fa734-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="fa734-138">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="fa734-138">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="fa734-139">[Částečné odkazy na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fa734-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
