---
title: Přehled atributů (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: 2ecc3fb0a3bf7365b6eec39e1c5086d99f2c5a19
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642458"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="895be-102">Přehled atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="895be-103">Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále).</span><span class="sxs-lookup"><span data-stu-id="895be-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="895be-104">Po atributu je spojen s entitou program, atribut může být dotázán za běhu pomocí techniky označované jako *reflexe*.</span><span class="sxs-lookup"><span data-stu-id="895be-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="895be-105">Další informace najdete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="895be-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="895be-106">Atributy mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="895be-106">Attributes have the following properties:</span></span>  
  
- <span data-ttu-id="895be-107">Atributy přidat metadata do programu.</span><span class="sxs-lookup"><span data-stu-id="895be-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="895be-108">*Metadata* obsahuje informace o typy definované v programu.</span><span class="sxs-lookup"><span data-stu-id="895be-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="895be-109">Všechna sestavení rozhraní .NET obsahují zadanou množinu metadata popisující typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="895be-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="895be-110">Můžete přidat vlastní atributy k jakékoli další informace, které je nutné zadat.</span><span class="sxs-lookup"><span data-stu-id="895be-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="895be-111">Další informace najdete v tématu, [vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="895be-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
- <span data-ttu-id="895be-112">Můžete použít jeden nebo více atributů na celé sestavení, moduly nebo menší prvky programu, jako například třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="895be-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
- <span data-ttu-id="895be-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="895be-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
- <span data-ttu-id="895be-114">Aplikace můžete zkontrolovat svou vlastní metadaty nebo metadaty v jiných aplikacích pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="895be-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="895be-115">Další informace najdete v tématu [přístup k atributy podle použití reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="895be-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="895be-116">Pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="895be-116">Using Attributes</span></span>  
 <span data-ttu-id="895be-117">Atributy je možné použít u libovolného deklarace, když konkrétního atributu můžete narazit na omezení typů deklarace, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="895be-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="895be-118">V jazyce Visual Basic je atribut uzavřen do lomených závorek (\< >).</span><span class="sxs-lookup"><span data-stu-id="895be-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="895be-119">Musí být bezprostředně před elementem, ke které se použije, na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="895be-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="895be-120">V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování konkrétní charakteristiku pro třídu:</span><span class="sxs-lookup"><span data-stu-id="895be-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="895be-121">Metodu s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="895be-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="895be-122">Více než jeden atribut je možné použít v deklaraci:</span><span class="sxs-lookup"><span data-stu-id="895be-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="895be-123">Některé atributy můžete zadat více než jednou pro danou entitu.</span><span class="sxs-lookup"><span data-stu-id="895be-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="895be-124">Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="895be-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="895be-125">Podle konvence končí všechny názvy atributů slovem "Atribut", abychom je odlišili od ostatních položek v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="895be-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="895be-126">Ale není potřeba zadat atribut přípon při použití atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="895be-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="895be-127">Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="895be-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="895be-128">Atribut parametrů</span><span class="sxs-lookup"><span data-stu-id="895be-128">Attribute Parameters</span></span>  
 <span data-ttu-id="895be-129">Mnoho atributů mít parametry, které mohou být poziční, nepojmenovaný nebo s názvem.</span><span class="sxs-lookup"><span data-stu-id="895be-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="895be-130">Žádné poziční parametry musí být zadán v určitém pořadí a nelze jej vynechat; pojmenované parametry jsou volitelné a dá se zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="895be-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="895be-131">Poziční parametry jsou zadán jako první.</span><span class="sxs-lookup"><span data-stu-id="895be-131">Positional parameters are specified first.</span></span> <span data-ttu-id="895be-132">Například tyto tři atributy jsou ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="895be-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="895be-133">První parametr, název knihovny DLL je poziční a dodává se vždycky první; ostatní jsou pojmenovány.</span><span class="sxs-lookup"><span data-stu-id="895be-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="895be-134">V takovém případě pojmenované výchozí parametry na hodnotu false, takže lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="895be-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="895be-135">V dokumentaci jednotlivých atributů informace o výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="895be-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="895be-136">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="895be-136">Attribute Targets</span></span>  
 <span data-ttu-id="895be-137">*Cílové* atributu je entita, ke kterému se vztahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="895be-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="895be-138">Atribut může například použít pro třídu, konkrétní metody nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="895be-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="895be-139">Ve výchozím nastavení atribut se vztahuje k elementu, který předchází.</span><span class="sxs-lookup"><span data-stu-id="895be-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="895be-140">Ale můžete také explicitně identifikovat, například zda atributu se použije k metodě, její parametr nebo na jeho návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="895be-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="895be-141">Cíl atributu explicitně identifikovat, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="895be-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="895be-142">Seznam možných `target` hodnot je uveden v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="895be-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="895be-143">Cílová hodnota</span><span class="sxs-lookup"><span data-stu-id="895be-143">Target value</span></span>|<span data-ttu-id="895be-144">Platí pro</span><span class="sxs-lookup"><span data-stu-id="895be-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="895be-145">Celé sestavení</span><span class="sxs-lookup"><span data-stu-id="895be-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="895be-146">Aktuální modul sestavení (která se liší od modulu jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="895be-147">Následující příklad ukazuje způsob použití atributů pro sestavení a modulů.</span><span class="sxs-lookup"><span data-stu-id="895be-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="895be-148">Další informace najdete v tématu [běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="895be-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="895be-149">Běžné použití atributů</span><span class="sxs-lookup"><span data-stu-id="895be-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="895be-150">Následující seznam obsahuje několik běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="895be-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
- <span data-ttu-id="895be-151">Označení metody pomocí `WebMethod` atribut ve webové služby k označení, že metoda mělo by být umožněno prostřednictvím protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="895be-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="895be-152">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="895be-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
- <span data-ttu-id="895be-153">Popis způsobu zařazení parametrů metody při vzájemné spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="895be-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="895be-154">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="895be-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
- <span data-ttu-id="895be-155">Popis vlastnosti modelu COM pro třídy, metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="895be-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
- <span data-ttu-id="895be-156">Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="895be-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
- <span data-ttu-id="895be-157">Popisující vaše sestavení z hlediska název, verze, popis nebo ochranná známka.</span><span class="sxs-lookup"><span data-stu-id="895be-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
- <span data-ttu-id="895be-158">Popisující, které členy třídy k serializaci trvalosti.</span><span class="sxs-lookup"><span data-stu-id="895be-158">Describing which members of a class to serialize for persistence.</span></span>  
  
- <span data-ttu-id="895be-159">Popisující způsob, jakým mapování mezi členy třídy a z uzlů XML pro serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="895be-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
- <span data-ttu-id="895be-160">Popisuje požadavky zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="895be-160">Describing the security requirements for methods.</span></span>  
  
- <span data-ttu-id="895be-161">Zadání vlastnosti používá k vynucení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="895be-161">Specifying characteristics used to enforce security.</span></span>  
  
- <span data-ttu-id="895be-162">Řízení optimalizace kompilátoru just-in-time (JIT), tak zůstane usnadňuje ladění kódu.</span><span class="sxs-lookup"><span data-stu-id="895be-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
- <span data-ttu-id="895be-163">Získání informací o volajícím metody.</span><span class="sxs-lookup"><span data-stu-id="895be-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="895be-164">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="895be-164">Related Sections</span></span>  
 <span data-ttu-id="895be-165">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="895be-165">For more information, see:</span></span>  
  
- [<span data-ttu-id="895be-166">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [<span data-ttu-id="895be-167">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [<span data-ttu-id="895be-168">Postupy: Vytváření sjednocení C/C++ pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [<span data-ttu-id="895be-169">Běžné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [<span data-ttu-id="895be-170">Informace o volajícím (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="895be-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="895be-171">See also</span></span>

- [<span data-ttu-id="895be-172">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="895be-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="895be-173">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="895be-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="895be-174">Atributy</span><span class="sxs-lookup"><span data-stu-id="895be-174">Attributes</span></span>](../../../../standard/attributes/index.md)
