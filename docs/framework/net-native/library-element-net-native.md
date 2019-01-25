---
title: Element &lt;Library&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6615ab30fdc0d0ab65f135e1df4e206f5548dc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743778"
---
# <a name="ltlibrarygt-element-net-native"></a><span data-ttu-id="661c7-102">Element &lt;Library&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="661c7-102">&lt;Library&gt; Element (.NET Native)</span></span>
<span data-ttu-id="661c7-103">Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.</span><span class="sxs-lookup"><span data-stu-id="661c7-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="661c7-104">\<Direktivy > – Element</span><span class="sxs-lookup"><span data-stu-id="661c7-104">\<Directives> Element</span></span>  
<span data-ttu-id="661c7-105">\<Knihovna > – Element</span><span class="sxs-lookup"><span data-stu-id="661c7-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="661c7-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="661c7-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="661c7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="661c7-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="661c7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="661c7-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="661c7-109">Attributes</span></span>  
  
|<span data-ttu-id="661c7-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="661c7-110">Attribute</span></span>|<span data-ttu-id="661c7-111">Popis</span><span class="sxs-lookup"><span data-stu-id="661c7-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="661c7-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="661c7-112">Required attribute.</span></span> <span data-ttu-id="661c7-113">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="661c7-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="661c7-114">Podřízené prvky tohoto `<Library>` element definovat zásady reflexe modulu runtime pro typy a členy typů nalezena v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="661c7-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="661c7-115">Název atributu</span><span class="sxs-lookup"><span data-stu-id="661c7-115">Name attribute</span></span>  
  
|<span data-ttu-id="661c7-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="661c7-116">Value</span></span>|<span data-ttu-id="661c7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="661c7-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="661c7-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="661c7-118">*assembly_name*</span></span>|<span data-ttu-id="661c7-119">Jednoduchý název sestavení, bez jeho přípona souboru.</span><span class="sxs-lookup"><span data-stu-id="661c7-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="661c7-120">Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="661c7-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="661c7-121">Název sestavení s názvem Extensions.dll je například "Rozšíření".</span><span class="sxs-lookup"><span data-stu-id="661c7-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="661c7-122">V části poznámky pro zvláštní forma *název_sestavení* , který podporuje podmíněné zahrnutí metadat ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="661c7-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="661c7-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="661c7-123">Child Elements</span></span>  
  
|<span data-ttu-id="661c7-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="661c7-124">Element</span></span>|<span data-ttu-id="661c7-125">Popis</span><span class="sxs-lookup"><span data-stu-id="661c7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="661c7-126">\<Sestavení ></span><span class="sxs-lookup"><span data-stu-id="661c7-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="661c7-127">Použije zásady na všechny typy v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="661c7-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="661c7-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="661c7-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="661c7-129">Použije zásady na všechny typy v konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="661c7-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="661c7-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="661c7-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="661c7-131">Použije zásady na konkrétní typ, jako je například třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="661c7-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="661c7-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="661c7-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="661c7-133">Použije zásady na Konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="661c7-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="661c7-134">Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může použít k definování zásad pro `List<String>` typu.</span><span class="sxs-lookup"><span data-stu-id="661c7-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="661c7-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="661c7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="661c7-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="661c7-136">Element</span></span>|<span data-ttu-id="661c7-137">Popis</span><span class="sxs-lookup"><span data-stu-id="661c7-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="661c7-138">\<Direktivy ></span><span class="sxs-lookup"><span data-stu-id="661c7-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="661c7-139">Kořenový prvek souboru direktiv modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="661c7-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="661c7-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="661c7-140">Remarks</span></span>  
 <span data-ttu-id="661c7-141">[ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula, jeden nebo více `<Library>` elementy.</span><span class="sxs-lookup"><span data-stu-id="661c7-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="661c7-142">`<Library>` Prvek slouží jako kontejner pro definování prvky programu, jejichž metadat je potřeba za běhu; tento element není vyjádření zásad.</span><span class="sxs-lookup"><span data-stu-id="661c7-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="661c7-143">V době kompilace, kompilačních nástrojů hledání pouze v knihovně, které jsou určené `<Library>` – element pro prvky programu identifikován jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="661c7-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="661c7-144">Naproti tomu kompilátoru nástroje hledání všech knihoven, včetně.NET Framework základní knihovny, pro prvky programu identifikovaný podřízených elementů [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="661c7-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="661c7-145">`<Library>` direktivy může podmíněně využít.</span><span class="sxs-lookup"><span data-stu-id="661c7-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="661c7-146">Pokud název `<Library>` prvek začíná a končí s hvězdičkou (\*), `<Library>` – direktiva má vliv pouze v případě, že sestavení určena v rozsahu mezi hvězdičky odkazuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="661c7-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="661c7-147">Například následující direktivy modulu runtime platí jenom v případě, že Utillities.dll sestavení odkazuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="661c7-147">For example, the following runtime directive applies only if the Utillities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="661c7-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="661c7-148">See also</span></span>
- [<span data-ttu-id="661c7-149">\<Aplikace > – Element</span><span class="sxs-lookup"><span data-stu-id="661c7-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)
- [<span data-ttu-id="661c7-150">\<Direktivy > – Element</span><span class="sxs-lookup"><span data-stu-id="661c7-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)
- [<span data-ttu-id="661c7-151">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="661c7-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="661c7-152">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="661c7-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
