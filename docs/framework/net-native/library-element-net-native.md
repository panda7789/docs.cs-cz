---
title: <Library>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128367"
---
# <a name="library-element-net-native"></a><span data-ttu-id="58c97-102">\<Library>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="58c97-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="58c97-103">Definuje sestavení, které obsahuje typy a členy typů, jejichž metadata jsou k dispozici pro reflexi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="58c97-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="58c97-104">Element \<Directives></span><span class="sxs-lookup"><span data-stu-id="58c97-104">\<Directives> Element</span></span>  
<span data-ttu-id="58c97-105">Element \<Library></span><span class="sxs-lookup"><span data-stu-id="58c97-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c97-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58c97-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58c97-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58c97-107">Attributes and Elements</span></span>  
 <span data-ttu-id="58c97-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58c97-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58c97-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="58c97-109">Attributes</span></span>  
  
|<span data-ttu-id="58c97-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="58c97-110">Attribute</span></span>|<span data-ttu-id="58c97-111">Popis</span><span class="sxs-lookup"><span data-stu-id="58c97-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="58c97-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="58c97-112">Required attribute.</span></span> <span data-ttu-id="58c97-113">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="58c97-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="58c97-114">Podřízené elementy tohoto `<Library>` elementu definují zásady reflexe modulu runtime pro typy a členy typů nalezené v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="58c97-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="58c97-115">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="58c97-115">Name attribute</span></span>  
  
|<span data-ttu-id="58c97-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="58c97-116">Value</span></span>|<span data-ttu-id="58c97-117">Description</span><span class="sxs-lookup"><span data-stu-id="58c97-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="58c97-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="58c97-118">*assembly_name*</span></span>|<span data-ttu-id="58c97-119">Jednoduchý název sestavení bez přípony souboru.</span><span class="sxs-lookup"><span data-stu-id="58c97-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="58c97-120">Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58c97-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="58c97-121">Například název sestavení s názvem Extensions. dll je "Extensions".</span><span class="sxs-lookup"><span data-stu-id="58c97-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="58c97-122">Zvláštní podobu *assembly_name* , která podporuje podmíněné zahrnutí metadat ze sestavení, naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="58c97-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58c97-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58c97-123">Child Elements</span></span>  
  
|<span data-ttu-id="58c97-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="58c97-124">Element</span></span>|<span data-ttu-id="58c97-125">Description</span><span class="sxs-lookup"><span data-stu-id="58c97-125">Description</span></span>|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="58c97-126">Použije zásady na všechny typy v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="58c97-126">Applies policy to all the types in a particular assembly.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="58c97-127">Použije zásady na všechny typy v konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="58c97-127">Applies policy to all the types in a particular namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="58c97-128">Použije zásady na konkrétní typ, jako je třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="58c97-128">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="58c97-129">Použije zásady na konstruovaný obecný typ.</span><span class="sxs-lookup"><span data-stu-id="58c97-129">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="58c97-130">Například [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element může být použit k definování zásad pro `List<String>` typ.</span><span class="sxs-lookup"><span data-stu-id="58c97-130">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58c97-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58c97-131">Parent Elements</span></span>  
  
|<span data-ttu-id="58c97-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="58c97-132">Element</span></span>|<span data-ttu-id="58c97-133">Description</span><span class="sxs-lookup"><span data-stu-id="58c97-133">Description</span></span>|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|<span data-ttu-id="58c97-134">Kořenový prvek souboru direktiv modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="58c97-134">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58c97-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58c97-135">Remarks</span></span>  
 <span data-ttu-id="58c97-136">[\<Directives>](directives-element-net-native.md)Element může obsahovat nula, jeden nebo více `<Library>` prvků.</span><span class="sxs-lookup"><span data-stu-id="58c97-136">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="58c97-137">`<Library>`Element slouží jako kontejner pro definování prvků programu, jejichž metadata jsou potřebná v době běhu; tento prvek neposkytuje expresní zásady.</span><span class="sxs-lookup"><span data-stu-id="58c97-137">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="58c97-138">V době kompilace Nástroj pro kompilátor vyhledává pouze knihovnu určenou `<Library>` prvkem pro prvky programu identifikované jeho podřízenými prvky.</span><span class="sxs-lookup"><span data-stu-id="58c97-138">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="58c97-139">Naproti tomu nástroje kompilátoru hledají všechny knihovny, základní knihovny including.NET Framework pro prvky programu identifikované podřízenými prvky [\<Application>](application-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="58c97-139">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="58c97-140">`<Library>`direktivy mohou být využívány podmíněně.</span><span class="sxs-lookup"><span data-stu-id="58c97-140">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="58c97-141">Pokud název `<Library>` elementu začíná a končí hvězdičkou ( \* ), `<Library>` má tato direktiva účinek pouze v případě, že je v aplikaci odkazováno na sestavení zadané mezi hvězdičkami.</span><span class="sxs-lookup"><span data-stu-id="58c97-141">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="58c97-142">Například následující direktiva modulu runtime platí pouze v případě, že aplikace odkazuje na sestavení Utilities. dll.</span><span class="sxs-lookup"><span data-stu-id="58c97-142">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58c97-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="58c97-143">See also</span></span>

- [<span data-ttu-id="58c97-144">\<Application>Objekt</span><span class="sxs-lookup"><span data-stu-id="58c97-144">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="58c97-145">\<Directives>Objekt</span><span class="sxs-lookup"><span data-stu-id="58c97-145">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="58c97-146">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="58c97-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="58c97-147">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="58c97-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
