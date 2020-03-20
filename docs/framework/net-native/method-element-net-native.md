---
title: <Method>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180990"
---
# <a name="method-element-net-native"></a><span data-ttu-id="9ea99-102">\<Metoda> element (nativní.NET)</span><span class="sxs-lookup"><span data-stu-id="9ea99-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="9ea99-103">Aplikuje zásady odrazu za běhu na konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="9ea99-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ea99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea99-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ea99-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9ea99-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9ea99-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9ea99-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ea99-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="9ea99-107">Attributes</span></span>  
  
|<span data-ttu-id="9ea99-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="9ea99-108">Attribute</span></span>|<span data-ttu-id="9ea99-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="9ea99-109">Attribute type</span></span>|<span data-ttu-id="9ea99-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea99-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9ea99-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="9ea99-111">General</span></span>|<span data-ttu-id="9ea99-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9ea99-112">Required attribute.</span></span> <span data-ttu-id="9ea99-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="9ea99-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="9ea99-114">General</span></span>|<span data-ttu-id="9ea99-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9ea99-115">Optional attribute.</span></span> <span data-ttu-id="9ea99-116">Určuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-116">Specifies the method signature.</span></span> <span data-ttu-id="9ea99-117">Pokud jsou k dispozici více parametrů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="9ea99-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="9ea99-118">Například následující `<Method>` prvek definuje zásady <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> pro metodu.</span><span class="sxs-lookup"><span data-stu-id="9ea99-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="9ea99-119">Pokud atribut chybí, direktiva runtime platí pro všechna přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="9ea99-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="9ea99-120">Reflection</span></span>|<span data-ttu-id="9ea99-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9ea99-121">Optional attribute.</span></span> <span data-ttu-id="9ea99-122">Řídí dotazování na informace o metodě nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.</span><span class="sxs-lookup"><span data-stu-id="9ea99-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="9ea99-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="9ea99-123">Reflection</span></span>|<span data-ttu-id="9ea99-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="9ea99-124">Optional attribute.</span></span> <span data-ttu-id="9ea99-125">Řídí přístup za běhu k konstruktoru nebo metodě, která umožňuje dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="9ea99-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="9ea99-126">Tato zásada zajišťuje, že člen může být vyvolán dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="9ea99-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9ea99-127">Atribut Název</span><span class="sxs-lookup"><span data-stu-id="9ea99-127">Name attribute</span></span>  
  
|<span data-ttu-id="9ea99-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9ea99-128">Value</span></span>|<span data-ttu-id="9ea99-129">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea99-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ea99-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="9ea99-130">*method_name*</span></span>|<span data-ttu-id="9ea99-131">Název metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-131">The method name.</span></span> <span data-ttu-id="9ea99-132">Typ metody je definován nadřazeným [ \<typem>](type-element-net-native.md) nebo [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) elementem.</span><span class="sxs-lookup"><span data-stu-id="9ea99-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="9ea99-133">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="9ea99-133">Signature attribute</span></span>  
  
|<span data-ttu-id="9ea99-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9ea99-134">Value</span></span>|<span data-ttu-id="9ea99-135">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea99-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ea99-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="9ea99-136">*method_signature*</span></span>|<span data-ttu-id="9ea99-137">Typy parametrů, které tvoří podpis metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="9ea99-138">Více parametrů je odděleno čárkami, `"System.String,System.Int32,System.Int32)"`například .</span><span class="sxs-lookup"><span data-stu-id="9ea99-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="9ea99-139">Názvy typů parametrů by měly být plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="9ea99-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9ea99-140">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="9ea99-140">All other attributes</span></span>  
  
|<span data-ttu-id="9ea99-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9ea99-141">Value</span></span>|<span data-ttu-id="9ea99-142">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea99-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ea99-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="9ea99-143">*policy_setting*</span></span>|<span data-ttu-id="9ea99-144">Nastavení, které se má použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="9ea99-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="9ea99-145">Možné hodnoty `Auto` `Excluded`jsou `Included`, `Required`, a .</span><span class="sxs-lookup"><span data-stu-id="9ea99-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="9ea99-146">Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9ea99-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ea99-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9ea99-147">Child Elements</span></span>  
  
