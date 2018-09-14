---
title: Element &lt;Property&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ed75d377814a740edece2b6a69e44acbd8ef0c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527708"
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="7d318-102">Element &lt;Property&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7d318-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="7d318-103">Vlastnost se týká zásady reflexe modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7d318-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d318-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d318-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d318-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d318-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7d318-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d318-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d318-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d318-107">Attributes</span></span>  
  
|<span data-ttu-id="7d318-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d318-108">Attribute</span></span>|<span data-ttu-id="7d318-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="7d318-109">Attribute type</span></span>|<span data-ttu-id="7d318-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7d318-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7d318-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="7d318-111">General</span></span>|<span data-ttu-id="7d318-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7d318-112">Required attribute.</span></span> <span data-ttu-id="7d318-113">Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d318-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="7d318-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7d318-114">Reflection</span></span>|<span data-ttu-id="7d318-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7d318-115">Optional attribute.</span></span> <span data-ttu-id="7d318-116">Ovládací prvky dotazování na informace o nebo vytváření výčtu vlastnost, ale neumožňuje dynamické přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="7d318-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="7d318-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7d318-117">Reflection</span></span>|<span data-ttu-id="7d318-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7d318-118">Optional attribute.</span></span> <span data-ttu-id="7d318-119">Modul runtime řídí přístup k vlastnosti, které chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="7d318-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="7d318-120">Tato zásada zajistí, že vlastnost můžete nastavit nebo načíst dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="7d318-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="7d318-121">Serializace</span><span class="sxs-lookup"><span data-stu-id="7d318-121">Serialization</span></span>|<span data-ttu-id="7d318-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7d318-122">Optional attribute.</span></span> <span data-ttu-id="7d318-123">Určuje runtime přístup k vlastnosti, které chcete povolit instance typu bylo serializováno modulem knihoven, jako je například serializátor Newtonsoft JSON nebo má být použit pro vytváření datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="7d318-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7d318-124">Název atributu</span><span class="sxs-lookup"><span data-stu-id="7d318-124">Name attribute</span></span>  
  
|<span data-ttu-id="7d318-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7d318-125">Value</span></span>|<span data-ttu-id="7d318-126">Popis</span><span class="sxs-lookup"><span data-stu-id="7d318-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d318-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="7d318-127">*method_name*</span></span>|<span data-ttu-id="7d318-128">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7d318-128">The property name.</span></span> <span data-ttu-id="7d318-129">Typ vlastnosti je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7d318-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7d318-130">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="7d318-130">All other attributes</span></span>  
  
|<span data-ttu-id="7d318-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7d318-131">Value</span></span>|<span data-ttu-id="7d318-132">Popis</span><span class="sxs-lookup"><span data-stu-id="7d318-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d318-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7d318-133">*policy_setting*</span></span>|<span data-ttu-id="7d318-134">Toto nastavení platí pro tento typ zásad pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d318-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="7d318-135">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="7d318-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="7d318-136">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7d318-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d318-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d318-137">Child Elements</span></span>  
 <span data-ttu-id="7d318-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d318-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d318-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d318-139">Parent Elements</span></span>  
  
|<span data-ttu-id="7d318-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d318-140">Element</span></span>|<span data-ttu-id="7d318-141">Popis</span><span class="sxs-lookup"><span data-stu-id="7d318-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d318-142">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="7d318-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="7d318-143">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7d318-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="7d318-144">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="7d318-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="7d318-145">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7d318-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d318-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d318-146">Remarks</span></span>  
 <span data-ttu-id="7d318-147">Pokud nejsou výslovně definované vlastnosti zásady, dědí zásady modulu runtime objektů svého nadřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="7d318-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d318-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d318-148">Example</span></span>  
 <span data-ttu-id="7d318-149">Následující příklad používá reflexi pro vytvoření instance `Book` objektů a zobrazení jeho hodnotám vlastností.</span><span class="sxs-lookup"><span data-stu-id="7d318-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="7d318-150">Původní soubor default.rd.xml projektu se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="7d318-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="7d318-151">Soubor se vztahuje `All` hodnota, která se `Activate` zásady pro `Book` třídu, která umožňuje přístup ke třídě konstruktory prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="7d318-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="7d318-152">`Browse` Zásady `Book` třída dědí z jeho nadřazeného oboru.</span><span class="sxs-lookup"><span data-stu-id="7d318-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="7d318-153">Je nastavené na `Required Public`, který zpřístupňuje metadat v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7d318-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="7d318-154">Následující je zdrojový kód pro příklad.</span><span class="sxs-lookup"><span data-stu-id="7d318-154">The following is the source code for the example.</span></span> <span data-ttu-id="7d318-155">`outputBlock` Představuje proměnnou [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7d318-155">The `outputBlock` variable represents a [TextBlock](https://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="7d318-156">Ale vyvolá výjimku kompilace a spuštění tohoto příkladu [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky.</span><span class="sxs-lookup"><span data-stu-id="7d318-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="7d318-157">I když jsme metadat `Book` typu k dispozici, jste nepovedlo se nám zpřístupnit implementace gettery vlastností dynamicky.</span><span class="sxs-lookup"><span data-stu-id="7d318-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="7d318-158">Tuto chybu můžeme opravit buď v jedné ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="7d318-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="7d318-159">definováním `Dynamic` zásady pro `Book` zadejte jeho [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7d318-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="7d318-160">Přidáním vnořený [ \<vlastnost >](../../../docs/framework/net-native/property-element-net-native.md) – element pro každou vlastnost, jejíž metoda getter, rádi bychom vyvolat, protože následující soubor default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="7d318-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7d318-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d318-161">See Also</span></span>  
 [<span data-ttu-id="7d318-162">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7d318-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="7d318-163">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7d318-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="7d318-164">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7d318-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
