---
title: Atributy (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2993ef3f424aa6487681e194f21e0f82193342ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-c"></a><span data-ttu-id="56dd7-102">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-102">Attributes (C#)</span></span>
<span data-ttu-id="56dd7-103">Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále).</span><span class="sxs-lookup"><span data-stu-id="56dd7-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="56dd7-104">Po atribut je spojen s entitou program, může být dotazován atribut v době běhu pomocí techniky názvem *reflexe*.</span><span class="sxs-lookup"><span data-stu-id="56dd7-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="56dd7-105">Další informace najdete v tématu [reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="56dd7-105">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="56dd7-106">Atributy mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="56dd7-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="56dd7-107">Atributy přidat metadata do programu.</span><span class="sxs-lookup"><span data-stu-id="56dd7-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="56dd7-108">*Metadata* je informace o typech definované v programu.</span><span class="sxs-lookup"><span data-stu-id="56dd7-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="56dd7-109">Všechny sestavení .NET obsahovat zadanou sadu metadata, která popisuje typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="56dd7-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="56dd7-110">Můžete přidat vlastní atributy pro žádné další informace, které jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="56dd7-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="56dd7-111">Další informace najdete v tématu, [vytváření vlastní atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="56dd7-111">For more information, see, [Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="56dd7-112">Celý sestavení, moduly nebo menší program prvky, jako jsou například třídy a vlastnosti, můžete použít jeden nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="56dd7-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="56dd7-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="56dd7-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="56dd7-114">Váš program můžete zkontrolovat svůj vlastní metadata nebo metadata v ostatních aplikacích pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="56dd7-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="56dd7-115">Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="56dd7-115">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="56dd7-116">Pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="56dd7-116">Using Attributes</span></span>  
 <span data-ttu-id="56dd7-117">Atributy je možné použít u libovolného deklarace, když konkrétní atribut může omezit přístup k deklarace, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="56dd7-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="56dd7-118">V jazyce C# můžete určit atribut umístěním název atributu, uzavřeny do hranatých závorek ([]), nad deklaraci entity, které se.</span><span class="sxs-lookup"><span data-stu-id="56dd7-118">In C#, you specify an attribute by placing the name of the attribute, enclosed in square brackets ([]), above the declaration of the entity to which it applies.</span></span>  
  
 <span data-ttu-id="56dd7-119">V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování zvláštní vlastností pro třídu:</span><span class="sxs-lookup"><span data-stu-id="56dd7-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 <span data-ttu-id="56dd7-120">Metody s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován takto:</span><span class="sxs-lookup"><span data-stu-id="56dd7-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 <span data-ttu-id="56dd7-121">Více než jeden atribut je možné použít u deklaraci:</span><span class="sxs-lookup"><span data-stu-id="56dd7-121">More than one attribute can be placed on a declaration:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 <span data-ttu-id="56dd7-122">Některé atributy lze zadat více než jednou pro danou entitu.</span><span class="sxs-lookup"><span data-stu-id="56dd7-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="56dd7-123">Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="56dd7-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="56dd7-124">Podle konvence ukončete všechny názvy atributů slovem "Atribut" jej odlišit od jiných položek v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56dd7-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="56dd7-125">Však není potřeba zadejte příponu atribut při použití atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="56dd7-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="56dd7-126">Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56dd7-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="56dd7-127">Atribut parametry</span><span class="sxs-lookup"><span data-stu-id="56dd7-127">Attribute Parameters</span></span>  
 <span data-ttu-id="56dd7-128">Počet atributů mít parametry, které může být poziční, nepojmenovaný nebo s názvem.</span><span class="sxs-lookup"><span data-stu-id="56dd7-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="56dd7-129">Žádné poziční parametry musí být zadaný v určitém pořadí a nelze jej vynechat; pojmenované parametry jsou volitelné a lze jej zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="56dd7-129">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="56dd7-130">Nejprve jsou zadány poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="56dd7-130">Positional parameters are specified first.</span></span> <span data-ttu-id="56dd7-131">Například odpovídají tyto tři atributy:</span><span class="sxs-lookup"><span data-stu-id="56dd7-131">For example, these three attributes are equivalent:</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 <span data-ttu-id="56dd7-132">První parametr název DLL je poziční a dodává se vždy první; ostatní s názvem.</span><span class="sxs-lookup"><span data-stu-id="56dd7-132">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="56dd7-133">V takovém případě i s názvem výchozí parametry na hodnotu false, můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="56dd7-133">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="56dd7-134">Vyhledejte jednotlivé atributy dokumentaci informace o výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="56dd7-134">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="56dd7-135">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="56dd7-135">Attribute Targets</span></span>  
 <span data-ttu-id="56dd7-136">*Cíl* atributu je ta entita, na které se vztahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="56dd7-136">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="56dd7-137">Atribut může například použít třídu, konkrétní metody nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="56dd7-137">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="56dd7-138">Ve výchozím nastavení atribut vztahuje k elementu, který ho předchází.</span><span class="sxs-lookup"><span data-stu-id="56dd7-138">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="56dd7-139">Ale můžete také explicitně identifikovat, například zda atribut se použije na metodu, nebo její parametr nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="56dd7-139">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="56dd7-140">K identifikaci explicitně atribut target, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="56dd7-140">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```csharp  
[target : attribute-list]  
```  
  
 <span data-ttu-id="56dd7-141">Seznam možných `target` hodnoty je uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="56dd7-141">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="56dd7-142">Hodnota cíle</span><span class="sxs-lookup"><span data-stu-id="56dd7-142">Target value</span></span>|<span data-ttu-id="56dd7-143">Platí pro</span><span class="sxs-lookup"><span data-stu-id="56dd7-143">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="56dd7-144">Celý sestavení</span><span class="sxs-lookup"><span data-stu-id="56dd7-144">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="56dd7-145">Aktuální modul sestavení</span><span class="sxs-lookup"><span data-stu-id="56dd7-145">Current assembly module</span></span>|  
|`field`|<span data-ttu-id="56dd7-146">Pole ve třídě nebo struktury</span><span class="sxs-lookup"><span data-stu-id="56dd7-146">Field in a class or a struct</span></span>|  
|`event`|<span data-ttu-id="56dd7-147">Událost</span><span class="sxs-lookup"><span data-stu-id="56dd7-147">Event</span></span>|  
|`method`|<span data-ttu-id="56dd7-148">Metoda nebo `get` a `set` vlastnost přístupové objekty</span><span class="sxs-lookup"><span data-stu-id="56dd7-148">Method or `get` and `set` property accessors</span></span>|  
|`param`|<span data-ttu-id="56dd7-149">Parametry metody nebo `set` parametry přistupující objekt vlastnosti</span><span class="sxs-lookup"><span data-stu-id="56dd7-149">Method parameters or `set` property accessor parameters</span></span>|  
|`property`|<span data-ttu-id="56dd7-150">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="56dd7-150">Property</span></span>|  
|`return`|<span data-ttu-id="56dd7-151">Návratová hodnota metody, vlastnosti indexer nebo `get` přistupující objekt vlastnosti</span><span class="sxs-lookup"><span data-stu-id="56dd7-151">Return value of a method, property indexer, or `get` property accessor</span></span>|  
|`type`|<span data-ttu-id="56dd7-152">Struktura, třídu, rozhraní, výčet nebo delegáta</span><span class="sxs-lookup"><span data-stu-id="56dd7-152">Struct, class, interface, enum, or delegate</span></span>|  
  
 <span data-ttu-id="56dd7-153">Následující příklad ukazuje, jak chcete použít atributy pro sestavení a moduly.</span><span class="sxs-lookup"><span data-stu-id="56dd7-153">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="56dd7-154">Další informace najdete v tématu [běžné atributy (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="56dd7-154">For more information, see [Common Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 <span data-ttu-id="56dd7-155">Následující příklad ukazuje, jak se má použít k metodám, metoda parametry, atributy a metoda návratové hodnoty v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="56dd7-155">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  <span data-ttu-id="56dd7-156">Bez ohledu na to cíle, na kterém `SomeAttr` je definován jako platný, `return` cíl musí být zadaný, i když `SomeAttr` byly definovány se provádí pouze návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="56dd7-156">Regardless of the targets on which `SomeAttr` is defined to be valid, the `return` target has to be specified, even if `SomeAttr` were defined to apply only to return values.</span></span> <span data-ttu-id="56dd7-157">Jinými slovy, nebude používat kompilátor `AttributeUsage` informace týkající se řešení cíle nejednoznačný atributů.</span><span class="sxs-lookup"><span data-stu-id="56dd7-157">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="56dd7-158">Další informace najdete v tématu [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="56dd7-158">For more information, see [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span></span>  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="56dd7-159">Běžná použití atributů</span><span class="sxs-lookup"><span data-stu-id="56dd7-159">Common Uses for Attributes</span></span>  
 <span data-ttu-id="56dd7-160">Následující seznam obsahuje několik příkladů běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="56dd7-160">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="56dd7-161">Označení metody pomocí `WebMethod` atribut v webové služby k označení, že metoda by měla být s přes protokol SOAP.</span><span class="sxs-lookup"><span data-stu-id="56dd7-161">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="56dd7-162">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="56dd7-162">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="56dd7-163">Popisující, jak při vzájemné spolupráci s nativním kódem zařazování parametry metody.</span><span class="sxs-lookup"><span data-stu-id="56dd7-163">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="56dd7-164">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="56dd7-164">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="56dd7-165">Popisující COM vlastnosti tříd, metod a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56dd7-165">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="56dd7-166">Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="56dd7-166">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="56dd7-167">Která popisují vaše sestavení z hlediska název, verze, popis nebo ochranná známka.</span><span class="sxs-lookup"><span data-stu-id="56dd7-167">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="56dd7-168">Popisující, kteří členové třídy k serializaci trvalosti.</span><span class="sxs-lookup"><span data-stu-id="56dd7-168">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="56dd7-169">Popisující, jak pro mapování mezi členy třídy a z uzlů XML pro serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="56dd7-169">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="56dd7-170">Popisuje požadavky na zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="56dd7-170">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="56dd7-171">Zadání vlastnosti slouží k vynucení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="56dd7-171">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="56dd7-172">Řízení optimalizace kompilátorem v běhu (JIT), takže stále snadno ladit kód.</span><span class="sxs-lookup"><span data-stu-id="56dd7-172">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="56dd7-173">Získání informací o volajícího, aby metoda.</span><span class="sxs-lookup"><span data-stu-id="56dd7-173">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56dd7-174">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="56dd7-174">Related Sections</span></span>  
 <span data-ttu-id="56dd7-175">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="56dd7-175">For more information, see:</span></span>  
  
-   [<span data-ttu-id="56dd7-176">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-176">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="56dd7-177">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-177">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="56dd7-178">Postupy: vytváření sjednocení C/C++ pomocí atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-178">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="56dd7-179">Mezi běžné atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-179">Common Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="56dd7-180">Informace o subjektu volajícím (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-180">Caller Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="56dd7-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="56dd7-181">See Also</span></span>  
 [<span data-ttu-id="56dd7-182">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="56dd7-182">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56dd7-183">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="56dd7-183">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="56dd7-184">Atributy</span><span class="sxs-lookup"><span data-stu-id="56dd7-184">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)
