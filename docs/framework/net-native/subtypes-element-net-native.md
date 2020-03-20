---
title: <Subtypes>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180939"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="ffc28-102">\<Podtypy> Element (nativní.NET)</span><span class="sxs-lookup"><span data-stu-id="ffc28-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="ffc28-103">Aplikuje zásady runtime na všechny třídy zděděné z obsahujícího typu.</span><span class="sxs-lookup"><span data-stu-id="ffc28-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffc28-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffc28-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ffc28-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ffc28-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ffc28-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffc28-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ffc28-107">Attributes</span></span>  
  
|<span data-ttu-id="ffc28-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ffc28-108">Attribute</span></span>|<span data-ttu-id="ffc28-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="ffc28-109">Attribute type</span></span>|<span data-ttu-id="ffc28-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ffc28-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="ffc28-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ffc28-111">Reflection</span></span>|<span data-ttu-id="ffc28-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-112">Optional attribute.</span></span> <span data-ttu-id="ffc28-113">Řídí přístup za běhu k konstruktorům, aby bylo možné aktivovat instance.</span><span class="sxs-lookup"><span data-stu-id="ffc28-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="ffc28-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ffc28-114">Reflection</span></span>|<span data-ttu-id="ffc28-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-115">Optional attribute.</span></span> <span data-ttu-id="ffc28-116">Řídí dotazování na informace o prvcích programu, ale neumožňuje žádný přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="ffc28-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="ffc28-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ffc28-117">Reflection</span></span>|<span data-ttu-id="ffc28-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-118">Optional attribute.</span></span> <span data-ttu-id="ffc28-119">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, aby bylo možné povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="ffc28-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="ffc28-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="ffc28-120">Serialization</span></span>|<span data-ttu-id="ffc28-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-121">Optional attribute.</span></span> <span data-ttu-id="ffc28-122">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby instance typu mohly být serializovány a deserializovány knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="ffc28-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="ffc28-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="ffc28-123">Serialization</span></span>|<span data-ttu-id="ffc28-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-124">Optional attribute.</span></span> <span data-ttu-id="ffc28-125">Řídí zásady serializace, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> která používá třídu.</span><span class="sxs-lookup"><span data-stu-id="ffc28-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="ffc28-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="ffc28-126">Serialization</span></span>|<span data-ttu-id="ffc28-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-127">Optional attribute.</span></span> <span data-ttu-id="ffc28-128">Řídí zásady pro serializaci JSON, který používá třídu. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ffc28-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="ffc28-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="ffc28-129">Serialization</span></span>|<span data-ttu-id="ffc28-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-130">Optional attribute.</span></span> <span data-ttu-id="ffc28-131">Řídí zásady serializace XML, která používá třídu. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ffc28-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="ffc28-132">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="ffc28-132">Interop</span></span>|<span data-ttu-id="ffc28-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-133">Optional attribute.</span></span> <span data-ttu-id="ffc28-134">Řídí zásady pro zařazování typů odkazů na prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="ffc28-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="ffc28-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="ffc28-135">Interop</span></span>|<span data-ttu-id="ffc28-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-136">Optional attribute.</span></span> <span data-ttu-id="ffc28-137">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="ffc28-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="ffc28-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="ffc28-138">Interop</span></span>|<span data-ttu-id="ffc28-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ffc28-139">Optional attribute.</span></span> <span data-ttu-id="ffc28-140">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="ffc28-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="ffc28-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="ffc28-141">All attributes</span></span>  
  
|<span data-ttu-id="ffc28-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ffc28-142">Value</span></span>|<span data-ttu-id="ffc28-143">Popis</span><span class="sxs-lookup"><span data-stu-id="ffc28-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ffc28-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ffc28-144">*policy_setting*</span></span>|<span data-ttu-id="ffc28-145">Nastavení, které se má použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="ffc28-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="ffc28-146">Možné hodnoty `All` `Auto`jsou `Excluded` `Public`, `PublicAndInternal` `Required Public`, `Required PublicAndInternal`, `Required All`, , , a .</span><span class="sxs-lookup"><span data-stu-id="ffc28-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="ffc28-147">Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ffc28-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffc28-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ffc28-148">Child Elements</span></span>  
 <span data-ttu-id="ffc28-149">Žádné.</span><span class="sxs-lookup"><span data-stu-id="ffc28-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffc28-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ffc28-150">Parent Elements</span></span>  
  
|<span data-ttu-id="ffc28-151">Element</span><span class="sxs-lookup"><span data-stu-id="ffc28-151">Element</span></span>|<span data-ttu-id="ffc28-152">Popis</span><span class="sxs-lookup"><span data-stu-id="ffc28-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffc28-153">\<Typ></span><span class="sxs-lookup"><span data-stu-id="ffc28-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="ffc28-154">Použije zásady reflexe na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="ffc28-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc28-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffc28-155">Remarks</span></span>  
 <span data-ttu-id="ffc28-156">Prvek `<Subtypes>` platí zásady pro všechny podtypy jeho obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="ffc28-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="ffc28-157">Můžete použít, pokud chcete použít různé zásady odvozené typy a jejich základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ffc28-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="ffc28-158">Reflexe, serializace a interop atributy jsou volitelné, i když alespoň jeden by měl být přítomen.</span><span class="sxs-lookup"><span data-stu-id="ffc28-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffc28-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffc28-159">Example</span></span>  
 <span data-ttu-id="ffc28-160">Následující příklad definuje třídu `BaseClass` s názvem `Derived1`a podtřídu s názvem .</span><span class="sxs-lookup"><span data-stu-id="ffc28-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="ffc28-161">Jak je znázorněno v následujícím kódu, soubor `Dynamic` direktiv runtime explicitně nastaví zásady a `Activate` pro `BaseClass` . `Excluded`</span><span class="sxs-lookup"><span data-stu-id="ffc28-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="ffc28-162">Z tohoto důvodu objekty typu `BaseClass` nelze vytvořit instance dynamicky `BaseClass` nebo volání konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="ffc28-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="ffc28-163">`<Subtypes>` Prvek však umožňuje třídy `BaseClass` odvozené z dynamicky a prostřednictvím volání jejich konstruktory třídy.</span><span class="sxs-lookup"><span data-stu-id="ffc28-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="ffc28-164">Z důvodu `<Subtypes>` směrnice následující kód, který instanci `Derived1` instance dynamicky voláním <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> metody provede úspěšně.</span><span class="sxs-lookup"><span data-stu-id="ffc28-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="ffc28-165">Proměnná bloku je <xref:System.Windows.Controls.TextBlock> objekt v prázdné aplikaci pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ffc28-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ffc28-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffc28-166">See also</span></span>

- [<span data-ttu-id="ffc28-167">\<Typ> element</span><span class="sxs-lookup"><span data-stu-id="ffc28-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="ffc28-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ffc28-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ffc28-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ffc28-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ffc28-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ffc28-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
