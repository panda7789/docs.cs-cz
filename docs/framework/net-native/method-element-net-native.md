---
title: <Method>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 8db32c660846b4f4071fff2a40c760a3d1ef2489
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180990"
---
# <a name="method-element-net-native"></a><span data-ttu-id="8b255-102">\<Method>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="8b255-102">\<Method> Element (.NET Native)</span></span>
<span data-ttu-id="8b255-103">Aplikuje zásady reflexe za běhu na konstruktor nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="8b255-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b255-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b255-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b255-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8b255-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8b255-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8b255-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b255-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8b255-107">Attributes</span></span>  
  
|<span data-ttu-id="8b255-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8b255-108">Attribute</span></span>|<span data-ttu-id="8b255-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="8b255-109">Attribute type</span></span>|<span data-ttu-id="8b255-110">Description</span><span class="sxs-lookup"><span data-stu-id="8b255-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8b255-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="8b255-111">General</span></span>|<span data-ttu-id="8b255-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8b255-112">Required attribute.</span></span> <span data-ttu-id="8b255-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="8b255-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="8b255-114">General</span></span>|<span data-ttu-id="8b255-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="8b255-115">Optional attribute.</span></span> <span data-ttu-id="8b255-116">Určuje signaturu metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-116">Specifies the method signature.</span></span> <span data-ttu-id="8b255-117">Pokud je přítomno více parametrů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="8b255-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="8b255-118">Například následující `<Method>` prvek definuje zásadu pro <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> metodu.</span><span class="sxs-lookup"><span data-stu-id="8b255-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="8b255-119">Pokud atribut chybí, platí direktiva modulu runtime pro všechna přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="8b255-120">Reflexe</span><span class="sxs-lookup"><span data-stu-id="8b255-120">Reflection</span></span>|<span data-ttu-id="8b255-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="8b255-121">Optional attribute.</span></span> <span data-ttu-id="8b255-122">Řídí dotazování na informace o nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.</span><span class="sxs-lookup"><span data-stu-id="8b255-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="8b255-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="8b255-123">Reflection</span></span>|<span data-ttu-id="8b255-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="8b255-124">Optional attribute.</span></span> <span data-ttu-id="8b255-125">Řídí přístup za běhu k konstruktoru nebo metodě pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="8b255-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="8b255-126">Tato zásada zajišťuje, že člen může být v době běhu vyvolán dynamicky.</span><span class="sxs-lookup"><span data-stu-id="8b255-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8b255-127">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="8b255-127">Name attribute</span></span>  
  
|<span data-ttu-id="8b255-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8b255-128">Value</span></span>|<span data-ttu-id="8b255-129">Description</span><span class="sxs-lookup"><span data-stu-id="8b255-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8b255-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="8b255-130">*method_name*</span></span>|<span data-ttu-id="8b255-131">Název metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-131">The method name.</span></span> <span data-ttu-id="8b255-132">Typ metody je definován nadřazeným [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem nebo prvkem.</span><span class="sxs-lookup"><span data-stu-id="8b255-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="8b255-133">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="8b255-133">Signature attribute</span></span>  
  
|<span data-ttu-id="8b255-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8b255-134">Value</span></span>|<span data-ttu-id="8b255-135">Description</span><span class="sxs-lookup"><span data-stu-id="8b255-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8b255-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="8b255-136">*method_signature*</span></span>|<span data-ttu-id="8b255-137">Typy parametrů, které tvoří signaturu metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="8b255-138">Více parametrů je odděleno čárkami, například `"System.String,System.Int32,System.Int32)"` .</span><span class="sxs-lookup"><span data-stu-id="8b255-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="8b255-139">Názvy typů parametrů by měly být plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="8b255-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8b255-140">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="8b255-140">All other attributes</span></span>  
  
|<span data-ttu-id="8b255-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8b255-141">Value</span></span>|<span data-ttu-id="8b255-142">Description</span><span class="sxs-lookup"><span data-stu-id="8b255-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8b255-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8b255-143">*policy_setting*</span></span>|<span data-ttu-id="8b255-144">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="8b255-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="8b255-145">Možné hodnoty jsou `Auto` , `Excluded` , `Included` a `Required` .</span><span class="sxs-lookup"><span data-stu-id="8b255-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="8b255-146">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8b255-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b255-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8b255-147">Child Elements</span></span>  
  
