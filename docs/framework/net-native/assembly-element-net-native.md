---
title: Element &lt;Assembly&gt; (.NET Native)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34e49e4d11f442f15db2f06b330b8b84a165a08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="ltassemblygt-element-net-native"></a><span data-ttu-id="dff6a-102">Element &lt;Assembly&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="dff6a-102">&lt;Assembly&gt; Element (.NET Native)</span></span>
<span data-ttu-id="dff6a-103">Modul runtime reflexe zásad platí pro všechny typy v zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="dff6a-103">Applies runtime reflection policy to all the types in a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dff6a-104">Syntax</span></span>  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting" />  
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dff6a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dff6a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dff6a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dff6a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dff6a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="dff6a-107">Attributes</span></span>  
  
|<span data-ttu-id="dff6a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="dff6a-108">Attribute</span></span>|<span data-ttu-id="dff6a-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="dff6a-109">Attribute type</span></span>|<span data-ttu-id="dff6a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dff6a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="dff6a-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="dff6a-111">General</span></span>|<span data-ttu-id="dff6a-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-112">Required attribute.</span></span> <span data-ttu-id="dff6a-113">Určuje jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="dff6a-113">Specifies the simple name of an assembly.</span></span>|  
|`Activate`|<span data-ttu-id="dff6a-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="dff6a-114">Reflection</span></span>|<span data-ttu-id="dff6a-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-115">Optional attribute.</span></span> <span data-ttu-id="dff6a-116">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="dff6a-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="dff6a-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="dff6a-117">Reflection</span></span>|<span data-ttu-id="dff6a-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-118">Optional attribute.</span></span> <span data-ttu-id="dff6a-119">Ovládací prvky dotazování na informace o nebo vytváření výčtu typy v sestavení, ale neumožňuje žádné dynamické přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-119">Controls querying for information about or enumerating the types in the assembly, but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="dff6a-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="dff6a-120">Reflection</span></span>|<span data-ttu-id="dff6a-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-121">Optional attribute.</span></span> <span data-ttu-id="dff6a-122">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="dff6a-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="dff6a-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="dff6a-123">Serialization</span></span>|<span data-ttu-id="dff6a-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-124">Optional attribute.</span></span> <span data-ttu-id="dff6a-125">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="dff6a-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="dff6a-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="dff6a-126">Serialization</span></span>|<span data-ttu-id="dff6a-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-127">Optional attribute.</span></span> <span data-ttu-id="dff6a-128">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="dff6a-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="dff6a-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="dff6a-129">Serialization</span></span>|<span data-ttu-id="dff6a-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-130">Optional attribute.</span></span> <span data-ttu-id="dff6a-131">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="dff6a-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="dff6a-132">Serializace</span><span class="sxs-lookup"><span data-stu-id="dff6a-132">Serialization</span></span>|<span data-ttu-id="dff6a-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-133">Optional attribute.</span></span> <span data-ttu-id="dff6a-134">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="dff6a-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="dff6a-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="dff6a-135">Interop</span></span>|<span data-ttu-id="dff6a-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-136">Optional attribute.</span></span> <span data-ttu-id="dff6a-137">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="dff6a-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="dff6a-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="dff6a-138">Interop</span></span>|<span data-ttu-id="dff6a-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-139">Optional attribute.</span></span> <span data-ttu-id="dff6a-140">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="dff6a-141">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="dff6a-141">Interop</span></span>|<span data-ttu-id="dff6a-142">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dff6a-142">Optional attribute.</span></span> <span data-ttu-id="dff6a-143">Ovládací prvky zásady pro zařazování struktur nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="dff6a-144">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="dff6a-144">Name attribute</span></span>  
  
|<span data-ttu-id="dff6a-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dff6a-145">Value</span></span>|<span data-ttu-id="dff6a-146">Popis</span><span class="sxs-lookup"><span data-stu-id="dff6a-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dff6a-147">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="dff6a-147">*assembly_name*</span></span>|<span data-ttu-id="dff6a-148">Jednoduchý název sestavení, bez jeho přípona souboru.</span><span class="sxs-lookup"><span data-stu-id="dff6a-148">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="dff6a-149">Tento atribut odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dff6a-149">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="dff6a-150">Název sestavení s názvem Extensions.dll je například "Rozšíření".</span><span class="sxs-lookup"><span data-stu-id="dff6a-150">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span><br /><br /> <span data-ttu-id="dff6a-151">Můžete také určit řetězcového literálu `*Application*` uplatňovat zásady na všechna sestavení v balíčku aplikace se, zda tato sestavení jsou načteny, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="dff6a-151">You can also specify the literal string `*Application*` to apply policy to all assemblies in your app package, whether those assemblies are loaded or not.</span></span> <span data-ttu-id="dff6a-152">`*Application*` nikdy platí zásady pro sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dff6a-152">`*Application*` never applies policy to .NET Framework assemblies.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="dff6a-153">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="dff6a-153">All other attributes</span></span>  
  
