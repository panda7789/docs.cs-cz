---
title: <Method> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fdc4441a8a11df5427badfaea95edb0abe52bde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131713"
---
# <a name="method-element-net-native"></a><span data-ttu-id="6d87c-102">\<Metoda > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6d87c-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="6d87c-103">Použije zásady reflexe runtime konstruktoru nebo metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d87c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d87c-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d87c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d87c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d87c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d87c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d87c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d87c-107">Attributes</span></span>  
  
|<span data-ttu-id="6d87c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d87c-108">Attribute</span></span>|<span data-ttu-id="6d87c-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="6d87c-109">Attribute type</span></span>|<span data-ttu-id="6d87c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6d87c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="6d87c-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="6d87c-111">General</span></span>|<span data-ttu-id="6d87c-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d87c-112">Required attribute.</span></span> <span data-ttu-id="6d87c-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="6d87c-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="6d87c-114">General</span></span>|<span data-ttu-id="6d87c-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d87c-115">Optional attribute.</span></span> <span data-ttu-id="6d87c-116">Určuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-116">Specifies the method signature.</span></span> <span data-ttu-id="6d87c-117">Pokud více parametrů jsou k dispozici, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="6d87c-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="6d87c-118">Například následující `<Method>` element definuje zásady pro <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="6d87c-119">Pokud atribut chybí, direktivy modulu runtime se vztahuje na všechna přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="6d87c-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6d87c-120">Reflection</span></span>|<span data-ttu-id="6d87c-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d87c-121">Optional attribute.</span></span> <span data-ttu-id="6d87c-122">Ovládací prvky dotazování na informace o nebo vytváření výčtu metody, ale nepovolí všechny dynamické vyvolání za běhu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="6d87c-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6d87c-123">Reflection</span></span>|<span data-ttu-id="6d87c-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6d87c-124">Optional attribute.</span></span> <span data-ttu-id="6d87c-125">Ovládací prvky runtime přístup k konstruktoru nebo metody, které chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="6d87c-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="6d87c-126">Tato zásada zajistí, že člen může být vyvolána dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6d87c-127">Název atributu</span><span class="sxs-lookup"><span data-stu-id="6d87c-127">Name attribute</span></span>  
  
|<span data-ttu-id="6d87c-128">Value</span><span class="sxs-lookup"><span data-stu-id="6d87c-128">Value</span></span>|<span data-ttu-id="6d87c-129">Popis</span><span class="sxs-lookup"><span data-stu-id="6d87c-129">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="6d87c-130">method_name</span><span class="sxs-lookup"><span data-stu-id="6d87c-130">method_name</span></span>*|<span data-ttu-id="6d87c-131">Název metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-131">The method name.</span></span> <span data-ttu-id="6d87c-132">Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-132">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="6d87c-133">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="6d87c-133">Signature attribute</span></span>  
  
