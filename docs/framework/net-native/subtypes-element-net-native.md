---
title: Element &lt;Subtypes&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5503e89006411887de9b0def929ac1155df5aa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537251"
---
# <a name="ltsubtypesgt-element-net-native"></a><span data-ttu-id="1d458-102">Element &lt;Subtypes&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="1d458-102">&lt;Subtypes&gt; Element (.NET Native)</span></span>
<span data-ttu-id="1d458-103">Zásady modulu runtime se vztahuje na všechny třídy dědí z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="1d458-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d458-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d458-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d458-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d458-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1d458-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d458-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d458-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d458-107">Attributes</span></span>  
  
|<span data-ttu-id="1d458-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d458-108">Attribute</span></span>|<span data-ttu-id="1d458-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="1d458-109">Attribute type</span></span>|<span data-ttu-id="1d458-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1d458-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="1d458-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="1d458-111">Reflection</span></span>|<span data-ttu-id="1d458-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-112">Optional attribute.</span></span> <span data-ttu-id="1d458-113">Ovládací prvky runtime přístup k konstruktory Povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="1d458-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="1d458-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="1d458-114">Reflection</span></span>|<span data-ttu-id="1d458-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-115">Optional attribute.</span></span> <span data-ttu-id="1d458-116">Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1d458-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="1d458-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="1d458-117">Reflection</span></span>|<span data-ttu-id="1d458-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-118">Optional attribute.</span></span> <span data-ttu-id="1d458-119">Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="1d458-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="1d458-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="1d458-120">Serialization</span></span>|<span data-ttu-id="1d458-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-121">Optional attribute.</span></span> <span data-ttu-id="1d458-122">Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="1d458-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="1d458-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="1d458-123">Serialization</span></span>|<span data-ttu-id="1d458-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-124">Optional attribute.</span></span> <span data-ttu-id="1d458-125">Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d458-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="1d458-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="1d458-126">Serialization</span></span>|<span data-ttu-id="1d458-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-127">Optional attribute.</span></span> <span data-ttu-id="1d458-128">Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d458-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="1d458-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="1d458-129">Serialization</span></span>|<span data-ttu-id="1d458-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-130">Optional attribute.</span></span> <span data-ttu-id="1d458-131">Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d458-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="1d458-132">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="1d458-132">Interop</span></span>|<span data-ttu-id="1d458-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-133">Optional attribute.</span></span> <span data-ttu-id="1d458-134">Ovládací prvky zásad pro zařazování odkazové typy Windows Runtime a modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1d458-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="1d458-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="1d458-135">Interop</span></span>|<span data-ttu-id="1d458-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-136">Optional attribute.</span></span> <span data-ttu-id="1d458-137">Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="1d458-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="1d458-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="1d458-138">Interop</span></span>|<span data-ttu-id="1d458-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1d458-139">Optional attribute.</span></span> <span data-ttu-id="1d458-140">Určuje zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="1d458-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="1d458-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="1d458-141">All attributes</span></span>  
  
|<span data-ttu-id="1d458-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1d458-142">Value</span></span>|<span data-ttu-id="1d458-143">Popis</span><span class="sxs-lookup"><span data-stu-id="1d458-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d458-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="1d458-144">*policy_setting*</span></span>|<span data-ttu-id="1d458-145">Toto nastavení platí pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="1d458-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="1d458-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="1d458-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="1d458-147">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="1d458-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d458-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d458-148">Child Elements</span></span>  
 <span data-ttu-id="1d458-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="1d458-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d458-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d458-150">Parent Elements</span></span>  
  
|<span data-ttu-id="1d458-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d458-151">Element</span></span>|<span data-ttu-id="1d458-152">Popis</span><span class="sxs-lookup"><span data-stu-id="1d458-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d458-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="1d458-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="1d458-154">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="1d458-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d458-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d458-155">Remarks</span></span>  
 <span data-ttu-id="1d458-156">`<Subtypes>` Element použije zásady na všechny podtypy jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="1d458-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="1d458-157">Použijete ji, pokud chcete použít jiné zásady pro odvozené typy a jejich základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1d458-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="1d458-158">Reflexe, serializace a atributů spolupráce jsou nepovinné, ale alespoň jeden by měl být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1d458-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d458-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d458-159">Example</span></span>  
 <span data-ttu-id="1d458-160">Následující příklad definuje třídu s názvem `BaseClass` a podtřídu s názvem `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="1d458-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="1d458-161">Jak je znázorněno v následujícím kódu, direktivy modulu runtime explicitně souboru nastaví `Dynamic` a `Activate` zásady pro `BaseClass` k `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="1d458-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="1d458-162">Z důvodu této, objekty typu `BaseClass` nelze vytvořit instanci dynamicky nebo voláním do `BaseClass` konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="1d458-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="1d458-163">Ale `<Subtypes>` element umožňuje třídy odvozené od `BaseClass` má být vytvořena dynamicky a prostřednictvím volání konstruktorů své třídy.</span><span class="sxs-lookup"><span data-stu-id="1d458-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="1d458-164">Z důvodu `<Subtypes>` směrnice, následující kód, který vytvoří instanci `Derived1` instance dynamicky voláním <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> metoda provede úspěšně.</span><span class="sxs-lookup"><span data-stu-id="1d458-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="1d458-165">Tady je proměnná bloku <xref:System.Windows.Controls.TextBlock> objektu v prázdnou aplikaci pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="1d458-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1d458-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d458-166">See also</span></span>
- [<span data-ttu-id="1d458-167">\<Typ > – Element</span><span class="sxs-lookup"><span data-stu-id="1d458-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="1d458-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="1d458-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1d458-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="1d458-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="1d458-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="1d458-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