|<span data-ttu-id="dff6a-154">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dff6a-154">Value</span></span>|<span data-ttu-id="dff6a-155">Popis</span><span class="sxs-lookup"><span data-stu-id="dff6a-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dff6a-156">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="dff6a-156">*policy_setting*</span></span>|<span data-ttu-id="dff6a-157">Nastavení, které chcete použít pro tento typ zásad pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="dff6a-157">The setting to apply to this policy type for all types in the assembly.</span></span> <span data-ttu-id="dff6a-158">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="dff6a-158">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="dff6a-159">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="dff6a-159">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dff6a-160">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dff6a-160">Child Elements</span></span>  
  
|<span data-ttu-id="dff6a-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="dff6a-161">Element</span></span>|<span data-ttu-id="dff6a-162">Popis</span><span class="sxs-lookup"><span data-stu-id="dff6a-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dff6a-163">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="dff6a-163">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)|<span data-ttu-id="dff6a-164">Reflexe zásad platí pro všechny typy v oboru názvů podřízené.</span><span class="sxs-lookup"><span data-stu-id="dff6a-164">Applies reflection policy to all types in a child namespace.</span></span>|  
|[<span data-ttu-id="dff6a-165">\<Type></span><span class="sxs-lookup"><span data-stu-id="dff6a-165">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="dff6a-166">Reflexe zásada se vztahuje na typ.</span><span class="sxs-lookup"><span data-stu-id="dff6a-166">Applies reflection policy to a type.</span></span>|  
|[<span data-ttu-id="dff6a-167">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="dff6a-167">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="dff6a-168">Reflexe zásada se vztahuje na vytvořený obecného typu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-168">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dff6a-169">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dff6a-169">Parent Elements</span></span>  
  
|<span data-ttu-id="dff6a-170">Prvek</span><span class="sxs-lookup"><span data-stu-id="dff6a-170">Element</span></span>|<span data-ttu-id="dff6a-171">Popis</span><span class="sxs-lookup"><span data-stu-id="dff6a-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dff6a-172">\<Aplikace ></span><span class="sxs-lookup"><span data-stu-id="dff6a-172">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="dff6a-173">Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-173">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="dff6a-174">[ \<Aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element může obsahovat nula, jednu nebo více `<Assembly>` elementy.</span><span class="sxs-lookup"><span data-stu-id="dff6a-174">The [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element can have zero, one, or more `<Assembly>` elements.</span></span>|  
|[<span data-ttu-id="dff6a-175">\<Library></span><span class="sxs-lookup"><span data-stu-id="dff6a-175">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="dff6a-176">Definuje sestavení, které obsahuje typy a členy typu jejichž metadata jsou k dispozici pro reflexi za běhu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-176">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="dff6a-177">[ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element může obsahovat nula nebo jedna `<Assembly>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dff6a-177">The [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element can have zero or one `<Assembly>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dff6a-178">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dff6a-178">Remarks</span></span>  
 <span data-ttu-id="dff6a-179">`<Assembly>` Element definuje zásady modulu runtime pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="dff6a-179">The `<Assembly>` element defines runtime policy for all the types in an assembly.</span></span> <span data-ttu-id="dff6a-180">Liší se od [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) element, který určuje knihovnu, ale závisí na její podřízené elementy definovat zásady reflexe modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="dff6a-180">It differs from the [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element, which specifies a library but depends on its child elements to define runtime reflection policy.</span></span> <span data-ttu-id="dff6a-181">`<Assembly>` Element platí pro všechny typy v sestavení, pokud jsou přepsány podřízený element.</span><span class="sxs-lookup"><span data-stu-id="dff6a-181">The `<Assembly>` element applies to all the types in an assembly unless they are overridden by a child element.</span></span>  
  
 <span data-ttu-id="dff6a-182">Následující příklad ukazuje, jak můžete použít zásady modulu runtime pro všechny typy v sestavení v rámci vašeho balíčku aplikace přiřazením `Name` hodnotu atributu "* aplikace\*".</span><span class="sxs-lookup"><span data-stu-id="dff6a-182">The following example shows how you can apply runtime policy to all the types in assemblies within your app package by assigning the `Name` attribute a value of "*Application\*".</span></span> <span data-ttu-id="dff6a-183">`<Assembly>` Element musí být podřízenou [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="dff6a-183">The `<Assembly>` element must be a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 <span data-ttu-id="dff6a-184">`Activate`, `Browse`, `Dynamic`, A `Serialize` atributy jsou nepovinné.</span><span class="sxs-lookup"><span data-stu-id="dff6a-184">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="dff6a-185">Ale `<Assembly>` element musí obsahovat alespoň jeden z těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="dff6a-185">However, the `<Assembly>` element must contain at least one of these attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff6a-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="dff6a-186">See Also</span></span>  
 [<span data-ttu-id="dff6a-187">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="dff6a-187">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="dff6a-188">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="dff6a-188">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="dff6a-189">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="dff6a-189">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
