---
title: Přehled atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: c799b9be9b936beadde28374bd9882ebc6e2d9a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966322"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="7d1ae-102">Přehled atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="7d1ae-103">Atributy poskytují výkonnou metodu přidružování metadat nebo deklarativní informace, s kódem (sestavení, typy, metodami, vlastnostmi a tak dále).</span><span class="sxs-lookup"><span data-stu-id="7d1ae-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="7d1ae-104">Po přiřazení atributu k entitě programu lze pomocí metody s názvem reflexe zadat dotaz na atribut v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="7d1ae-105">Další informace naleznete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="7d1ae-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="7d1ae-106">Atributy mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-106">Attributes have the following properties:</span></span>  
  
- <span data-ttu-id="7d1ae-107">Atributy přidávají do programu metadata.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="7d1ae-108">*Metadata* jsou informace o typech definovaných v programu.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="7d1ae-109">Všechna sestavení .NET obsahují zadanou sadu metadat, které popisují typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="7d1ae-110">Můžete přidat vlastní atributy a zadat případné další požadované informace.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="7d1ae-111">Další informace najdete v tématu [Vytvoření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7d1ae-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
- <span data-ttu-id="7d1ae-112">Jeden nebo více atributů lze použít pro celá sestavení, moduly nebo menší prvky programu, jako jsou třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
- <span data-ttu-id="7d1ae-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
- <span data-ttu-id="7d1ae-114">Váš program může prošetřit vlastní metadata nebo metadata v jiných programech pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="7d1ae-115">Další informace naleznete v tématu [přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="7d1ae-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="7d1ae-116">Používání atributů</span><span class="sxs-lookup"><span data-stu-id="7d1ae-116">Using Attributes</span></span>  
 <span data-ttu-id="7d1ae-117">Atributy lze umístit na většinu jakékoli deklarace, i když konkrétní atribut může omezit typy deklarací, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="7d1ae-118">V Visual Basic je atribut uzavřený v lomených závorkách\< (>).</span><span class="sxs-lookup"><span data-stu-id="7d1ae-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="7d1ae-119">Musí se objevit bezprostředně před prvkem, na který je použit, na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="7d1ae-120">V tomto příkladu <xref:System.SerializableAttribute> je atribut použit k použití konkrétní charakteristiky pro třídu:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="7d1ae-121">Metoda s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarována takto:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="7d1ae-122">V deklaraci lze umístit více než jeden atribut:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="7d1ae-123">Některé atributy lze pro danou entitu zadat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="7d1ae-124">Příklad takového atributu Multiuse je <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
> <span data-ttu-id="7d1ae-125">Podle konvence názvy všech atributů končí slovem "Attribute", aby je bylo možné odlišit od ostatních položek v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="7d1ae-126">Při použití atributů v kódu však není nutné zadávat příponu atributu.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="7d1ae-127">Například `[DllImport]` je ekvivalentní k `[DllImportAttribute]`, ale `DllImportAttribute` je skutečným názvem atributu v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="7d1ae-128">Parametry atributu</span><span class="sxs-lookup"><span data-stu-id="7d1ae-128">Attribute Parameters</span></span>  
 <span data-ttu-id="7d1ae-129">Mnoho atributů má parametry, které mohou být pozice, nepojmenované nebo pojmenované.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="7d1ae-130">V určitém pořadí musí být zadány všechny poziční parametry a nelze je vynechat; pojmenované parametry jsou volitelné a lze je zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="7d1ae-131">Poziční parametry jsou uvedeny jako první.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-131">Positional parameters are specified first.</span></span> <span data-ttu-id="7d1ae-132">Například tyto tři atributy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="7d1ae-133">První parametr, název knihovny DLL, je pozice a vždy se nachází jako první; ostatní mají název.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="7d1ae-134">V takovém případě mají obě pojmenované parametry výchozí hodnotu false, takže je lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="7d1ae-135">Informace o výchozích hodnotách parametrů naleznete v dokumentaci k jednotlivým atributům.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="7d1ae-136">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="7d1ae-136">Attribute Targets</span></span>  
 <span data-ttu-id="7d1ae-137">*Cíl* atributu je entita, na kterou se atribut vztahuje.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="7d1ae-138">Atribut může například platit pro třídu, konkrétní metodu nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="7d1ae-139">Ve výchozím nastavení se atribut vztahuje na element, který předchází.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="7d1ae-140">Můžete ale také explicitně určit, zda je atribut použit na metodu, nebo na jeho parametr nebo na jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="7d1ae-141">K explicitní identifikaci cíle atributu použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="7d1ae-142">Seznam možných `target` hodnot je uveden v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="7d1ae-143">Cílová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d1ae-143">Target value</span></span>|<span data-ttu-id="7d1ae-144">Platí pro</span><span class="sxs-lookup"><span data-stu-id="7d1ae-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="7d1ae-145">Celé sestavení</span><span class="sxs-lookup"><span data-stu-id="7d1ae-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="7d1ae-146">Aktuální modul sestavení (který se liší od modulu Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="7d1ae-147">Následující příklad ukazuje, jak použít atributy na sestavení a moduly.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="7d1ae-148">Další informace najdete v tématu [běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7d1ae-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="7d1ae-149">Běžné použití atributů</span><span class="sxs-lookup"><span data-stu-id="7d1ae-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="7d1ae-150">Následující seznam obsahuje několik běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
- <span data-ttu-id="7d1ae-151">Označení metod pomocí `WebMethod` atributu ve webových službách k označení toho, že by měla být metoda volat přes protokol SOAP.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="7d1ae-152">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
- <span data-ttu-id="7d1ae-153">Popisuje způsob zařazení parametrů metody při spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="7d1ae-154">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
- <span data-ttu-id="7d1ae-155">Popisuje vlastnosti modelu COM pro třídy, metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
- <span data-ttu-id="7d1ae-156">Volání nespravovaného kódu <xref:System.Runtime.InteropServices.DllImportAttribute> pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
- <span data-ttu-id="7d1ae-157">Popisuje vaše sestavení s ohledem na název, verzi, popis nebo ochrannou známku.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
- <span data-ttu-id="7d1ae-158">Popisuje, kteří členové třídy mají být serializováni k trvalému serializaci.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-158">Describing which members of a class to serialize for persistence.</span></span>  
  
- <span data-ttu-id="7d1ae-159">Popisuje, jak mapovat mezi členy třídy a uzly XML pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
- <span data-ttu-id="7d1ae-160">Popisuje požadavky na zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-160">Describing the security requirements for methods.</span></span>  
  
- <span data-ttu-id="7d1ae-161">Určení vlastností používaných k vymáhání zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-161">Specifying characteristics used to enforce security.</span></span>  
  
- <span data-ttu-id="7d1ae-162">Řízení optimalizace pomocí kompilátoru JIT (just-in-time), takže kód zůstane snadno laděn.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
- <span data-ttu-id="7d1ae-163">Získání informací o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="7d1ae-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d1ae-164">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7d1ae-164">Related Sections</span></span>  
 <span data-ttu-id="7d1ae-165">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-165">For more information, see:</span></span>  
  
- [<span data-ttu-id="7d1ae-166">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [<span data-ttu-id="7d1ae-167">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [<span data-ttu-id="7d1ae-168">Postupy: Vytvoření C/C++ sjednocení pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [<span data-ttu-id="7d1ae-169">Společné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [<span data-ttu-id="7d1ae-170">Informace o volajícím (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d1ae-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d1ae-171">See also</span></span>

- [<span data-ttu-id="7d1ae-172">Průvodce programováním Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d1ae-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="7d1ae-173">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d1ae-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="7d1ae-174">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d1ae-174">Attributes</span></span>](../../../../standard/attributes/index.md)
