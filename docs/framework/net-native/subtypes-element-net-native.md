---
title: Element &lt;Subtypes&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9609027d31e757af93f6a4401a784a68a53cfdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsubtypesgt-element-net-native"></a><span data-ttu-id="6ace8-102">Element &lt;Subtypes&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6ace8-102">&lt;Subtypes&gt; Element (.NET Native)</span></span>
<span data-ttu-id="6ace8-103">Modul runtime zásad platí pro všechny třídy dědí z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="6ace8-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ace8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ace8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ace8-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ace8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6ace8-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ace8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ace8-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ace8-107">Attributes</span></span>  
  
|<span data-ttu-id="6ace8-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="6ace8-108">Attribute</span></span>|<span data-ttu-id="6ace8-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="6ace8-109">Attribute type</span></span>|<span data-ttu-id="6ace8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6ace8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="6ace8-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6ace8-111">Reflection</span></span>|<span data-ttu-id="6ace8-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-112">Optional attribute.</span></span> <span data-ttu-id="6ace8-113">Ovládací prvky runtime přístup k konstruktory povolit aktivace instancí.</span><span class="sxs-lookup"><span data-stu-id="6ace8-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="6ace8-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6ace8-114">Reflection</span></span>|<span data-ttu-id="6ace8-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-115">Optional attribute.</span></span> <span data-ttu-id="6ace8-116">Ovládací prvky dotazování na informace o programu elementů, ale nepovolí žádné přístup k modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6ace8-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="6ace8-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="6ace8-117">Reflection</span></span>|<span data-ttu-id="6ace8-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-118">Optional attribute.</span></span> <span data-ttu-id="6ace8-119">Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktory, metody, polí, vlastnosti a události, chcete-li povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="6ace8-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="6ace8-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="6ace8-120">Serialization</span></span>|<span data-ttu-id="6ace8-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-121">Optional attribute.</span></span> <span data-ttu-id="6ace8-122">Ovládací prvky runtime přístup k konstruktory, pole a vlastnosti, aby instance typu serializovat a deserializovat pomocí knihovny například serializátor Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="6ace8-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="6ace8-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="6ace8-123">Serialization</span></span>|<span data-ttu-id="6ace8-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-124">Optional attribute.</span></span> <span data-ttu-id="6ace8-125">Zásady pro serializaci, který používá ovládací prvky <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="6ace8-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="6ace8-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="6ace8-126">Serialization</span></span>|<span data-ttu-id="6ace8-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-127">Optional attribute.</span></span> <span data-ttu-id="6ace8-128">Zásady pro serializaci JSON, který používá ovládací prvky <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="6ace8-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="6ace8-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="6ace8-129">Serialization</span></span>|<span data-ttu-id="6ace8-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-130">Optional attribute.</span></span> <span data-ttu-id="6ace8-131">Zásady pro serializaci XML, který používá ovládací prvky <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="6ace8-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="6ace8-132">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="6ace8-132">Interop</span></span>|<span data-ttu-id="6ace8-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-133">Optional attribute.</span></span> <span data-ttu-id="6ace8-134">Ovládací prvky zásady pro zařazování odkazové typy prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="6ace8-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="6ace8-135">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="6ace8-135">Interop</span></span>|<span data-ttu-id="6ace8-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-136">Optional attribute.</span></span> <span data-ttu-id="6ace8-137">Ovládací prvky zásady pro zařazování delegáta typy jako ukazatelů na funkce do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6ace8-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="6ace8-138">Zprostředkovatel komunikace s objekty</span><span class="sxs-lookup"><span data-stu-id="6ace8-138">Interop</span></span>|<span data-ttu-id="6ace8-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6ace8-139">Optional attribute.</span></span> <span data-ttu-id="6ace8-140">Ovládací prvky zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6ace8-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="6ace8-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="6ace8-141">All attributes</span></span>  
  
|<span data-ttu-id="6ace8-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ace8-142">Value</span></span>|<span data-ttu-id="6ace8-143">Popis</span><span class="sxs-lookup"><span data-stu-id="6ace8-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6ace8-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="6ace8-144">*policy_setting*</span></span>|<span data-ttu-id="6ace8-145">Nastavení, které chcete použít pro tento typ zásad.</span><span class="sxs-lookup"><span data-stu-id="6ace8-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="6ace8-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="6ace8-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="6ace8-147">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6ace8-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ace8-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6ace8-148">Child Elements</span></span>  
 <span data-ttu-id="6ace8-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ace8-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ace8-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6ace8-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6ace8-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ace8-151">Element</span></span>|<span data-ttu-id="6ace8-152">Popis</span><span class="sxs-lookup"><span data-stu-id="6ace8-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ace8-153">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="6ace8-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="6ace8-154">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="6ace8-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ace8-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ace8-155">Remarks</span></span>  
 <span data-ttu-id="6ace8-156">`<Subtypes>` Element platí pro všechny podtypů jeho obsahující typ zásad.</span><span class="sxs-lookup"><span data-stu-id="6ace8-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="6ace8-157">Použijete jej, pokud chcete přiřadit různé zásady pro odvozené typy a jejich základních tříd.</span><span class="sxs-lookup"><span data-stu-id="6ace8-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="6ace8-158">Reflexe, serializace a atributů spolupráce jsou nepovinné, ale alespoň jeden by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="6ace8-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ace8-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ace8-159">Example</span></span>  
 <span data-ttu-id="6ace8-160">Následující příklad definuje třídu s názvem `BaseClass` a podtřídy s názvem `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="6ace8-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="6ace8-161">Jak je znázorněno v následujícím kódu, direktivy modulu runtime soubor explicitně nastaví `Dynamic` a `Activate` zásady pro `BaseClass` k `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="6ace8-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="6ace8-162">Z důvodu se objekty typu `BaseClass` nelze vytvořit instanci dynamicky nebo volání do `BaseClass` konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="6ace8-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="6ace8-163">Ale `<Subtypes>` element umožňuje třídy odvozené od třídy `BaseClass` chcete vytvořit instanci dynamicky a prostřednictvím volání do jejich konstruktory třídy.</span><span class="sxs-lookup"><span data-stu-id="6ace8-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="6ace8-164">Z důvodu `<Subtypes>` – direktiva, následující kód, který vytvoří `Derived1` instance dynamicky voláním <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="6ace8-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="6ace8-165">Je zde proměnná bloku <xref:System.Windows.Controls.TextBlock> objekt v prázdnou aplikaci pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="6ace8-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6ace8-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ace8-166">See Also</span></span>  
 [<span data-ttu-id="6ace8-167">\<Typ > elementu</span><span class="sxs-lookup"><span data-stu-id="6ace8-167">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="6ace8-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6ace8-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="6ace8-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6ace8-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="6ace8-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6ace8-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