|<span data-ttu-id="8b255-148">Prvek</span><span class="sxs-lookup"><span data-stu-id="8b255-148">Element</span></span>|<span data-ttu-id="8b255-149">Description</span><span class="sxs-lookup"><span data-stu-id="8b255-149">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="8b255-150">Použije zásady na typ argumentu předaného metodě.</span><span class="sxs-lookup"><span data-stu-id="8b255-150">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="8b255-151">Použije zásady na typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-151">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="8b255-152">Použije zásady na typ, pokud byly tyto zásady použity na metodu reprezentovanou obsaženým `<Method>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="8b255-152">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="8b255-153">Použije zásady na typ představovaný <xref:System.Type> argumentem předaným metodě.</span><span class="sxs-lookup"><span data-stu-id="8b255-153">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b255-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8b255-154">Parent Elements</span></span>  
  
|<span data-ttu-id="8b255-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="8b255-155">Element</span></span>|<span data-ttu-id="8b255-156">Description</span><span class="sxs-lookup"><span data-stu-id="8b255-156">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="8b255-157">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="8b255-157">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="8b255-158">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="8b255-158">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b255-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b255-159">Remarks</span></span>  
 <span data-ttu-id="8b255-160">`<Method>`Element obecné metody aplikuje zásady na všechny instance, které nemají vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="8b255-160">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="8b255-161">Atribut lze použít `Signature` k určení zásad pro konkrétní přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-161">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="8b255-162">V opačném případě, pokud `Signature` atribut chybí, platí direktiva modulu runtime pro všechna přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="8b255-162">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="8b255-163">Nemůžete definovat zásady reflexe modulu runtime pro konstruktor pomocí `<Method>` elementu.</span><span class="sxs-lookup"><span data-stu-id="8b255-163">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="8b255-164">Místo toho použijte `Activate` atribut [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) prvku,, [\<Type>](type-element-net-native.md) nebo [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="8b255-164">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b255-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b255-165">Example</span></span>  
 <span data-ttu-id="8b255-166">`Stringify`Metoda v následujícím příkladu je metoda formátování pro obecné účely, která používá reflexi k převodu objektu na jeho řetězcovou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="8b255-166">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="8b255-167">Kromě volání výchozí `ToString` metody objektu může metoda vytvořit formátovaný výsledný řetězec předáním `ToString` metody objektu formátovacího řetězce, <xref:System.IFormatProvider> implementace nebo obojího.</span><span class="sxs-lookup"><span data-stu-id="8b255-167">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="8b255-168">Může také volat jedno z <xref:System.Convert.ToString%2A?displayProperty=nameWithType> přetížení, které převádí číslo na binární, šestnáctkové nebo osmičkové vyjádření.</span><span class="sxs-lookup"><span data-stu-id="8b255-168">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="8b255-169">`Stringify`Metodu lze volat pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="8b255-169">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="8b255-170">Nicméně při kompilaci s .NET Native může příklad vyvolat počet výjimek za běhu, včetně <xref:System.NullReferenceException> a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimek, k tomu dochází, protože `Stringify` Metoda je určena hlavně pro podporu dynamického formátování primitivních typů v knihovně tříd .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b255-170">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="8b255-171">Nicméně jejich metadata nejsou k dispozici ve výchozím souboru direktiv.</span><span class="sxs-lookup"><span data-stu-id="8b255-171">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="8b255-172">I v případě, že jsou k dispozici jejich metadata, ale příklad vyvolá výjimku [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , protože příslušné `ToString` implementace nebyly zahrnuty do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="8b255-172">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="8b255-173">Tyto výjimky lze eliminovat pomocí [\<Type>](type-element-net-native.md) elementu pro definování typů, jejichž metadata musí být přítomna, a přidáním prvků, aby `<Method>` bylo zajištěno, že je také k dispozici implementace přetížení metody, které lze volat dynamicky.</span><span class="sxs-lookup"><span data-stu-id="8b255-173">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="8b255-174">Následuje výchozí soubor. Rd. XML, který eliminuje tyto výjimky a umožňuje, aby se tento příklad spustil bez chyby.</span><span class="sxs-lookup"><span data-stu-id="8b255-174">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b255-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b255-175">See also</span></span>

- [<span data-ttu-id="8b255-176">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8b255-176">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8b255-177">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8b255-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="8b255-178">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8b255-178">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="8b255-179">\<MethodInstantiation>Objekt</span><span class="sxs-lookup"><span data-stu-id="8b255-179">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
