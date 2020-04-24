---
title: Atributy (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 0379bb76cf18ff836bd14aafb9cb97c30aee8ec7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645489"
---
# <a name="attributes-c"></a><span data-ttu-id="b9cca-102">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-102">Attributes (C#)</span></span>

<span data-ttu-id="b9cca-103">Atributy poskytují výkonnou metodu připojování metadat nebo deklarativních informací s kódem (sestavení, typy, metody, vlastnosti atd.).</span><span class="sxs-lookup"><span data-stu-id="b9cca-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="b9cca-104">Poté, co je atribut přidružen k entitě programu, může být tento atribut dotazován za běhu pomocí techniky nazývané *reflexe*.</span><span class="sxs-lookup"><span data-stu-id="b9cca-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="b9cca-105">Další informace naleznete v [tématu Reflection (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b9cca-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="b9cca-106">Atributy mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b9cca-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="b9cca-107">Atributy přidávají do programu metadata.</span><span class="sxs-lookup"><span data-stu-id="b9cca-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="b9cca-108">*Metadata* jsou informace o typech definovaných v programu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="b9cca-109">Všechna sestavení rozhraní .NET obsahují zadanou sadu metadat, která popisuje typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9cca-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="b9cca-110">Můžete přidat vlastní atributy a zadat další informace, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="b9cca-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="b9cca-111">Další informace naleznete v [tématu Vytváření vlastních atributů (C#).](creating-custom-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="b9cca-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="b9cca-112">Jeden nebo více atributů můžete použít na celá sestavení, moduly nebo menší prvky programu, jako jsou třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9cca-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="b9cca-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b9cca-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="b9cca-114">Program může zkoumat vlastní metadata nebo metadata v jiných programech pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="b9cca-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="b9cca-115">Další informace naleznete [v tématu Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b9cca-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="b9cca-116">Použití atributů</span><span class="sxs-lookup"><span data-stu-id="b9cca-116">Using attributes</span></span>

<span data-ttu-id="b9cca-117">Atributy lze umístit na většinu jakékoli prohlášení, i když konkrétní atribut může omezit typy deklarací, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="b9cca-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="b9cca-118">V c# zadáte atribut umístěním názvu atributu uzavřeného v hranatých závorkách ([]) nad deklaraci entity, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="b9cca-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="b9cca-119">V tomto příkladu <xref:System.SerializableAttribute> se atribut používá k použití určité charakteristiky na třídu:</span><span class="sxs-lookup"><span data-stu-id="b9cca-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="b9cca-120">Metoda s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarována jako následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b9cca-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="b9cca-121">Více než jeden atribut lze umístit na prohlášení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b9cca-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="b9cca-122">Některé atributy lze zadat více než jednou pro danou entitu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="b9cca-123">Příkladem takového víceúčelového atributu je <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="b9cca-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="b9cca-124">Podle konvence všechny názvy atributů končí slovem "Atribut", aby se odlišily od ostatních položek v knihovnách .NET.</span><span class="sxs-lookup"><span data-stu-id="b9cca-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="b9cca-125">Při použití atributů v kódu však není nutné zadávat příponu atributu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="b9cca-126">Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, `DllImportAttribute` ale je skutečný název atributu v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9cca-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="b9cca-127">Parametry atributů</span><span class="sxs-lookup"><span data-stu-id="b9cca-127">Attribute parameters</span></span>

<span data-ttu-id="b9cca-128">Mnoho atributů má parametry, které mohou být poziční, nepojmenované nebo pojmenované.</span><span class="sxs-lookup"><span data-stu-id="b9cca-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="b9cca-129">Všechny poziční parametry musí být zadány v určitém pořadí a nelze je vynechat.</span><span class="sxs-lookup"><span data-stu-id="b9cca-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="b9cca-130">Pojmenované parametry jsou volitelné a lze je zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b9cca-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="b9cca-131">Nejprve jsou zadány poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="b9cca-131">Positional parameters are specified first.</span></span> <span data-ttu-id="b9cca-132">Například tyto tři atributy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="b9cca-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="b9cca-133">První parametr, název dll, je poziční a vždy je na prvním místě; ostatní jsou pojmenovány.</span><span class="sxs-lookup"><span data-stu-id="b9cca-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="b9cca-134">V tomto případě oba pojmenované parametry výchozí false, takže mohou být vynechány.</span><span class="sxs-lookup"><span data-stu-id="b9cca-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="b9cca-135">Poziční parametry odpovídají parametrům konstruktoru atributu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="b9cca-136">Pojmenované nebo volitelné parametry odpovídají vlastnostem nebo polím atributu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="b9cca-137">Informace o výchozích hodnotách parametrů naleznete v dokumentaci k jednotlivým atributům.</span><span class="sxs-lookup"><span data-stu-id="b9cca-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="b9cca-138">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="b9cca-138">Attribute targets</span></span>

<span data-ttu-id="b9cca-139">*Cílem* atributu je entita, na kterou se atribut vztahuje.</span><span class="sxs-lookup"><span data-stu-id="b9cca-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="b9cca-140">Atribut může například použít pro třídu, určitou metodu nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9cca-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="b9cca-141">Ve výchozím nastavení se atribut vztahuje na prvek, který za ním následuje.</span><span class="sxs-lookup"><span data-stu-id="b9cca-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="b9cca-142">Můžete však také explicitně určit, například zda je atribut použit pro metodu nebo její parametr nebo na jeho vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="b9cca-143">Chcete-li explicitně identifikovat cíl atributu, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="b9cca-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="b9cca-144">Seznam možných `target` hodnot je uveden v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b9cca-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="b9cca-145">Cílová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9cca-145">Target value</span></span>|<span data-ttu-id="b9cca-146">Platí pro</span><span class="sxs-lookup"><span data-stu-id="b9cca-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="b9cca-147">Celá sestava</span><span class="sxs-lookup"><span data-stu-id="b9cca-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="b9cca-148">Aktuální montážní modul</span><span class="sxs-lookup"><span data-stu-id="b9cca-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="b9cca-149">Pole ve třídě nebo struktuře</span><span class="sxs-lookup"><span data-stu-id="b9cca-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="b9cca-150">Událost</span><span class="sxs-lookup"><span data-stu-id="b9cca-150">Event</span></span>|
|`method`|<span data-ttu-id="b9cca-151">Přístupové `get` `set` objekty metody nebo vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9cca-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="b9cca-152">Parametry metody `set` nebo parametry přístupového objektu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b9cca-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="b9cca-153">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b9cca-153">Property</span></span>|
|`return`|<span data-ttu-id="b9cca-154">Vrácená hodnota metody, indexeru `get` vlastností nebo přistupujícího objektu vlastností</span><span class="sxs-lookup"><span data-stu-id="b9cca-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="b9cca-155">Struktura, třída, rozhraní, výčt nebo delegát</span><span class="sxs-lookup"><span data-stu-id="b9cca-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="b9cca-156">Zadali byste `field` cílovou hodnotu, která má atribut použít na záložní pole vytvořené pro [automaticky implementovanou vlastnost](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="b9cca-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="b9cca-157">Následující příklad ukazuje, jak použít atributy sestavení a modulů.</span><span class="sxs-lookup"><span data-stu-id="b9cca-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="b9cca-158">Další informace naleznete [v tématu Common Attributes (C#)](../../../language-reference/attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="b9cca-158">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="b9cca-159">Následující příklad ukazuje, jak použít atributy metody, parametry metody a metody vrácené hodnoty v C#.</span><span class="sxs-lookup"><span data-stu-id="b9cca-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="b9cca-160">Bez ohledu na cíle, na kterých `ValidatedContract` `return` je definována jako platná, cíl musí být určen, i když `ValidatedContract` byly definovány použít pouze pro vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9cca-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="b9cca-161">Jinými slovy kompilátor nebude `AttributeUsage` používat informace k vyřešení nejednoznačných cílů atributů.</span><span class="sxs-lookup"><span data-stu-id="b9cca-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="b9cca-162">Další informace naleznete v tématu [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="b9cca-162">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="b9cca-163">Běžné použití atributů</span><span class="sxs-lookup"><span data-stu-id="b9cca-163">Common uses for attributes</span></span>

<span data-ttu-id="b9cca-164">Následující seznam obsahuje několik běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="b9cca-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="b9cca-165">Metody označení `WebMethod` pomocí atributu ve webových službách označují, že metoda by měla být volatelná přes protokol SOAP.</span><span class="sxs-lookup"><span data-stu-id="b9cca-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="b9cca-166">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b9cca-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="b9cca-167">Popisující, jak zařazovat parametry metody při spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="b9cca-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="b9cca-168">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b9cca-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="b9cca-169">Popisující vlastnosti com pro třídy, metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b9cca-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="b9cca-170">Volání nespravovaného <xref:System.Runtime.InteropServices.DllImportAttribute> kódu pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="b9cca-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="b9cca-171">Popis vašeho sestavení z hlediska názvu, verze, popisu nebo ochranné známky.</span><span class="sxs-lookup"><span data-stu-id="b9cca-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="b9cca-172">Popisující, které členy třídy serializovat pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="b9cca-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="b9cca-173">Popis mapování mezi členy třídy a uzly XML pro serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="b9cca-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="b9cca-174">Popisující požadavky na zabezpečení metod.</span><span class="sxs-lookup"><span data-stu-id="b9cca-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="b9cca-175">Určení charakteristik používaných k vynucení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b9cca-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="b9cca-176">Řízení optimalizace kompilátorem just-in-time (JIT), takže kód zůstává snadno ladit.</span><span class="sxs-lookup"><span data-stu-id="b9cca-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="b9cca-177">Získání informací o volajícím na metodu.</span><span class="sxs-lookup"><span data-stu-id="b9cca-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b9cca-178">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b9cca-178">Related sections</span></span>

<span data-ttu-id="b9cca-179">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="b9cca-179">For more information, see:</span></span>

- [<span data-ttu-id="b9cca-180">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="b9cca-181">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="b9cca-182">Jak vytvořit sjednocení C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-182">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="b9cca-183">Běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-183">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="b9cca-184">Informace o volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-184">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="b9cca-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9cca-185">See also</span></span>

- [<span data-ttu-id="b9cca-186">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9cca-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="b9cca-187">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="b9cca-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="b9cca-188">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9cca-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="b9cca-189">Použití atributů v C #</span><span class="sxs-lookup"><span data-stu-id="b9cca-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
