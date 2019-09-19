---
title: <Library>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049650"
---
# <a name="library-element-net-native"></a><span data-ttu-id="b58b9-102">\<Element > knihovny (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b58b9-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="b58b9-103">Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b58b9-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="b58b9-104">\<Direktivy > element</span><span class="sxs-lookup"><span data-stu-id="b58b9-104">\<Directives> Element</span></span>  
<span data-ttu-id="b58b9-105">\<Element > knihovny</span><span class="sxs-lookup"><span data-stu-id="b58b9-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58b9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b58b9-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b58b9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b58b9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b58b9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b58b9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b58b9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b58b9-109">Attributes</span></span>  
  
|<span data-ttu-id="b58b9-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b58b9-110">Attribute</span></span>|<span data-ttu-id="b58b9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b58b9-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="b58b9-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b58b9-112">Required attribute.</span></span> <span data-ttu-id="b58b9-113">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="b58b9-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="b58b9-114">Podřízené elementy tohoto `<Library>` elementu definují zásady reflexe modulu runtime pro typy a členy typů nalezené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="b58b9-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="b58b9-115">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="b58b9-115">Name attribute</span></span>  
  
|<span data-ttu-id="b58b9-116">Value</span><span class="sxs-lookup"><span data-stu-id="b58b9-116">Value</span></span>|<span data-ttu-id="b58b9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b58b9-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b58b9-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="b58b9-118">*assembly_name*</span></span>|<span data-ttu-id="b58b9-119">Jednoduchý název sestavení bez přípony souboru.</span><span class="sxs-lookup"><span data-stu-id="b58b9-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="b58b9-120">Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b58b9-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b58b9-121">Například název sestavení s názvem Extensions. dll je "Extensions".</span><span class="sxs-lookup"><span data-stu-id="b58b9-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="b58b9-122">Zvláštní podobu *assembly_name* , která podporuje podmíněné zahrnutí metadat ze sestavení, naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="b58b9-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b58b9-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b58b9-123">Child Elements</span></span>  
  
|<span data-ttu-id="b58b9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b58b9-124">Element</span></span>|<span data-ttu-id="b58b9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b58b9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b58b9-126">\<> Sestavení</span><span class="sxs-lookup"><span data-stu-id="b58b9-126">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="b58b9-127">Použije zásady na všechny typy v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="b58b9-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="b58b9-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="b58b9-128">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="b58b9-129">Použije zásady na všechny typy v konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b58b9-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="b58b9-130">\<Zadejte ></span><span class="sxs-lookup"><span data-stu-id="b58b9-130">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="b58b9-131">Použije zásady na konkrétní typ, jako je třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="b58b9-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="b58b9-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="b58b9-132">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="b58b9-133">Použije zásady na konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="b58b9-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="b58b9-134">Například `List<String>` [ \<element TypeInstantiation >](typeinstantiation-element-net-native.md) lze použít k definování zásad pro typ.</span><span class="sxs-lookup"><span data-stu-id="b58b9-134">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b58b9-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b58b9-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b58b9-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="b58b9-136">Element</span></span>|<span data-ttu-id="b58b9-137">Popis</span><span class="sxs-lookup"><span data-stu-id="b58b9-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b58b9-138">\<> Direktiv</span><span class="sxs-lookup"><span data-stu-id="b58b9-138">\<Directives></span></span>](directives-element-net-native.md)|<span data-ttu-id="b58b9-139">Kořenový prvek souboru direktiv modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b58b9-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b58b9-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b58b9-140">Remarks</span></span>  
 <span data-ttu-id="b58b9-141">Direktivy > element může obsahovat nula, jeden nebo více `<Library>` prvků. [ \<](directives-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="b58b9-141">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="b58b9-142">`<Library>` Element slouží jako kontejner pro definování prvků programu, jejichž metadata jsou potřebná v době běhu; tento prvek neposkytuje expresní zásady.</span><span class="sxs-lookup"><span data-stu-id="b58b9-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="b58b9-143">V době kompilace Nástroj pro kompilátor vyhledává pouze knihovnu určenou `<Library>` prvkem pro prvky programu identifikované jeho podřízenými prvky.</span><span class="sxs-lookup"><span data-stu-id="b58b9-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="b58b9-144">Naproti tomu nástroje kompilátoru hledají všechny knihovny, základní knihovny including.NET Framework pro prvky programu identifikované podřízenými prvky [ \<aplikace >](application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b58b9-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="b58b9-145">`<Library>`direktivy mohou být využívány podmíněně.</span><span class="sxs-lookup"><span data-stu-id="b58b9-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="b58b9-146">Pokud název `<Library>` elementu začíná a končí hvězdičkou (\*), má tato `<Library>` direktiva účinek pouze v případě, že je v aplikaci odkazováno na sestavení zadané mezi hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="b58b9-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="b58b9-147">Například následující direktiva modulu runtime platí pouze v případě, že aplikace odkazuje na sestavení Utilities. dll.</span><span class="sxs-lookup"><span data-stu-id="b58b9-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b58b9-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b58b9-148">See also</span></span>

- [<span data-ttu-id="b58b9-149">\<> Element aplikace</span><span class="sxs-lookup"><span data-stu-id="b58b9-149">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="b58b9-150">\<Direktivy > element</span><span class="sxs-lookup"><span data-stu-id="b58b9-150">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="b58b9-151">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="b58b9-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b58b9-152">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="b58b9-152">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
