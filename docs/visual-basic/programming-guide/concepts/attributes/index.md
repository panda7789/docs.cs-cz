---
title: "Přehled atributy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b78eb3e5ac52ec89e810fde682249c689ba304a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="0ce73-102">Přehled atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="0ce73-103">Atributy poskytují výkonný metoda spojování metadata nebo deklarativní informace s kódem (sestavení, typy, metody, vlastnosti a tak dále).</span><span class="sxs-lookup"><span data-stu-id="0ce73-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="0ce73-104">Po atribut je spojen s entitou program, může být dotazován atribut v době běhu pomocí techniky názvem *reflexe*.</span><span class="sxs-lookup"><span data-stu-id="0ce73-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="0ce73-105">Další informace najdete v tématu [reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0ce73-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="0ce73-106">Atributy mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0ce73-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="0ce73-107">Atributy přidat metadata do programu.</span><span class="sxs-lookup"><span data-stu-id="0ce73-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="0ce73-108">*Metadata* je informace o typech definované v programu.</span><span class="sxs-lookup"><span data-stu-id="0ce73-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="0ce73-109">Všechny sestavení .NET obsahovat zadanou sadu metadata, která popisuje typy a členy typu definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ce73-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="0ce73-110">Můžete přidat vlastní atributy pro žádné další informace, které jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="0ce73-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="0ce73-111">Další informace najdete v tématu, [vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0ce73-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="0ce73-112">Celý sestavení, moduly nebo menší program prvky, jako jsou například třídy a vlastnosti, můžete použít jeden nebo více atributů.</span><span class="sxs-lookup"><span data-stu-id="0ce73-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="0ce73-113">Atributy mohou přijímat argumenty stejným způsobem jako metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0ce73-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="0ce73-114">Váš program můžete zkontrolovat svůj vlastní metadata nebo metadata v ostatních aplikacích pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="0ce73-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="0ce73-115">Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0ce73-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="0ce73-116">Pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="0ce73-116">Using Attributes</span></span>  
 <span data-ttu-id="0ce73-117">Atributy je možné použít u libovolného deklarace, když konkrétní atribut může omezit přístup k deklarace, na kterých je platný.</span><span class="sxs-lookup"><span data-stu-id="0ce73-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="0ce73-118">V jazyce Visual Basic je atribut uzavřené v lomených závorkách (\< >).</span><span class="sxs-lookup"><span data-stu-id="0ce73-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="0ce73-119">Musí být uvedena bezprostředně před element, ke které se použije, na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="0ce73-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="0ce73-120">V tomto příkladu <xref:System.SerializableAttribute> atribut se používá k aplikování zvláštní vlastností pro třídu:</span><span class="sxs-lookup"><span data-stu-id="0ce73-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="0ce73-121">Metody s atributem <xref:System.Runtime.InteropServices.DllImportAttribute> je deklarován takto:</span><span class="sxs-lookup"><span data-stu-id="0ce73-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="0ce73-122">Více než jeden atribut je možné použít u deklaraci:</span><span class="sxs-lookup"><span data-stu-id="0ce73-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="0ce73-123">Některé atributy lze zadat více než jednou pro danou entitu.</span><span class="sxs-lookup"><span data-stu-id="0ce73-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="0ce73-124">Je například multiuse atribut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="0ce73-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="0ce73-125">Podle konvence ukončete všechny názvy atributů slovem "Atribut" jej odlišit od jiných položek v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ce73-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="0ce73-126">Však není potřeba zadejte příponu atribut při použití atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="0ce73-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="0ce73-127">Například `[DllImport]` je ekvivalentní `[DllImportAttribute]`, ale `DllImportAttribute` je skutečný název atributu v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ce73-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="0ce73-128">Atribut parametry</span><span class="sxs-lookup"><span data-stu-id="0ce73-128">Attribute Parameters</span></span>  
 <span data-ttu-id="0ce73-129">Počet atributů mít parametry, které může být poziční, nepojmenovaný nebo s názvem.</span><span class="sxs-lookup"><span data-stu-id="0ce73-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="0ce73-130">Žádné poziční parametry musí být zadaný v určitém pořadí a nelze jej vynechat; pojmenované parametry jsou volitelné a lze jej zadat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0ce73-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="0ce73-131">Nejprve jsou zadány poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="0ce73-131">Positional parameters are specified first.</span></span> <span data-ttu-id="0ce73-132">Například odpovídají tyto tři atributy:</span><span class="sxs-lookup"><span data-stu-id="0ce73-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="0ce73-133">První parametr název DLL je poziční a dodává se vždy první; ostatní s názvem.</span><span class="sxs-lookup"><span data-stu-id="0ce73-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="0ce73-134">V takovém případě i s názvem výchozí parametry na hodnotu false, můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="0ce73-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="0ce73-135">Vyhledejte jednotlivé atributy dokumentaci informace o výchozí hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="0ce73-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="0ce73-136">Cíle atributů</span><span class="sxs-lookup"><span data-stu-id="0ce73-136">Attribute Targets</span></span>  
 <span data-ttu-id="0ce73-137">*Cíl* atributu je ta entita, na které se vztahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="0ce73-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="0ce73-138">Atribut může například použít třídu, konkrétní metody nebo celé sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ce73-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="0ce73-139">Ve výchozím nastavení atribut vztahuje k elementu, který ho předchází.</span><span class="sxs-lookup"><span data-stu-id="0ce73-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="0ce73-140">Ale můžete také explicitně identifikovat, například zda atribut se použije na metodu, nebo její parametr nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0ce73-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="0ce73-141">K identifikaci explicitně atribut target, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="0ce73-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="0ce73-142">Seznam možných `target` hodnoty je uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0ce73-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="0ce73-143">Hodnota cíle</span><span class="sxs-lookup"><span data-stu-id="0ce73-143">Target value</span></span>|<span data-ttu-id="0ce73-144">Platí pro</span><span class="sxs-lookup"><span data-stu-id="0ce73-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="0ce73-145">Celý sestavení</span><span class="sxs-lookup"><span data-stu-id="0ce73-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="0ce73-146">Aktuální modul sestavení (který se liší od modulu jazyka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="0ce73-147">Následující příklad ukazuje, jak chcete použít atributy pro sestavení a moduly.</span><span class="sxs-lookup"><span data-stu-id="0ce73-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="0ce73-148">Další informace najdete v tématu [běžné atributy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0ce73-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="0ce73-149">Běžná použití atributů</span><span class="sxs-lookup"><span data-stu-id="0ce73-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="0ce73-150">Následující seznam obsahuje několik příkladů běžných použití atributů v kódu:</span><span class="sxs-lookup"><span data-stu-id="0ce73-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="0ce73-151">Označení metody pomocí `WebMethod` atribut v webové služby k označení, že metoda by měla být s přes protokol SOAP.</span><span class="sxs-lookup"><span data-stu-id="0ce73-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="0ce73-152">Další informace naleznete v tématu <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0ce73-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="0ce73-153">Popisující, jak při vzájemné spolupráci s nativním kódem zařazování parametry metody.</span><span class="sxs-lookup"><span data-stu-id="0ce73-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="0ce73-154">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0ce73-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="0ce73-155">Popisující COM vlastnosti tříd, metod a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ce73-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="0ce73-156">Volání nespravovaného kódu pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="0ce73-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="0ce73-157">Která popisují vaše sestavení z hlediska název, verze, popis nebo ochranná známka.</span><span class="sxs-lookup"><span data-stu-id="0ce73-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="0ce73-158">Popisující, kteří členové třídy k serializaci trvalosti.</span><span class="sxs-lookup"><span data-stu-id="0ce73-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="0ce73-159">Popisující, jak pro mapování mezi členy třídy a z uzlů XML pro serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="0ce73-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="0ce73-160">Popisuje požadavky na zabezpečení pro metody.</span><span class="sxs-lookup"><span data-stu-id="0ce73-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="0ce73-161">Zadání vlastnosti slouží k vynucení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0ce73-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="0ce73-162">Řízení optimalizace kompilátorem v běhu (JIT), takže stále snadno ladit kód.</span><span class="sxs-lookup"><span data-stu-id="0ce73-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="0ce73-163">Získání informací o volajícího, aby metoda.</span><span class="sxs-lookup"><span data-stu-id="0ce73-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0ce73-164">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0ce73-164">Related Sections</span></span>  
 <span data-ttu-id="0ce73-165">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="0ce73-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0ce73-166">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="0ce73-167">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="0ce73-168">Postupy: vytváření sjednocení C/C++ pomocí atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="0ce73-169">Mezi běžné atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="0ce73-170">Informace o subjektu volajícím (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="0ce73-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ce73-171">See Also</span></span>  
 [<span data-ttu-id="0ce73-172">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ce73-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="0ce73-173">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ce73-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="0ce73-174">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ce73-174">Attributes</span></span>](../../../../standard/attributes/index.md)
