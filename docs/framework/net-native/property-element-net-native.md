---
title: <Property>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
ms.openlocfilehash: b9bc89804a872dddf1a56c2a3dadc9c3df4f5fd1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128212"
---
# <a name="property-element-net-native"></a><span data-ttu-id="33cda-102">\<Property>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="33cda-102">\<Property> Element (.NET Native)</span></span>
<span data-ttu-id="33cda-103">Aplikuje zásady reflexe za běhu na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="33cda-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33cda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33cda-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33cda-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33cda-105">Attributes and Elements</span></span>  
 <span data-ttu-id="33cda-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33cda-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33cda-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="33cda-107">Attributes</span></span>  
  
|<span data-ttu-id="33cda-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="33cda-108">Attribute</span></span>|<span data-ttu-id="33cda-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="33cda-109">Attribute type</span></span>|<span data-ttu-id="33cda-110">Description</span><span class="sxs-lookup"><span data-stu-id="33cda-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="33cda-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="33cda-111">General</span></span>|<span data-ttu-id="33cda-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="33cda-112">Required attribute.</span></span> <span data-ttu-id="33cda-113">Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="33cda-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="33cda-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="33cda-114">Reflection</span></span>|<span data-ttu-id="33cda-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="33cda-115">Optional attribute.</span></span> <span data-ttu-id="33cda-116">Řídí dotazování pro informace o nebo vytváření výčtu vlastnosti, ale neumožňuje žádný dynamický přístup v době běhu.</span><span class="sxs-lookup"><span data-stu-id="33cda-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="33cda-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="33cda-117">Reflection</span></span>|<span data-ttu-id="33cda-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="33cda-118">Optional attribute.</span></span> <span data-ttu-id="33cda-119">Řídí přístup za běhu k vlastnosti pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="33cda-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="33cda-120">Tato zásada zajišťuje, že vlastnost může být v době běhu nastavena nebo načtena dynamicky.</span><span class="sxs-lookup"><span data-stu-id="33cda-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="33cda-121">Serializace</span><span class="sxs-lookup"><span data-stu-id="33cda-121">Serialization</span></span>|<span data-ttu-id="33cda-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="33cda-122">Optional attribute.</span></span> <span data-ttu-id="33cda-123">Řídí přístup za běhu k vlastnosti, která umožňuje serializaci instancí typů pomocí knihoven, jako je například serializátor JSON Newtonsoft nebo který se má použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="33cda-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="33cda-124">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="33cda-124">Name attribute</span></span>  
  
|<span data-ttu-id="33cda-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="33cda-125">Value</span></span>|<span data-ttu-id="33cda-126">Description</span><span class="sxs-lookup"><span data-stu-id="33cda-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33cda-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="33cda-127">*method_name*</span></span>|<span data-ttu-id="33cda-128">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="33cda-128">The property name.</span></span> <span data-ttu-id="33cda-129">Typ vlastnosti je definován nadřazeným [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem nebo elementem.</span><span class="sxs-lookup"><span data-stu-id="33cda-129">The type of the property is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="33cda-130">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="33cda-130">All other attributes</span></span>  
  
|<span data-ttu-id="33cda-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="33cda-131">Value</span></span>|<span data-ttu-id="33cda-132">Description</span><span class="sxs-lookup"><span data-stu-id="33cda-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33cda-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="33cda-133">*policy_setting*</span></span>|<span data-ttu-id="33cda-134">Nastavení, které se má použít pro tento typ zásad pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="33cda-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="33cda-135">Možné hodnoty jsou `Auto` , `Excluded` , `Included` a `Required` .</span><span class="sxs-lookup"><span data-stu-id="33cda-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="33cda-136">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="33cda-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33cda-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33cda-137">Child Elements</span></span>  
 <span data-ttu-id="33cda-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="33cda-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33cda-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="33cda-139">Parent Elements</span></span>  
  
|<span data-ttu-id="33cda-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="33cda-140">Element</span></span>|<span data-ttu-id="33cda-141">Description</span><span class="sxs-lookup"><span data-stu-id="33cda-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="33cda-142">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="33cda-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="33cda-143">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="33cda-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33cda-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33cda-144">Remarks</span></span>  
 <span data-ttu-id="33cda-145">Pokud zásada vlastnosti není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="33cda-145">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33cda-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="33cda-146">Example</span></span>  
 <span data-ttu-id="33cda-147">Následující příklad používá reflexi pro vytvoření instance `Book` objektu a zobrazení hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="33cda-147">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="33cda-148">Původní soubor default. Rd. XML pro projekt se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="33cda-148">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="33cda-149">Soubor používá `All` hodnotu pro `Activate` zásadu pro `Book` třídu, která umožňuje přístup k konstruktorům třídy prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="33cda-149">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="33cda-150">`Browse`Zásady pro `Book` třídu jsou zděděny z jejího nadřazeného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="33cda-150">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="33cda-151">To je nastaveno na `Required Public` , díky čemuž jsou k dispozici metadata za běhu.</span><span class="sxs-lookup"><span data-stu-id="33cda-151">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="33cda-152">Následuje zdrojový kód pro příklad.</span><span class="sxs-lookup"><span data-stu-id="33cda-152">The following is the source code for the example.</span></span> <span data-ttu-id="33cda-153">`outputBlock`Proměnná představuje <xref:Windows.UI.Xaml.Controls.TextBlock> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="33cda-153">The `outputBlock` variable represents a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="33cda-154">Kompilace a spuštění tohoto příkladu však vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="33cda-154">However, compiling and executing this example throws a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="33cda-155">I když jsme udělali metadata pro daný `Book` typ, nedokázali jsme využít dynamicky dostupné implementace vlastností getter.</span><span class="sxs-lookup"><span data-stu-id="33cda-155">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="33cda-156">Tuto chybu můžeme opravit jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="33cda-156">We can correct this error by either in one of two ways:</span></span>  
  
- <span data-ttu-id="33cda-157">definováním `Dynamic` zásad pro `Book` typ v jeho [\<Type>](type-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="33cda-157">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](type-element-net-native.md) element.</span></span>  
  
- <span data-ttu-id="33cda-158">Přidáním vnořeného [\<Property>](property-element-net-native.md) prvku pro každou vlastnost, jejíž getter chceme vyvolat, jako následující soubor default. Rd. XML.</span><span class="sxs-lookup"><span data-stu-id="33cda-158">By adding a nested [\<Property>](property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33cda-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="33cda-159">See also</span></span>

- [<span data-ttu-id="33cda-160">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="33cda-160">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="33cda-161">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="33cda-161">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="33cda-162">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="33cda-162">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
