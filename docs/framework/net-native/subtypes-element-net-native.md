---
title: <Subtypes> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: 9f090e7d1558d31111345e2c9b8dabb55b7122c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128108"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="7f3f4-102">\<dílčí typy > elementu (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7f3f4-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="7f3f4-103">Aplikuje zásady modulu runtime na všechny třídy zděděné z nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f3f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f3f4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f3f4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f3f4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7f3f4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f3f4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f3f4-107">Attributes</span></span>  
  
|<span data-ttu-id="7f3f4-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f3f4-108">Attribute</span></span>|<span data-ttu-id="7f3f4-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="7f3f4-109">Attribute type</span></span>|<span data-ttu-id="7f3f4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7f3f4-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="7f3f4-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7f3f4-111">Reflection</span></span>|<span data-ttu-id="7f3f4-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-112">Optional attribute.</span></span> <span data-ttu-id="7f3f4-113">Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="7f3f4-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7f3f4-114">Reflection</span></span>|<span data-ttu-id="7f3f4-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-115">Optional attribute.</span></span> <span data-ttu-id="7f3f4-116">Řídí dotazování pro informace o prvcích programu, ale nepovoluje přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="7f3f4-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7f3f4-117">Reflection</span></span>|<span data-ttu-id="7f3f4-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-118">Optional attribute.</span></span> <span data-ttu-id="7f3f4-119">Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="7f3f4-120">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-120">Serialization</span></span>|<span data-ttu-id="7f3f4-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-121">Optional attribute.</span></span> <span data-ttu-id="7f3f4-122">Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="7f3f4-123">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-123">Serialization</span></span>|<span data-ttu-id="7f3f4-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-124">Optional attribute.</span></span> <span data-ttu-id="7f3f4-125">Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="7f3f4-126">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-126">Serialization</span></span>|<span data-ttu-id="7f3f4-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-127">Optional attribute.</span></span> <span data-ttu-id="7f3f4-128">Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="7f3f4-129">Serializace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-129">Serialization</span></span>|<span data-ttu-id="7f3f4-130">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-130">Optional attribute.</span></span> <span data-ttu-id="7f3f4-131">Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="7f3f4-132">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-132">Interop</span></span>|<span data-ttu-id="7f3f4-133">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-133">Optional attribute.</span></span> <span data-ttu-id="7f3f4-134">Řídí zásady pro zařazování typů odkazů do prostředí Windows Runtime a COM.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="7f3f4-135">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-135">Interop</span></span>|<span data-ttu-id="7f3f4-136">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-136">Optional attribute.</span></span> <span data-ttu-id="7f3f4-137">Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="7f3f4-138">Zprostředkovatel komunikace</span><span class="sxs-lookup"><span data-stu-id="7f3f4-138">Interop</span></span>|<span data-ttu-id="7f3f4-139">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-139">Optional attribute.</span></span> <span data-ttu-id="7f3f4-140">Řídí zásady pro zařazování typů hodnot do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="7f3f4-141">Všechny atributy</span><span class="sxs-lookup"><span data-stu-id="7f3f4-141">All attributes</span></span>  
  
|<span data-ttu-id="7f3f4-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7f3f4-142">Value</span></span>|<span data-ttu-id="7f3f4-143">Popis</span><span class="sxs-lookup"><span data-stu-id="7f3f4-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f3f4-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7f3f4-144">*policy_setting*</span></span>|<span data-ttu-id="7f3f4-145">Nastavení, které se má použít u tohoto typu zásad</span><span class="sxs-lookup"><span data-stu-id="7f3f4-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="7f3f4-146">Možné hodnoty jsou `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`a `Required All`.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7f3f4-147">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7f3f4-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f3f4-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f3f4-148">Child Elements</span></span>  
 <span data-ttu-id="7f3f4-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f3f4-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f3f4-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f3f4-150">Parent Elements</span></span>  
  
|<span data-ttu-id="7f3f4-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f3f4-151">Element</span></span>|<span data-ttu-id="7f3f4-152">Popis</span><span class="sxs-lookup"><span data-stu-id="7f3f4-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f3f4-153">Typ\<</span><span class="sxs-lookup"><span data-stu-id="7f3f4-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="7f3f4-154">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f3f4-155">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f3f4-155">Remarks</span></span>  
 <span data-ttu-id="7f3f4-156">Element `<Subtypes>` aplikuje zásadu na všechny podtypy svého nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="7f3f4-157">Použijete ji, pokud chcete použít jiné zásady na odvozené typy a jejich základní třídy.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="7f3f4-158">Atributy Reflection, Serialization a interoperability jsou všechny volitelné, ale musí být přítomné aspoň jedno.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f3f4-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f3f4-159">Example</span></span>  
 <span data-ttu-id="7f3f4-160">Následující příklad definuje třídu s názvem `BaseClass` a podtřídou s názvem `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="7f3f4-161">Jak je znázorněno v následujícím kódu, soubor direktiv runtime explicitně nastaví `Dynamic` a zásady `Activate` pro `BaseClass` na `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="7f3f4-162">Z tohoto důvodu nelze vytvářet instance objektů typu `BaseClass` dynamicky ani voláním konstruktoru `BaseClass` třídy.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="7f3f4-163">Element `<Subtypes>` však umožňuje dynamicky vytvářet instance tříd odvozené od `BaseClass` a prostřednictvím volání jejich konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
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
  
 <span data-ttu-id="7f3f4-164">Z důvodu direktivy `<Subtypes>`, následující kód, který dynamicky vytváří instanci `Derived1`, voláním metody <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> se úspěšně spustí.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="7f3f4-165">Proměnná Block zde je <xref:System.Windows.Controls.TextBlock> objekt v prázdné aplikaci pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="7f3f4-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7f3f4-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f3f4-166">See also</span></span>

- [<span data-ttu-id="7f3f4-167">\<typ > elementu</span><span class="sxs-lookup"><span data-stu-id="7f3f4-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="7f3f4-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7f3f4-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7f3f4-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7f3f4-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="7f3f4-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7f3f4-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
