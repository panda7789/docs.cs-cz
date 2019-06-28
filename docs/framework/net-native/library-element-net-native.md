---
title: <Library> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce001ed25d7704301d7f809887a445e3492e93fc
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422540"
---
# <a name="library-element-net-native"></a><span data-ttu-id="eb5ef-102">\<Knihovna > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="eb5ef-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="eb5ef-103">Určuje sestavení, který obsahuje typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe v době běhu.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="eb5ef-104">\<Direktivy > – Element</span><span class="sxs-lookup"><span data-stu-id="eb5ef-104">\<Directives> Element</span></span>  
<span data-ttu-id="eb5ef-105">\<Knihovna > – Element</span><span class="sxs-lookup"><span data-stu-id="eb5ef-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb5ef-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb5ef-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb5ef-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eb5ef-107">Attributes and Elements</span></span>  
 <span data-ttu-id="eb5ef-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb5ef-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb5ef-109">Attributes</span></span>  
  
|<span data-ttu-id="eb5ef-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="eb5ef-110">Attribute</span></span>|<span data-ttu-id="eb5ef-111">Popis</span><span class="sxs-lookup"><span data-stu-id="eb5ef-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="eb5ef-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-112">Required attribute.</span></span> <span data-ttu-id="eb5ef-113">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="eb5ef-114">Podřízené prvky tohoto `<Library>` element definovat zásady reflexe modulu runtime pro typy a členy typů nalezena v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="eb5ef-115">Název atributu</span><span class="sxs-lookup"><span data-stu-id="eb5ef-115">Name attribute</span></span>  
  
|<span data-ttu-id="eb5ef-116">Value</span><span class="sxs-lookup"><span data-stu-id="eb5ef-116">Value</span></span>|<span data-ttu-id="eb5ef-117">Popis</span><span class="sxs-lookup"><span data-stu-id="eb5ef-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb5ef-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="eb5ef-118">*assembly_name*</span></span>|<span data-ttu-id="eb5ef-119">Jednoduchý název sestavení, bez jeho přípona souboru.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="eb5ef-120">Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="eb5ef-121">Název sestavení s názvem Extensions.dll je například "Rozšíření".</span><span class="sxs-lookup"><span data-stu-id="eb5ef-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="eb5ef-122">V části poznámky pro zvláštní forma *název_sestavení* , který podporuje podmíněné zahrnutí metadat ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb5ef-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eb5ef-123">Child Elements</span></span>  
  
|<span data-ttu-id="eb5ef-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="eb5ef-124">Element</span></span>|<span data-ttu-id="eb5ef-125">Popis</span><span class="sxs-lookup"><span data-stu-id="eb5ef-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb5ef-126">\<Sestavení ></span><span class="sxs-lookup"><span data-stu-id="eb5ef-126">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="eb5ef-127">Použije zásady na všechny typy v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="eb5ef-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="eb5ef-128">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="eb5ef-129">Použije zásady na všechny typy v konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="eb5ef-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="eb5ef-130">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="eb5ef-131">Použije zásady na konkrétní typ, jako je například třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="eb5ef-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="eb5ef-132">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="eb5ef-133">Použije zásady na Konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="eb5ef-134">Například [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element může použít k definování zásad pro `List<String>` typu.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-134">For example, a [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb5ef-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eb5ef-135">Parent Elements</span></span>  
  
|<span data-ttu-id="eb5ef-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="eb5ef-136">Element</span></span>|<span data-ttu-id="eb5ef-137">Popis</span><span class="sxs-lookup"><span data-stu-id="eb5ef-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb5ef-138">\<Direktivy ></span><span class="sxs-lookup"><span data-stu-id="eb5ef-138">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)|<span data-ttu-id="eb5ef-139">Kořenový prvek souboru direktiv modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb5ef-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb5ef-140">Remarks</span></span>  
 <span data-ttu-id="eb5ef-141">[ \<Direktivy >](../../../docs/framework/net-native/directives-element-net-native.md) element může obsahovat nula, jeden nebo více `<Library>` elementy.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-141">The [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="eb5ef-142">`<Library>` Prvek slouží jako kontejner pro definování prvky programu, jejichž metadat je potřeba za běhu; tento element není vyjádření zásad.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="eb5ef-143">V době kompilace, kompilačních nástrojů hledání pouze v knihovně, které jsou určené `<Library>` – element pro prvky programu identifikován jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="eb5ef-144">Naproti tomu kompilátoru nástroje hledání všech knihoven, včetně.NET Framework základní knihovny, pro prvky programu identifikovaný podřízených elementů [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="eb5ef-145">`<Library>` direktivy může podmíněně využít.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="eb5ef-146">Pokud název `<Library>` prvek začíná a končí s hvězdičkou (\*), `<Library>` – direktiva má vliv pouze v případě, že sestavení určena v rozsahu mezi hvězdičky odkazuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="eb5ef-147">Například následující direktivy modulu runtime platí jenom v případě, že Utilities.dll sestavení odkazuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eb5ef-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb5ef-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb5ef-148">See also</span></span>

- [<span data-ttu-id="eb5ef-149">\<Aplikace > – Element</span><span class="sxs-lookup"><span data-stu-id="eb5ef-149">\<Application> Element</span></span>](../../../docs/framework/net-native/application-element-net-native.md)
- [<span data-ttu-id="eb5ef-150">\<Direktivy > – Element</span><span class="sxs-lookup"><span data-stu-id="eb5ef-150">\<Directives> Element</span></span>](../../../docs/framework/net-native/directives-element-net-native.md)
- [<span data-ttu-id="eb5ef-151">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="eb5ef-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="eb5ef-152">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="eb5ef-152">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
