---
title: Element &lt;Method&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6d70fd560cb7b164460eb3882cac88ed733d788
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodgt-element-net-native"></a><span data-ttu-id="e027a-102">Element &lt;Method&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e027a-102">&lt;Method&gt; Element (.NET Native)</span></span>
<span data-ttu-id="e027a-103">Platí zásady reflexe modulu runtime pro konstruktor nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="e027a-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e027a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e027a-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e027a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e027a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e027a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e027a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e027a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e027a-107">Attributes</span></span>  
  
|<span data-ttu-id="e027a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="e027a-108">Attribute</span></span>|<span data-ttu-id="e027a-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="e027a-109">Attribute type</span></span>|<span data-ttu-id="e027a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e027a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e027a-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="e027a-111">General</span></span>|<span data-ttu-id="e027a-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e027a-112">Required attribute.</span></span> <span data-ttu-id="e027a-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="e027a-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="e027a-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="e027a-114">General</span></span>|<span data-ttu-id="e027a-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e027a-115">Optional attribute.</span></span> <span data-ttu-id="e027a-116">Určuje podpis metody.</span><span class="sxs-lookup"><span data-stu-id="e027a-116">Specifies the method signature.</span></span> <span data-ttu-id="e027a-117">Pokud jsou v něm několik parametrů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="e027a-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="e027a-118">Například následující `<Method>` element definuje zásady pro <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="e027a-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="e027a-119">Pokud chybí atribut, direktivy modulu runtime platí pro všechny přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="e027a-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="e027a-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="e027a-120">Reflection</span></span>|<span data-ttu-id="e027a-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e027a-121">Optional attribute.</span></span> <span data-ttu-id="e027a-122">Ovládací prvky dotazování na informace o nebo vytváření výčtu metodu, ale neumožňuje žádné dynamické volání za běhu.</span><span class="sxs-lookup"><span data-stu-id="e027a-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e027a-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="e027a-123">Reflection</span></span>|<span data-ttu-id="e027a-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e027a-124">Optional attribute.</span></span> <span data-ttu-id="e027a-125">Ovládací prvky runtime přístup k konstruktor nebo způsob povolení dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="e027a-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="e027a-126">Tato zásada zajistí, že člena nelze vyvolat dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="e027a-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e027a-127">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="e027a-127">Name attribute</span></span>  
  
|<span data-ttu-id="e027a-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e027a-128">Value</span></span>|<span data-ttu-id="e027a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="e027a-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e027a-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="e027a-130">*method_name*</span></span>|<span data-ttu-id="e027a-131">Název metody.</span><span class="sxs-lookup"><span data-stu-id="e027a-131">The method name.</span></span> <span data-ttu-id="e027a-132">Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="e027a-132">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="e027a-133">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="e027a-133">Signature attribute</span></span>  
  
|<span data-ttu-id="e027a-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e027a-134">Value</span></span>|<span data-ttu-id="e027a-135">Popis</span><span class="sxs-lookup"><span data-stu-id="e027a-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e027a-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="e027a-136">*method_signature*</span></span>|<span data-ttu-id="e027a-137">Typy parametrů, které vytvářejí podpis metody.</span><span class="sxs-lookup"><span data-stu-id="e027a-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="e027a-138">Několik parametrů jsou oddělené čárkami, například `"System.String,System.Int32,System.Int32)"`.</span><span class="sxs-lookup"><span data-stu-id="e027a-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="e027a-139">Typ názvy parametrů by měl být úplný.</span><span class="sxs-lookup"><span data-stu-id="e027a-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e027a-140">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="e027a-140">All other attributes</span></span>  
  
|<span data-ttu-id="e027a-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e027a-141">Value</span></span>|<span data-ttu-id="e027a-142">Popis</span><span class="sxs-lookup"><span data-stu-id="e027a-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e027a-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e027a-143">*policy_setting*</span></span>|<span data-ttu-id="e027a-144">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="e027a-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="e027a-145">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="e027a-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e027a-146">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e027a-146">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e027a-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e027a-147">Child Elements</span></span>  
  
