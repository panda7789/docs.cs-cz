---
title: Atributy (C#)
description: Naučte se, jak pomocí atributů přidružit metadata nebo deklarativní informace k kódu v jazyce C#. Atribut může být dotazován v době běhu pomocí reflexe.
ms.date: 04/26/2018
ms.openlocfilehash: 5c57838b649531d8e8fe89919771adf8830e7f54
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924982"
---
# <a name="attributes-c"></a><span data-ttu-id="c741a-104">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-104">Attributes (C#)</span></span>

<span data-ttu-id="c741a-105">Atributy poskytují výkonnou metodu přidružování metadat nebo deklarativní informace, s kódem (sestavení, typy, metodami, vlastnostmi a tak dále).</span><span class="sxs-lookup"><span data-stu-id="c741a-105">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="c741a-106">Po přiřazení atributu k entitě programu lze pomocí metody s názvem *reflexe*zadat dotaz na atribut v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c741a-106">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="c741a-107">Další informace naleznete v tématu [reflexe (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-107">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="c741a-108">Atributy mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c741a-108">Attributes have the following properties:</span></span>

- <span data-ttu-id="c741a-109">Atributy přidávají do programu metadata.</span><span class="sxs-lookup"><span data-stu-id="c741a-109">Attributes add metadata to your program.</span></span> <span data-ttu-id="c741a-110">*Metadata* jsou informace o typech definovaných v programu.</span><span class="sxs-lookup"><span data-stu-id="c741a-110">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="c741a-111">Všechna sestavení .NET obsahují zadanou sadu metadat, které popisují typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="c741a-111">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="c741a-112">Můžete přidat vlastní atributy a zadat případné další požadované informace.</span><span class="sxs-lookup"><span data-stu-id="c741a-112">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="c741a-113">Další informace naleznete v tématu a [vytváření vlastních atributů (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-113">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="c741a-114">Jeden nebo více atributů lze použít pro celá sestavení, moduly nebo menší prvky programu, jako jsou třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c741a-114">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="c741a-115">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c741a-115">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="c741a-116">Váš program může prošetřit vlastní metadata nebo metadata v jiných programech pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="c741a-116">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="c741a-117">Další informace naleznete v tématu [přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-117">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="c741a-118">Použití atributů</span><span class="sxs-lookup"><span data-stu-id="c741a-118">Using attributes</span></span>

<span data-ttu-id="c741a-119">Atributy lze umístit na většinu jakékoli deklarace, i když konkrétní atribut může omezit typy deklarací, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="c741a-119">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="c741a-120">V jazyce C# zadáte atribut tak, že umístíte název atributu uzavřený do hranatých závorek ([]) nad deklaraci entity, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="c741a-120">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="c741a-121">V tomto příkladu <xref:System.SerializableAttribute> je atribut použit k použití konkrétní charakteristiky pro třídu:</span><span class="sxs-lookup"><span data-stu-id="c741a-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="c741a-122">Metoda s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarována jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c741a-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="c741a-123">V deklaraci lze umístit více než jeden atribut, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c741a-123">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="c741a-124">Některé atributy lze pro danou entitu zadat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="c741a-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="c741a-125">Příklad takového atributu Multiuse je <xref:System.Diagnostics.ConditionalAttribute> :</span><span class="sxs-lookup"><span data-stu-id="c741a-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="c741a-126">Podle konvence názvy všech atributů končí slovem "Attribute", aby je bylo možné odlišit od ostatních položek v knihovnách .NET.</span><span class="sxs-lookup"><span data-stu-id="c741a-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="c741a-127">Při použití atributů v kódu však není nutné zadávat příponu atributu.</span><span class="sxs-lookup"><span data-stu-id="c741a-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="c741a-128">Například `[DllImport]` je ekvivalentní k `[DllImportAttribute]` , ale `DllImportAttribute` je skutečným názvem atributu v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="c741a-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="c741a-129">Parametry atributu</span><span class="sxs-lookup"><span data-stu-id="c741a-129">Attribute parameters</span></span>

<span data-ttu-id="c741a-130">Mnoho atributů má parametry, které mohou být pozice, nepojmenované nebo pojmenované.</span><span class="sxs-lookup"><span data-stu-id="c741a-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="c741a-131">V určitém pořadí musí být zadány všechny poziční parametry a nelze je vynechat.</span><span class="sxs-lookup"><span data-stu-id="c741a-131">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="c741a-132">Pojmenované parametry jsou volitelné a lze je zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c741a-132">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="c741a-133">Poziční parametry jsou uvedeny jako první.</span><span class="sxs-lookup"><span data-stu-id="c741a-133">Positional parameters are specified first.</span></span> <span data-ttu-id="c741a-134">Například tyto tři atributy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="c741a-134">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="c741a-135">První parametr, název knihovny DLL, je pozice a vždy se nachází jako první; ostatní mají název.</span><span class="sxs-lookup"><span data-stu-id="c741a-135">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="c741a-136">V takovém případě mají obě pojmenované parametry výchozí hodnotu false, takže je lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="c741a-136">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="c741a-137">Poziční parametry odpovídají parametrům konstruktoru atributu.</span><span class="sxs-lookup"><span data-stu-id="c741a-137">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="c741a-138">Pojmenované nebo volitelné parametry odpovídají buď vlastnostem nebo polím atributu.</span><span class="sxs-lookup"><span data-stu-id="c741a-138">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="c741a-139">Informace o výchozích hodnotách parametrů naleznete v dokumentaci k jednotlivým atributům.</span><span class="sxs-lookup"><span data-stu-id="c741a-139">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="c741a-140">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="c741a-140">Attribute targets</span></span>

<span data-ttu-id="c741a-141">*Cíl* atributu je entita, na kterou se atribut vztahuje.</span><span class="sxs-lookup"><span data-stu-id="c741a-141">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="c741a-142">Atribut může například platit pro třídu, konkrétní metodu nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="c741a-142">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="c741a-143">Ve výchozím nastavení se atribut vztahuje na prvek, který následuje.</span><span class="sxs-lookup"><span data-stu-id="c741a-143">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="c741a-144">Můžete ale také explicitně určit, zda je atribut použit na metodu, nebo na jeho parametr nebo na jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c741a-144">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="c741a-145">K explicitní identifikaci cíle atributu použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="c741a-145">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="c741a-146">Seznam možných `target` hodnot je uveden v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c741a-146">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="c741a-147">Cílová hodnota</span><span class="sxs-lookup"><span data-stu-id="c741a-147">Target value</span></span>|<span data-ttu-id="c741a-148">Platí pro</span><span class="sxs-lookup"><span data-stu-id="c741a-148">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="c741a-149">Celé sestavení</span><span class="sxs-lookup"><span data-stu-id="c741a-149">Entire assembly</span></span>|
|`module`|<span data-ttu-id="c741a-150">Aktuální modul sestavení</span><span class="sxs-lookup"><span data-stu-id="c741a-150">Current assembly module</span></span>|
|`field`|<span data-ttu-id="c741a-151">Pole ve třídě nebo struktuře</span><span class="sxs-lookup"><span data-stu-id="c741a-151">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="c741a-152">Událost</span><span class="sxs-lookup"><span data-stu-id="c741a-152">Event</span></span>|
|`method`|<span data-ttu-id="c741a-153">`get` `set` Přístupové objekty metody nebo vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c741a-153">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="c741a-154">Parametry metody nebo `set` parametry přístupového objektu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c741a-154">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="c741a-155">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c741a-155">Property</span></span>|
|`return`|<span data-ttu-id="c741a-156">Návratová hodnota metody, indexeru vlastností nebo `get` přistupujícího objektu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c741a-156">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="c741a-157">Struktura, třída, rozhraní, výčet nebo delegát</span><span class="sxs-lookup"><span data-stu-id="c741a-157">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="c741a-158">Zadejte `field` cílovou hodnotu pro použití atributu pro pole zálohování vytvořené pro [automaticky implementovanou vlastnost](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-158">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="c741a-159">Následující příklad ukazuje, jak použít atributy na sestavení a moduly.</span><span class="sxs-lookup"><span data-stu-id="c741a-159">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="c741a-160">Další informace najdete v tématu [běžné atributy (C#)](../../../language-reference/attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-160">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="c741a-161">Následující příklad ukazuje, jak použít atributy na metody, parametry metody a návratové hodnoty metody v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c741a-161">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="c741a-162">Bez ohledu na cíle `ValidatedContract` , které jsou definovány jako platné, je `return` nutné zadat cíl, a to i v případě, že `ValidatedContract` byly definovány pro použití pouze pro návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c741a-162">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="c741a-163">Jinými slovy, kompilátor nebude používat `AttributeUsage` informace pro vyřešení dvojznačných cílů atributu.</span><span class="sxs-lookup"><span data-stu-id="c741a-163">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="c741a-164">Další informace naleznete v tématu [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-164">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="c741a-165">Běžné použití atributů</span><span class="sxs-lookup"><span data-stu-id="c741a-165">Common uses for attributes</span></span>

<span data-ttu-id="c741a-166">Následující seznam obsahuje několik běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="c741a-166">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="c741a-167">Označení metod pomocí `WebMethod` atributu ve webových službách k označení toho, že by měla být metoda volat přes protokol SOAP.</span><span class="sxs-lookup"><span data-stu-id="c741a-167">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="c741a-168">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c741a-168">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="c741a-169">Popisuje způsob zařazení parametrů metody při spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="c741a-169">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="c741a-170">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c741a-170">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="c741a-171">Popisuje vlastnosti modelu COM pro třídy, metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c741a-171">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="c741a-172">Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="c741a-172">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="c741a-173">Popisuje vaše sestavení s ohledem na název, verzi, popis nebo ochrannou známku.</span><span class="sxs-lookup"><span data-stu-id="c741a-173">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="c741a-174">Popisuje, kteří členové třídy mají být serializováni k trvalému serializaci.</span><span class="sxs-lookup"><span data-stu-id="c741a-174">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="c741a-175">Popisuje, jak mapovat mezi členy třídy a uzly XML pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="c741a-175">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="c741a-176">Popisuje požadavky na zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="c741a-176">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="c741a-177">Určení vlastností používaných k vymáhání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c741a-177">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="c741a-178">Řízení optimalizace pomocí kompilátoru JIT (just-in-time), takže kód zůstane snadno laděn.</span><span class="sxs-lookup"><span data-stu-id="c741a-178">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="c741a-179">Získání informací o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="c741a-179">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c741a-180">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c741a-180">Related sections</span></span>

<span data-ttu-id="c741a-181">Další informace najdete tady:</span><span class="sxs-lookup"><span data-stu-id="c741a-181">For more information, see:</span></span>

- [<span data-ttu-id="c741a-182">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-182">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="c741a-183">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-183">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="c741a-184">Postup vytvoření sjednocení jazyka C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-184">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="c741a-185">Společné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-185">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="c741a-186">Informace o volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-186">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="c741a-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="c741a-187">See also</span></span>

- [<span data-ttu-id="c741a-188">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c741a-188">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="c741a-189">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="c741a-189">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="c741a-190">Atributy</span><span class="sxs-lookup"><span data-stu-id="c741a-190">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="c741a-191">Používání atributů v jazyce C #</span><span class="sxs-lookup"><span data-stu-id="c741a-191">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