|<span data-ttu-id="9ea99-148">Element</span><span class="sxs-lookup"><span data-stu-id="9ea99-148">Element</span></span>|<span data-ttu-id="9ea99-149">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea99-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ea99-150">\<>parametrů</span><span class="sxs-lookup"><span data-stu-id="9ea99-150">\<Parameter></span></span>](parameter-element-net-native.md)|<span data-ttu-id="9ea99-151">Platí zásadu pro typ argumentu předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="9ea99-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="9ea99-152">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="9ea99-152">\<GenericParameter></span></span>](genericparameter-element-net-native.md)|<span data-ttu-id="9ea99-153">Použije zásadu pro typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="9ea99-154">\<ImplikaceTyp></span><span class="sxs-lookup"><span data-stu-id="9ea99-154">\<ImpliesType></span></span>](impliestype-element-net-native.md)|<span data-ttu-id="9ea99-155">Platí zásadu pro typ, pokud tato zásada byla použita `<Method>` pro metodu reprezentovanou obsahující prvek.</span><span class="sxs-lookup"><span data-stu-id="9ea99-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="9ea99-156">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="9ea99-156">\<TypeParameter></span></span>](typeparameter-element-net-native.md)|<span data-ttu-id="9ea99-157">Platí zásadu pro typ <xref:System.Type> reprezentované argumentem předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="9ea99-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ea99-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9ea99-158">Parent Elements</span></span>  
  
|<span data-ttu-id="9ea99-159">Element</span><span class="sxs-lookup"><span data-stu-id="9ea99-159">Element</span></span>|<span data-ttu-id="9ea99-160">Popis</span><span class="sxs-lookup"><span data-stu-id="9ea99-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ea99-161">\<Typ></span><span class="sxs-lookup"><span data-stu-id="9ea99-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="9ea99-162">Použije zásady reflexe na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="9ea99-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="9ea99-163">\<TypRychlé></span><span class="sxs-lookup"><span data-stu-id="9ea99-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="9ea99-164">Použije zásady reflexe na vytvořený obecný typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="9ea99-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ea99-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ea99-165">Remarks</span></span>  
 <span data-ttu-id="9ea99-166">Prvek `<Method>` obecné metody použije své zásady pro všechny instance, které nemají své vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="9ea99-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="9ea99-167">`Signature` Atribut můžete použít k určení zásady pro přetížení určité metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="9ea99-168">V opačném `Signature` případě, pokud atribut chybí, direktiva runtime platí pro všechna přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="9ea99-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="9ea99-169">Nelze definovat zásady odrazu za běhu pro `<Method>` konstruktor pomocí prvku.</span><span class="sxs-lookup"><span data-stu-id="9ea99-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="9ea99-170">Místo toho `Activate` použijte atribut>[ \<elementu Assembly>](assembly-element-net-native.md), [ \<Namespace>](namespace-element-net-native.md), [ \<Type>](type-element-net-native.md)nebo [ \<TypeInstantiation.](typeinstantiation-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="9ea99-170">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ea99-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ea99-171">Example</span></span>  
 <span data-ttu-id="9ea99-172">Metoda `Stringify` v následujícím příkladu je metoda obecného formátování, která používá reflexi k převodu objektu na jeho řetězcovou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="9ea99-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="9ea99-173">Kromě volání výchozí `ToString` metody objektu může metoda vytvořit formátovaný výsledný řetězec předáním `ToString` metody objektu <xref:System.IFormatProvider> formátovací řetězec, implementaci nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="9ea99-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="9ea99-174">Může také volat jeden <xref:System.Convert.ToString%2A?displayProperty=nameWithType> z přetížení, který převádí číslo na jeho binární, šestnáctkové nebo osmičkové reprezentace.</span><span class="sxs-lookup"><span data-stu-id="9ea99-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="9ea99-175">Metoda `Stringify` může být volána kódem, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="9ea99-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="9ea99-176">Však při kompilaci s .NET Native, v příkladu může vyvolat <xref:System.NullReferenceException> počet výjimek za běhu, včetně a `Stringify` [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimky, K tomu dochází, protože metoda je určena především pro podporu dynamicky formátování primitivní typy v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ea99-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="9ea99-177">Jejich metadata však nejsou k dispozici ve výchozím souboru direktiv.</span><span class="sxs-lookup"><span data-stu-id="9ea99-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="9ea99-178">I v případě, že jejich metadata je k dispozici, však v `ToString` příkladu vyvolá [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimky, protože příslušné implementace nebyly zahrnuty v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="9ea99-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="9ea99-179">Tyto výjimky lze všechny odstranit pomocí [ \<Type>](type-element-net-native.md) prvek definovat typy, jejichž metadata musí být k dispozici, a přidáním `<Method>` prvků k zajištění, že implementace přetížení metody, které lze volat dynamicky je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9ea99-179">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="9ea99-180">Následuje soubor default.rd.xml, který tyto výjimky eliminuje a umožňuje provedení příkladu bez chyby.</span><span class="sxs-lookup"><span data-stu-id="9ea99-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ea99-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ea99-181">See also</span></span>

- [<span data-ttu-id="9ea99-182">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9ea99-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9ea99-183">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9ea99-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9ea99-184">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9ea99-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="9ea99-185">\<MethodInstantiation> Element</span><span class="sxs-lookup"><span data-stu-id="9ea99-185">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