|<span data-ttu-id="e027a-148">Prvek</span><span class="sxs-lookup"><span data-stu-id="e027a-148">Element</span></span>|<span data-ttu-id="e027a-149">Popis</span><span class="sxs-lookup"><span data-stu-id="e027a-149">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e027a-150">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="e027a-150">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)|<span data-ttu-id="e027a-151">Zásada se vztahuje na typ argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="e027a-151">Applies policy to the type of the argument passed to a method.</span></span>|  
|[<span data-ttu-id="e027a-152">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="e027a-152">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|<span data-ttu-id="e027a-153">Zásada se vztahuje na typ parametru obecný typ nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="e027a-153">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[<span data-ttu-id="e027a-154">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="e027a-154">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)|<span data-ttu-id="e027a-155">Platí zásady pro typu, v případě, že zásada pro metodu reprezentovanou obsahující `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e027a-155">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[<span data-ttu-id="e027a-156">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="e027a-156">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|<span data-ttu-id="e027a-157">Zásada se vztahuje na typ zastoupený <xref:System.Type> argument předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="e027a-157">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e027a-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e027a-158">Parent Elements</span></span>  
  
|<span data-ttu-id="e027a-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="e027a-159">Element</span></span>|<span data-ttu-id="e027a-160">Popis</span><span class="sxs-lookup"><span data-stu-id="e027a-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e027a-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="e027a-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="e027a-162">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="e027a-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="e027a-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="e027a-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="e027a-164">Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="e027a-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e027a-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e027a-165">Remarks</span></span>  
 <span data-ttu-id="e027a-166">A `<Method>` element obecná metoda svých zásad platí pro všechny konkretizací, které nemají své vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="e027a-166">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="e027a-167">Můžete použít `Signature` atribut určení zásad pro konkrétní metody přetížení.</span><span class="sxs-lookup"><span data-stu-id="e027a-167">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="e027a-168">Jinak, pokud `Signature` chybí atribut, direktivy modulu runtime platí pro všechny přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="e027a-168">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="e027a-169">Nelze definovat zásady reflexe modulu runtime pro konstruktor pomocí `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e027a-169">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="e027a-170">Místo toho použijte `Activate` atribut [ \<sestavení >](../../../docs/framework/net-native/assembly-element-net-native.md), [ \<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md), [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md), nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="e027a-170">Instead, use the `Activate` attribute of the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e027a-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="e027a-171">Example</span></span>  
 <span data-ttu-id="e027a-172">`Stringify` Metoda v následujícím příkladu je pro obecné účely formátování metoda, která používá reflexe převést řetězcovou reprezentaci objektu.</span><span class="sxs-lookup"><span data-stu-id="e027a-172">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="e027a-173">Kromě volání objektu výchozí `ToString` metody metodu můžete vytvořit řetězec formátovaný výsledek předáním objektu `ToString` metoda řetězec formátu <xref:System.IFormatProvider> implementace, nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="e027a-173">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="e027a-174">Také jeden z může zavolat <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, která převádí číslo na jeho binární, šestnáctkové nebo osmičková reprezentace.</span><span class="sxs-lookup"><span data-stu-id="e027a-174">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="e027a-175">`Stringify` Nelze volat metodu kódem takto:</span><span class="sxs-lookup"><span data-stu-id="e027a-175">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="e027a-176">Ale když kompilujete s .NET Native, v příkladu můžete vyvolat představuje počet výjimek za běhu, včetně <xref:System.NullReferenceException> a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, k tomu dochází proto `Stringify` je – metoda určená hlavně pro podporu dynamicky formátování primitivní typy v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e027a-176">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="e027a-177">Jejich metadat však není k dispozici ve výchozí soubor direktivy.</span><span class="sxs-lookup"><span data-stu-id="e027a-177">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="e027a-178">I když jejich metadata jsou k dispozici, ale v příkladu vyvolá [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky protože odpovídající `ToString` implementace nebyly byla obsahovat v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="e027a-178">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="e027a-179">Tyto výjimky všechny jdou vyloučit pomocí [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) elementu k definování typů, jejichž metadata musí být k dispozici a přidáním `<Method>` elementy zajistit, aby implementace přetížení metody které lze volat dynamicky se nachází.</span><span class="sxs-lookup"><span data-stu-id="e027a-179">These exceptions can all be eliminated by using the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="e027a-180">Zde je default.rd.xml soubor, který eliminuje tyto výjimky a umožňuje v příkladu provést bez chyby.</span><span class="sxs-lookup"><span data-stu-id="e027a-180">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e027a-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="e027a-181">See Also</span></span>  
 [<span data-ttu-id="e027a-182">Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e027a-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="e027a-183">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e027a-183">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="e027a-184">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e027a-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="e027a-185">\<MethodInstantiation > elementu</span><span class="sxs-lookup"><span data-stu-id="e027a-185">\<MethodInstantiation> Element</span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)
