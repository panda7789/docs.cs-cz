---
title: Atributy (C#)
ms.date: 04/26/2018
ms.openlocfilehash: fe94f0ee778f14581fd7949f705cc22f12058b27
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956069"
---
# <a name="attributes-c"></a><span data-ttu-id="0e94b-102">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-102">Attributes (C#)</span></span>

<span data-ttu-id="0e94b-103">Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále).</span><span class="sxs-lookup"><span data-stu-id="0e94b-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="0e94b-104">Po atribut je spojen s entitou program, může být dotazován atribut v době běhu pomocí techniky názvem *reflexe*.</span><span class="sxs-lookup"><span data-stu-id="0e94b-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="0e94b-105">Další informace najdete v tématu [reflexe (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0e94b-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="0e94b-106">Atributy mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0e94b-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="0e94b-107">Atributy přidat metadata do programu.</span><span class="sxs-lookup"><span data-stu-id="0e94b-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="0e94b-108">*Metadata* je informace o typech definované v programu.</span><span class="sxs-lookup"><span data-stu-id="0e94b-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="0e94b-109">Všechny sestavení .NET obsahovat zadanou sadu metadata, která popisuje typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e94b-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="0e94b-110">Můžete přidat vlastní atributy pro žádné další informace, které jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="0e94b-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="0e94b-111">Další informace najdete v tématu, [vytváření vlastní atributy (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0e94b-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="0e94b-112">Celý sestavení, moduly nebo menší program prvky, jako jsou například třídy a vlastnosti, můžete použít jeden nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="0e94b-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="0e94b-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0e94b-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="0e94b-114">Váš program můžete zkontrolovat svůj vlastní metadata nebo metadata v ostatních aplikacích pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="0e94b-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="0e94b-115">Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0e94b-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="0e94b-116">Pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="0e94b-116">Using attributes</span></span>

<span data-ttu-id="0e94b-117">Atributy je možné použít u libovolného deklarace, když konkrétní atribut může omezit přístup k deklarace, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="0e94b-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="0e94b-118">V jazyce C# zadejte atribut tím, že název atributu uzavřeny do hranatých závorek ([]) nad deklaraci entity, na který se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="0e94b-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="0e94b-119">V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování zvláštní vlastností pro třídu:</span><span class="sxs-lookup"><span data-stu-id="0e94b-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="0e94b-120">Metody s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e94b-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="0e94b-121">Více než jeden atribut je možné použít u deklaraci jako na následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e94b-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="0e94b-122">Některé atributy lze zadat více než jednou pro danou entitu.</span><span class="sxs-lookup"><span data-stu-id="0e94b-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="0e94b-123">Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="0e94b-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="0e94b-124">Podle konvence ukončete všechny názvy atributů slovem "Atribut" jej odlišit od jiných položek v na knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="0e94b-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="0e94b-125">Však není potřeba zadejte příponu atribut při použití atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="0e94b-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="0e94b-126">Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e94b-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="0e94b-127">Atribut parametry</span><span class="sxs-lookup"><span data-stu-id="0e94b-127">Attribute parameters</span></span>

<span data-ttu-id="0e94b-128">Počet atributů mít parametry, které může být poziční, nepojmenovaný nebo s názvem.</span><span class="sxs-lookup"><span data-stu-id="0e94b-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="0e94b-129">Žádné poziční parametry musí být zadaný v určitém pořadí a nelze jej vynechat.</span><span class="sxs-lookup"><span data-stu-id="0e94b-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="0e94b-130">Pojmenované parametry jsou volitelné a lze jej zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0e94b-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="0e94b-131">Nejprve jsou zadány poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="0e94b-131">Positional parameters are specified first.</span></span> <span data-ttu-id="0e94b-132">Například odpovídají tyto tři atributy:</span><span class="sxs-lookup"><span data-stu-id="0e94b-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="0e94b-133">První parametr název DLL je poziční a dodává se vždy první; ostatní s názvem.</span><span class="sxs-lookup"><span data-stu-id="0e94b-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="0e94b-134">V takovém případě i s názvem výchozí parametry na hodnotu false, můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="0e94b-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="0e94b-135">Poziční parametry odpovídají parametry konstruktoru atributu.</span><span class="sxs-lookup"><span data-stu-id="0e94b-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="0e94b-136">S názvem nebo volitelné parametry odpovídají vlastnosti nebo pole atributu.</span><span class="sxs-lookup"><span data-stu-id="0e94b-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="0e94b-137">Vyhledejte jednotlivé atributy dokumentaci informace o výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="0e94b-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="0e94b-138">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="0e94b-138">Attribute targets</span></span>

<span data-ttu-id="0e94b-139">*Cíl* atributu je ta entita, na které se vztahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="0e94b-139">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="0e94b-140">Atribut může například použít třídu, konkrétní metody nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e94b-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="0e94b-141">Ve výchozím nastavení atribut vztahuje k elementu, který ho předchází.</span><span class="sxs-lookup"><span data-stu-id="0e94b-141">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="0e94b-142">Ale můžete také explicitně identifikovat, například zda atribut se použije na metodu, nebo její parametr nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e94b-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="0e94b-143">K identifikaci explicitně atribut target, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="0e94b-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="0e94b-144">Seznam možných `target` hodnoty je uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0e94b-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="0e94b-145">Hodnota cíle</span><span class="sxs-lookup"><span data-stu-id="0e94b-145">Target value</span></span>|<span data-ttu-id="0e94b-146">Platí pro</span><span class="sxs-lookup"><span data-stu-id="0e94b-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="0e94b-147">Celý sestavení</span><span class="sxs-lookup"><span data-stu-id="0e94b-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="0e94b-148">Aktuální modul sestavení</span><span class="sxs-lookup"><span data-stu-id="0e94b-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="0e94b-149">Pole ve třídě nebo struktury</span><span class="sxs-lookup"><span data-stu-id="0e94b-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="0e94b-150">Událost</span><span class="sxs-lookup"><span data-stu-id="0e94b-150">Event</span></span>|
|`method`|<span data-ttu-id="0e94b-151">Metoda nebo `get` a `set` vlastnost přístupové objekty</span><span class="sxs-lookup"><span data-stu-id="0e94b-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="0e94b-152">Parametry metody nebo `set` parametry přistupující objekt vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0e94b-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="0e94b-153">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0e94b-153">Property</span></span>|
|`return`|<span data-ttu-id="0e94b-154">Návratová hodnota metody, vlastnosti indexer nebo `get` přistupující objekt vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0e94b-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="0e94b-155">Struktura, třídu, rozhraní, výčet nebo delegáta</span><span class="sxs-lookup"><span data-stu-id="0e94b-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="0e94b-156">Chcete-li zadejte `field` hodnota cíle pro použití atributu na pole Základní vytvořili pro [automaticky implementované vlastnosti](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="0e94b-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="0e94b-157">Následující příklad ukazuje, jak chcete použít atributy pro sestavení a moduly.</span><span class="sxs-lookup"><span data-stu-id="0e94b-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="0e94b-158">Další informace najdete v tématu [běžné atributy (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0e94b-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="0e94b-159">Následující příklad ukazuje, jak se má použít k metodám, metoda parametry, atributy a metoda návratové hodnoty v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="0e94b-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="0e94b-160">Bez ohledu na to cíle, na kterém `ValidatedContract` je definován jako platný, `return` cíl musí být zadaný, i když `ValidatedContract` byly definovány se provádí pouze návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0e94b-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="0e94b-161">Jinými slovy, nebude používat kompilátor `AttributeUsage` informace týkající se řešení cíle nejednoznačný atributů.</span><span class="sxs-lookup"><span data-stu-id="0e94b-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="0e94b-162">Další informace najdete v tématu [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="0e94b-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="0e94b-163">Běžná použití atributů</span><span class="sxs-lookup"><span data-stu-id="0e94b-163">Common uses for attributes</span></span>

<span data-ttu-id="0e94b-164">Následující seznam obsahuje několik příkladů běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="0e94b-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="0e94b-165">Označení metody pomocí `WebMethod` atribut v webové služby k označení, že metoda by měla být s přes protokol SOAP.</span><span class="sxs-lookup"><span data-stu-id="0e94b-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="0e94b-166">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0e94b-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="0e94b-167">Popisující, jak při vzájemné spolupráci s nativním kódem zařazování parametry metody.</span><span class="sxs-lookup"><span data-stu-id="0e94b-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="0e94b-168">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0e94b-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="0e94b-169">Popisující COM vlastnosti tříd, metod a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e94b-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="0e94b-170">Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="0e94b-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="0e94b-171">Která popisují vaše sestavení z hlediska název, verze, popis nebo ochranná známka.</span><span class="sxs-lookup"><span data-stu-id="0e94b-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="0e94b-172">Popisující, kteří členové třídy k serializaci trvalosti.</span><span class="sxs-lookup"><span data-stu-id="0e94b-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="0e94b-173">Popisující, jak pro mapování mezi členy třídy a z uzlů XML pro serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="0e94b-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="0e94b-174">Popisuje požadavky na zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="0e94b-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="0e94b-175">Zadání vlastnosti slouží k vynucení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e94b-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="0e94b-176">Řízení optimalizace kompilátorem v běhu (JIT), takže stále snadno ladit kód.</span><span class="sxs-lookup"><span data-stu-id="0e94b-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="0e94b-177">Získání informací o volajícího, aby metoda.</span><span class="sxs-lookup"><span data-stu-id="0e94b-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0e94b-178">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0e94b-178">Related sections</span></span>

<span data-ttu-id="0e94b-179">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="0e94b-179">For more information, see:</span></span>

- [<span data-ttu-id="0e94b-180">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="0e94b-181">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="0e94b-182">Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="0e94b-183">Mezi běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="0e94b-184">Informace o subjektu volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="0e94b-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e94b-185">See also</span></span>

 [<span data-ttu-id="0e94b-186">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0e94b-186">C# Programming Guide</span></span>](../../index.md)  
 [<span data-ttu-id="0e94b-187">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="0e94b-187">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="0e94b-188">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e94b-188">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="0e94b-189">Pomocí atributů v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0e94b-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)  
