---
title: <Property> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128212"
---
# <a name="property-element-net-native"></a><span data-ttu-id="e131e-102">Element > vlastnosti \<(.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e131e-102">\<Property> Element (.NET Native)</span></span>
<span data-ttu-id="e131e-103">Aplikuje zásady reflexe za běhu na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e131e-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e131e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e131e-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e131e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e131e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e131e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e131e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e131e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e131e-107">Attributes</span></span>  
  
|<span data-ttu-id="e131e-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="e131e-108">Attribute</span></span>|<span data-ttu-id="e131e-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="e131e-109">Attribute type</span></span>|<span data-ttu-id="e131e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e131e-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e131e-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="e131e-111">General</span></span>|<span data-ttu-id="e131e-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e131e-112">Required attribute.</span></span> <span data-ttu-id="e131e-113">Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e131e-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="e131e-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="e131e-114">Reflection</span></span>|<span data-ttu-id="e131e-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e131e-115">Optional attribute.</span></span> <span data-ttu-id="e131e-116">Řídí dotazování pro informace o nebo vytváření výčtu vlastnosti, ale neumožňuje žádný dynamický přístup v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e131e-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e131e-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="e131e-117">Reflection</span></span>|<span data-ttu-id="e131e-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e131e-118">Optional attribute.</span></span> <span data-ttu-id="e131e-119">Řídí přístup za běhu k vlastnosti pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="e131e-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="e131e-120">Tato zásada zajišťuje, že vlastnost může být v době běhu nastavena nebo načtena dynamicky.</span><span class="sxs-lookup"><span data-stu-id="e131e-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="e131e-121">Serializace</span><span class="sxs-lookup"><span data-stu-id="e131e-121">Serialization</span></span>|<span data-ttu-id="e131e-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e131e-122">Optional attribute.</span></span> <span data-ttu-id="e131e-123">Řídí přístup za běhu k vlastnosti, která umožňuje serializaci instancí typů pomocí knihoven, jako je například serializátor JSON Newtonsoft nebo který se má použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="e131e-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e131e-124">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="e131e-124">Name attribute</span></span>  
  
|<span data-ttu-id="e131e-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e131e-125">Value</span></span>|<span data-ttu-id="e131e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="e131e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e131e-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="e131e-127">*method_name*</span></span>|<span data-ttu-id="e131e-128">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e131e-128">The property name.</span></span> <span data-ttu-id="e131e-129">Typ vlastnosti je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="e131e-129">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e131e-130">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="e131e-130">All other attributes</span></span>  
  
|<span data-ttu-id="e131e-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e131e-131">Value</span></span>|<span data-ttu-id="e131e-132">Popis</span><span class="sxs-lookup"><span data-stu-id="e131e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e131e-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e131e-133">*policy_setting*</span></span>|<span data-ttu-id="e131e-134">Nastavení, které se má použít pro tento typ zásad pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="e131e-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="e131e-135">Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`.</span><span class="sxs-lookup"><span data-stu-id="e131e-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e131e-136">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e131e-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e131e-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e131e-137">Child Elements</span></span>  
 <span data-ttu-id="e131e-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="e131e-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e131e-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e131e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e131e-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="e131e-140">Element</span></span>|<span data-ttu-id="e131e-141">Popis</span><span class="sxs-lookup"><span data-stu-id="e131e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e131e-142">Typ\<</span><span class="sxs-lookup"><span data-stu-id="e131e-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="e131e-143">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="e131e-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="e131e-144">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="e131e-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e131e-145">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="e131e-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e131e-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e131e-146">Remarks</span></span>  
 <span data-ttu-id="e131e-147">Pokud zásada vlastnosti není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="e131e-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e131e-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="e131e-148">Example</span></span>  
 <span data-ttu-id="e131e-149">Následující příklad používá reflexi pro vytvoření instance objektu `Book` a zobrazení hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="e131e-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="e131e-150">Původní soubor default. Rd. XML pro projekt se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="e131e-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="e131e-151">Soubor používá `All` hodnotu na zásady `Activate` pro třídu `Book`, která umožňuje přístup ke konstruktorům třídy prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="e131e-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="e131e-152">Zásady `Browse` pro třídu `Book` jsou zděděny z jejího nadřazeného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e131e-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="e131e-153">Tato nastavení je nastavená na `Required Public`, která zpřístupňuje metadata v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e131e-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="e131e-154">Následuje zdrojový kód pro příklad.</span><span class="sxs-lookup"><span data-stu-id="e131e-154">The following is the source code for the example.</span></span> <span data-ttu-id="e131e-155">Proměnná `outputBlock` představuje ovládací prvek <xref:Windows.UI.Xaml.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="e131e-155">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="e131e-156">Kompilace a spuštění tohoto příkladu však vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="e131e-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="e131e-157">I když jsme k dispozici metadata pro `Book` typ, nedokázali jsme využít dynamicky dostupné implementace vlastností getter.</span><span class="sxs-lookup"><span data-stu-id="e131e-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="e131e-158">Tuto chybu můžeme opravit jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="e131e-158">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="e131e-159">definováním `Dynamic` zásad pro `Book` typu v [\<typu >](type-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e131e-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="e131e-160">Přidáním vnořené [\<vlastnosti >](property-element-net-native.md) elementu pro každou vlastnost, jejíž metoda getter by chtěla vyvolat, jako následující soubor default. Rd. XML.</span><span class="sxs-lookup"><span data-stu-id="e131e-160">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e131e-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e131e-161">See also</span></span>

- [<span data-ttu-id="e131e-162">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e131e-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e131e-163">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e131e-163">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e131e-164">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e131e-164">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