|<span data-ttu-id="6d87c-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6d87c-134">Value</span></span>|<span data-ttu-id="6d87c-135">Popis</span><span class="sxs-lookup"><span data-stu-id="6d87c-135">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="6d87c-136">method_signature</span><span class="sxs-lookup"><span data-stu-id="6d87c-136">method_signature</span></span>*|<span data-ttu-id="6d87c-137">Typy parametrů, které tvoří podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="6d87c-138">Více parametrů jsou odděleny čárkami, například `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="6d87c-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="6d87c-139">Názvy typů parametrů by měl být úplný.</span><span class="sxs-lookup"><span data-stu-id="6d87c-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="6d87c-140">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="6d87c-140">All other attributes</span></span>  
  
|<span data-ttu-id="6d87c-141">Value</span><span class="sxs-lookup"><span data-stu-id="6d87c-141">Value</span></span>|<span data-ttu-id="6d87c-142">Popis</span><span class="sxs-lookup"><span data-stu-id="6d87c-142">Description</span></span>|  
|-----------|-----------------|  
|*<span data-ttu-id="6d87c-143">policy_setting</span><span class="sxs-lookup"><span data-stu-id="6d87c-143">policy_setting</span></span>*|<span data-ttu-id="6d87c-144">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="6d87c-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="6d87c-145">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="6d87c-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="6d87c-146">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6d87c-146">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d87c-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d87c-147">Child Elements</span></span>  
  
|<span data-ttu-id="6d87c-148">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d87c-148">Element</span></span>|<span data-ttu-id="6d87c-149">Popis</span><span class="sxs-lookup"><span data-stu-id="6d87c-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d87c-150">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="6d87c-150">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)|<span data-ttu-id="6d87c-151">Použije zásady na typ argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="6d87c-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="6d87c-152">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="6d87c-152">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|<span data-ttu-id="6d87c-153">Použije zásady na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="6d87c-154">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="6d87c-154">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="6d87c-155">Použije zásady na typ, pokud tyto zásady se nastavily pro metodu reprezentovanou obsahující `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="6d87c-156">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="6d87c-156">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|<span data-ttu-id="6d87c-157">Použije zásady na typ zastoupený <xref:System.Type> argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="6d87c-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d87c-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d87c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="6d87c-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d87c-159">Element</span></span>|<span data-ttu-id="6d87c-160">Popis</span><span class="sxs-lookup"><span data-stu-id="6d87c-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d87c-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="6d87c-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6d87c-162">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="6d87c-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="6d87c-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="6d87c-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="6d87c-164">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="6d87c-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d87c-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d87c-165">Remarks</span></span>  
 <span data-ttu-id="6d87c-166">A `<Method>` elementu z obecné metody své zásady platí pro všechny instance, nesmí být svými vlastními zásadami.</span><span class="sxs-lookup"><span data-stu-id="6d87c-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="6d87c-167">Můžete použít `Signature` atribut určení zásad pro konkrétní metody přetížení.</span><span class="sxs-lookup"><span data-stu-id="6d87c-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="6d87c-168">Jinak, pokud `Signature` atribut chybí, direktivy modulu runtime se vztahuje na všechna přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="6d87c-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="6d87c-169">Nejde definovat zásady reflexe modulu runtime pro konstruktor s použitím `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="6d87c-170">Místo toho použijte `Activate` atribut [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-170">Instead, use the `Activate` attribute of the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d87c-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d87c-171">Example</span></span>  
 <span data-ttu-id="6d87c-172">`Stringify` Metodou v následujícím příkladu je pro obecné účely metody pro formátování, který používá reflexi k převedení objektu na jeho řetězcovou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="6d87c-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="6d87c-173">Kromě volání objektu výchozí `ToString` metody, metoda může vytvořit formátovaný výsledný řetězec předáním objektu `ToString` metoda řetězec formátu <xref:System.IFormatProvider> implementace nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="6d87c-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="6d87c-174">Může také volat jeden z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, která převede číslo na binární, hexadecimální nebo osmičkové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="6d87c-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="6d87c-175">`Stringify` Metoda může být volán kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="6d87c-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="6d87c-176">Ale při kompilaci s .NET Native, v příkladu může vyvolat počet výskytů výjimek za běhu, včetně <xref:System.NullReferenceException> a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, k tomu dochází, `Stringify` je – metoda určené primárně pro podporu dynamicky formátování primitivní typy v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d87c-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="6d87c-177">Jejich metadata, ale není k dispozici ve výchozí soubor direktivy.</span><span class="sxs-lookup"><span data-stu-id="6d87c-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="6d87c-178">I v případě, že jejich metadat je k dispozici, ale příklad vyvolá [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky protože odpovídající `ToString` implementace nebyly zahrnout nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6d87c-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="6d87c-179">Tyto výjimky lze všechny odstranit pomocí [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu k definování typů, jejichž metadata musí být k dispozici a to přidáním `<Method>` prvků, které se ujistěte se, že implementace metody přetížení který lze dynamicky volat je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6d87c-179">These exceptions can all be eliminated by using the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="6d87c-180">Následuje default.rd.xml soubor, který eliminuje těchto výjimek a umožňuje v příkladu provádět bez chyb.</span><span class="sxs-lookup"><span data-stu-id="6d87c-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d87c-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d87c-181">See also</span></span>

- [<span data-ttu-id="6d87c-182">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6d87c-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6d87c-183">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6d87c-183">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="6d87c-184">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6d87c-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="6d87c-185">\<MethodInstantiation > – Element</span><span class="sxs-lookup"><span data-stu-id="6d87c-185">\<MethodInstantiation> Element</span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
