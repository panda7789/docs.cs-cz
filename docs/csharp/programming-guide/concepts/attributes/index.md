---
title: Atributy (C#)
ms.date: 04/26/2018
ms.openlocfilehash: c33d93a4af91e0c61546e8d51ab470f2889c095c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127943"
---
# <a name="attributes-c"></a><span data-ttu-id="a6f5a-102">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-102">Attributes (C#)</span></span>

<span data-ttu-id="a6f5a-103">Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="a6f5a-104">Po atributu je spojen s entitou program, atribut může být dotázán za běhu pomocí techniky označované jako *reflexe*.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="a6f5a-105">Další informace najdete v tématu [reflexe (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="a6f5a-106">Atributy mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="a6f5a-107">Atributy přidat metadata do programu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="a6f5a-108">*Metadata* obsahuje informace o typy definované v programu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="a6f5a-109">Všechna sestavení rozhraní .NET obsahují zadanou množinu metadata popisující typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="a6f5a-110">Můžete přidat vlastní atributy k jakékoli další informace, které je nutné zadat.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="a6f5a-111">Další informace najdete v tématu, [vytváření vlastních atributů (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="a6f5a-112">Můžete použít jeden nebo více atributů na celé sestavení, moduly nebo menší prvky programu, jako například třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="a6f5a-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="a6f5a-114">Aplikace můžete zkontrolovat svou vlastní metadaty nebo metadaty v jiných aplikacích pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="a6f5a-115">Další informace najdete v tématu [přístup k atributy podle použití reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="a6f5a-116">Pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="a6f5a-116">Using attributes</span></span>

<span data-ttu-id="a6f5a-117">Atributy je možné použít u libovolného deklarace, když konkrétního atributu můžete narazit na omezení typů deklarace, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="a6f5a-118">V jazyce C# zadejte atribut tak, že název atributu uzavřeny do hranatých závorek ([]) nad deklarací entit, ke kterému se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="a6f5a-119">V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování konkrétní charakteristiku pro třídu:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="a6f5a-120">Metodu s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="a6f5a-121">Více než jeden atribut je možné použít v deklaraci jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="a6f5a-122">Některé atributy můžete zadat více než jednou pro danou entitu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="a6f5a-123">Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="a6f5a-124">Podle konvence končí všechny názvy atributů slovem "Atribut", abychom je odlišili od ostatních položek v knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="a6f5a-125">Ale není potřeba zadat atribut přípon při použití atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="a6f5a-126">Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="a6f5a-127">Atribut parametrů</span><span class="sxs-lookup"><span data-stu-id="a6f5a-127">Attribute parameters</span></span>

<span data-ttu-id="a6f5a-128">Mnoho atributů mít parametry, které mohou být poziční, nepojmenovaný nebo s názvem.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="a6f5a-129">Žádné poziční parametry musí být zadán v určitém pořadí a nelze jej vynechat.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="a6f5a-130">Pojmenované parametry jsou volitelné a dá se zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="a6f5a-131">Poziční parametry jsou zadán jako první.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-131">Positional parameters are specified first.</span></span> <span data-ttu-id="a6f5a-132">Například tyto tři atributy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="a6f5a-133">První parametr, název knihovny DLL je poziční a dodává se vždycky první; ostatní jsou pojmenovány.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="a6f5a-134">V takovém případě pojmenované výchozí parametry na hodnotu false, takže lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="a6f5a-135">Poziční parametry odpovídají parametry konstruktoru atributu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="a6f5a-136">Pojmenované a nepovinné parametry odpovídají vlastnosti nebo pole atributu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="a6f5a-137">V dokumentaci jednotlivých atributů informace o výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="a6f5a-138">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="a6f5a-138">Attribute targets</span></span>

<span data-ttu-id="a6f5a-139">*Cílové* atributu je entita, ke kterému se vztahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-139">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="a6f5a-140">Atribut může například použít pro třídu, konkrétní metody nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="a6f5a-141">Ve výchozím nastavení atribut se vztahuje k elementu, který předchází.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-141">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="a6f5a-142">Ale můžete také explicitně identifikovat, například zda atributu se použije k metodě, její parametr nebo na jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="a6f5a-143">Cíl atributu explicitně identifikovat, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="a6f5a-144">Seznam možných `target` hodnot je uveden v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="a6f5a-145">Cílová hodnota</span><span class="sxs-lookup"><span data-stu-id="a6f5a-145">Target value</span></span>|<span data-ttu-id="a6f5a-146">Platí pro</span><span class="sxs-lookup"><span data-stu-id="a6f5a-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="a6f5a-147">Celé sestavení</span><span class="sxs-lookup"><span data-stu-id="a6f5a-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="a6f5a-148">Aktuální modul sestavení</span><span class="sxs-lookup"><span data-stu-id="a6f5a-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="a6f5a-149">Pole třídy nebo struktury</span><span class="sxs-lookup"><span data-stu-id="a6f5a-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="a6f5a-150">Událost</span><span class="sxs-lookup"><span data-stu-id="a6f5a-150">Event</span></span>|
|`method`|<span data-ttu-id="a6f5a-151">Metoda nebo `get` a `set` přistupující objekty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a6f5a-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="a6f5a-152">Parametry metody nebo `set` parametry přistupující objekt vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a6f5a-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="a6f5a-153">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="a6f5a-153">Property</span></span>|
|`return`|<span data-ttu-id="a6f5a-154">Návratová hodnota metody, vlastnosti indexeru nebo `get` přistupující objekt vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a6f5a-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="a6f5a-155">Struktury, třídy, interface, enum nebo delegate</span><span class="sxs-lookup"><span data-stu-id="a6f5a-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="a6f5a-156">Zadejte `field` cílovou hodnotu použijte atribut na pomocné pole vytvoří pro [automaticky implementované vlastnosti](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="a6f5a-157">Následující příklad ukazuje způsob použití atributů pro sestavení a modulů.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="a6f5a-158">Další informace najdete v tématu [běžné atributy (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="a6f5a-159">Následující příklad ukazuje způsob použití atributů pro metody, parametry metody a metody návratové hodnoty v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="a6f5a-160">Bez ohledu na to cíle, na kterém `ValidatedContract` je definován jako platný, `return` cíl musí být zadaný, i v případě `ValidatedContract` byly definovány bylo použito pouze na návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="a6f5a-161">Jinými slovy, nebudeme je používat kompilátor `AttributeUsage` informace k jejímu vyřešení nejednoznačný atribut cíle.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="a6f5a-162">Další informace najdete v tématu [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5a-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="a6f5a-163">Běžné použití atributů</span><span class="sxs-lookup"><span data-stu-id="a6f5a-163">Common uses for attributes</span></span>

<span data-ttu-id="a6f5a-164">Následující seznam obsahuje několik běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="a6f5a-165">Označení metody pomocí `WebMethod` atribut ve webové služby k označení, že metoda mělo by být umožněno prostřednictvím protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="a6f5a-166">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="a6f5a-167">Popis způsobu zařazení parametrů metody při vzájemné spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="a6f5a-168">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="a6f5a-169">Popis vlastnosti modelu COM pro třídy, metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="a6f5a-170">Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="a6f5a-171">Popisující vaše sestavení z hlediska název, verze, popis nebo ochranná známka.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="a6f5a-172">Popisující, které členy třídy k serializaci trvalosti.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="a6f5a-173">Popisující způsob, jakým mapování mezi členy třídy a z uzlů XML pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="a6f5a-174">Popisuje požadavky zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="a6f5a-175">Zadání vlastnosti používá k vynucení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="a6f5a-176">Řízení optimalizace kompilátoru just-in-time (JIT), tak zůstane usnadňuje ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="a6f5a-177">Získání informací o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="a6f5a-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a6f5a-178">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a6f5a-178">Related sections</span></span>

<span data-ttu-id="a6f5a-179">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="a6f5a-179">For more information, see:</span></span>

- [<span data-ttu-id="a6f5a-180">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="a6f5a-181">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="a6f5a-182">Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="a6f5a-183">Běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="a6f5a-184">Informace o volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="a6f5a-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6f5a-185">See Also</span></span>

- [<span data-ttu-id="a6f5a-186">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a6f5a-186">C# Programming Guide</span></span>](../../index.md)  
- [<span data-ttu-id="a6f5a-187">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="a6f5a-187">Reflection (C#)</span></span>](../reflection.md)  
- [<span data-ttu-id="a6f5a-188">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6f5a-188">Attributes</span></span>](../../../../standard/attributes/index.md)  
- [<span data-ttu-id="a6f5a-189">Použití atributů v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a6f5a-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)  
