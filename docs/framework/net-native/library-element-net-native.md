---
title: Element &lt;Library&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2663bbd5ca93341455b7bd036469d25d91f4a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltlibrarygt-element-net-native"></a><span data-ttu-id="61e7c-102">Element &lt;Library&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="61e7c-102">&lt;Library&gt; Element (.NET Native)</span></span>
<span data-ttu-id="61e7c-103">Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.</span><span class="sxs-lookup"><span data-stu-id="61e7c-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="61e7c-104">\<Direktivy > elementu</span><span class="sxs-lookup"><span data-stu-id="61e7c-104">\<Directives> Element</span></span>  
<span data-ttu-id="61e7c-105">\<Knihovna > elementu</span><span class="sxs-lookup"><span data-stu-id="61e7c-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e7c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61e7c-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61e7c-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61e7c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="61e7c-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61e7c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61e7c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="61e7c-109">Attributes</span></span>  
  
|<span data-ttu-id="61e7c-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="61e7c-110">Attribute</span></span>|<span data-ttu-id="61e7c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="61e7c-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="61e7c-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="61e7c-112">Required attribute.</span></span> <span data-ttu-id="61e7c-113">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="61e7c-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="61e7c-114">Podřízené elementy tohoto `<Library>` element definovat zásady reflexe modulu runtime pro typy a členy typu najít v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="61e7c-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="61e7c-115">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="61e7c-115">Name attribute</span></span>  
  
|<span data-ttu-id="61e7c-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="61e7c-116">Value</span></span>|<span data-ttu-id="61e7c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="61e7c-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61e7c-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="61e7c-118">*assembly_name*</span></span>|<span data-ttu-id="61e7c-119">Jednoduchý název sestavení, bez jeho přípona souboru.</span><span class="sxs-lookup"><span data-stu-id="61e7c-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="61e7c-120">Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="61e7c-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="61e7c-121">Název sestavení s názvem Extensions.dll je například "Rozšíření".</span><span class="sxs-lookup"><span data-stu-id="61e7c-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="61e7c-122">Najdete v části poznámky pro speciální formu *assembly_name* podmíněné zahrnutí metadat ze sestavení, která podporuje.</span><span class="sxs-lookup"><span data-stu-id="61e7c-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61e7c-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61e7c-123">Child Elements</span></span>  
  
|<span data-ttu-id="61e7c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="61e7c-124">Element</span></span>|<span data-ttu-id="61e7c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="61e7c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61e7c-126">\<Sestavení ></span><span class="sxs-lookup"><span data-stu-id="61e7c-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="61e7c-127">Zásady platí pro všechny typy v určitém sestavení.</span><span class="sxs-lookup"><span data-stu-id="61e7c-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="61e7c-128">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="61e7c-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="61e7c-129">Zásady platí pro všechny typy v konkrétní oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="61e7c-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="61e7c-130">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="61e7c-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="61e7c-131">Platí pro konkrétní typ, jako je například třídu nebo strukturu zásad.</span><span class="sxs-lookup"><span data-stu-id="61e7c-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="61e7c-132">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="61e7c-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="61e7c-133">Zásada se vztahuje na vytvořený obecného typu.</span><span class="sxs-lookup"><span data-stu-id="61e7c-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="61e7c-134">Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může definovat zásady pro `List<String>` typu.</span><span class="sxs-lookup"><span data-stu-id="61e7c-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61e7c-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61e7c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="61e7c-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="61e7c-136">Element</span></span>|<span data-ttu-id="61e7c-137">Popis</span><span class="sxs-lookup"><span data-stu-id="61e7c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61e7c-138">\<Direktivy jazyka ></span><span class="sxs-lookup"><span data-stu-id="61e7c-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="61e7c-139">Kořenový element souboru direktivy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="61e7c-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61e7c-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61e7c-140">Remarks</span></span>  
 <span data-ttu-id="61e7c-141">[ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula, jednu nebo více `<Library>` elementy.</span><span class="sxs-lookup"><span data-stu-id="61e7c-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="61e7c-142">`<Library>` Element slouží jako kontejner pro definování program elementy, jejichž metadat je vyžadována v době běhu; tento element není vyjádření zásad.</span><span class="sxs-lookup"><span data-stu-id="61e7c-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="61e7c-143">Při kompilaci, nástrojů kompilátoru vyhledávat pouze v knihovně, které jsou určené, které `<Library>` element pro program prvky identifikovaná její podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="61e7c-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="61e7c-144">Na rozdíl od nástroje kompilátoru hledání všechny knihovny, including.NET Framework základní knihovny, pro program prvky identifikovaná podřízených elementů [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="61e7c-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="61e7c-145">`<Library>`direktivy, lze podmíněně využívat.</span><span class="sxs-lookup"><span data-stu-id="61e7c-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="61e7c-146">Pokud název `<Library>` element zahájení a ukončení s hvězdičkou (*), `<Library>` – direktiva má význam jen v případě, že zadaný v rozmezí hvězdičky sestavení odkazuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="61e7c-146">If the name of the `<Library>` element starts and ends with an asterisk (*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="61e7c-147">Například následující direktivy modulu runtime platí jenom v případě, že Utillities.dll sestavení odkazuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="61e7c-147">For example, the following runtime directive applies only if the Utillities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61e7c-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="61e7c-148">See Also</span></span>  
 [<span data-ttu-id="61e7c-149">\<Aplikace > elementu</span><span class="sxs-lookup"><span data-stu-id="61e7c-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 [<span data-ttu-id="61e7c-150">\<Direktivy > elementu</span><span class="sxs-lookup"><span data-stu-id="61e7c-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 [<span data-ttu-id="61e7c-151">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="61e7c-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="61e7c-152">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="61e7c-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
