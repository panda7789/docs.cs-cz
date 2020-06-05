---
title: Odkazy na deklarované elementy
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 23bff2eb098982f67ecb1b709e59096d5259a644
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405180"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="2135c-102">Odkazy na deklarované elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2135c-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="2135c-103">Když váš kód odkazuje na deklarovaný element, kompilátor Visual Basic odpovídá názvu ve vašem odkazu na příslušnou deklaraci daného názvu.</span><span class="sxs-lookup"><span data-stu-id="2135c-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="2135c-104">Pokud je deklarován více než jeden prvek se stejným názvem, můžete určit, na které prvky mají být odkazovány, pomocí *zařazení* jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="2135c-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="2135c-105">Kompilátor se pokusí vyhledat odkaz na název deklarace názvu s *nejužším oborem*.</span><span class="sxs-lookup"><span data-stu-id="2135c-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="2135c-106">To znamená, že začíná kódem, který vytváří odkaz a pracuje směrem nahoru až po sobě jdoucí úrovně obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="2135c-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="2135c-107">Následující příklad ukazuje odkazy na dvě proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="2135c-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="2135c-108">Příklad deklaruje dvě proměnné, každý s názvem `totalCount` , na různých úrovních oboru v modulu `container` .</span><span class="sxs-lookup"><span data-stu-id="2135c-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="2135c-109">Pokud se procedura `showCount` zobrazí `totalCount` bez kvalifikace, kompilátor Visual Basic vyřeší odkaz na deklaraci s nejužším rozsahem, konkrétně v rámci místní deklarace `showCount` .</span><span class="sxs-lookup"><span data-stu-id="2135c-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="2135c-110">Pokud se `totalCount` s obsahem obsaženým modulem přiřadí `container` , kompilátor přeloží odkaz na deklaraci s širším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="2135c-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="2135c-111">Kvalifikování názvu elementu</span><span class="sxs-lookup"><span data-stu-id="2135c-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="2135c-112">Pokud chcete tento proces hledání přepsat a zadat název deklarovaný v širším rozsahu, je nutné *kvalifikovat* název obsahující element širšího rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2135c-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="2135c-113">V některých případech může být také nutné kvalifikovat nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="2135c-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="2135c-114">Kvalifikování názvu znamená před ním ve zdrojovém příkazu informace, které identifikují, kde je cílový element definován.</span><span class="sxs-lookup"><span data-stu-id="2135c-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="2135c-115">Tyto informace se nazývají *kvalifikační řetězec*.</span><span class="sxs-lookup"><span data-stu-id="2135c-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="2135c-116">Může zahrnovat jeden nebo více oborů názvů a modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="2135c-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="2135c-117">Řetězec kvalifikace by měl jednoznačně určovat modul, třídu nebo strukturu obsahující cílový element.</span><span class="sxs-lookup"><span data-stu-id="2135c-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="2135c-118">Kontejner může být zase umístěný v jiném obsahujícím elementu, obvykle obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2135c-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="2135c-119">Je možné, že budete muset zahrnout několik obsahující prvky do řetězce kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="2135c-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="2135c-120">Přístup k deklarovanému elementu pomocí kvalifikování jeho názvu</span><span class="sxs-lookup"><span data-stu-id="2135c-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="2135c-121">Určete umístění, ve kterém byl prvek definován.</span><span class="sxs-lookup"><span data-stu-id="2135c-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="2135c-122">To může zahrnovat obor názvů nebo dokonce i hierarchii oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="2135c-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="2135c-123">V rámci oboru názvů nejnižší úrovně musí být element obsažen v modulu, třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="2135c-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. <span data-ttu-id="2135c-124">Určete cestu kvalifikace na základě umístění cílového elementu.</span><span class="sxs-lookup"><span data-stu-id="2135c-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="2135c-125">Začněte s oborem názvů nejvyšší úrovně, přejděte k oboru názvů nejnižší úrovně a ukončete modul, třídu nebo strukturu obsahující cílový element.</span><span class="sxs-lookup"><span data-stu-id="2135c-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="2135c-126">Každý prvek v cestě musí obsahovat element, který následuje za ním.</span><span class="sxs-lookup"><span data-stu-id="2135c-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="2135c-127">`outerSpace`→ `innerSpace` → → `holdsTotals``totals`</span><span class="sxs-lookup"><span data-stu-id="2135c-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="2135c-128">Připravte řetězec kvalifikace pro cílový element.</span><span class="sxs-lookup"><span data-stu-id="2135c-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="2135c-129">Umístěte tečku ( `.` ) za každý prvek v cestě.</span><span class="sxs-lookup"><span data-stu-id="2135c-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="2135c-130">Vaše aplikace musí mít přístup ke každému prvku v řetězci kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="2135c-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="2135c-131">Napište výraz nebo příkaz přiřazení odkazující na cílový element v normálním způsobu.</span><span class="sxs-lookup"><span data-stu-id="2135c-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="2135c-132">Před název cílového elementu uveďte řetězec kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="2135c-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="2135c-133">Název by měl následovat za tečkou ( `.` ), která následuje za modulem, třídou nebo strukturou, která obsahuje element.</span><span class="sxs-lookup"><span data-stu-id="2135c-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="2135c-134">Kompilátor používá řetězec kvalifikace k nalezení jasné, jednoznačné deklarace, ke které se může shodovat s odkazem na cílový element.</span><span class="sxs-lookup"><span data-stu-id="2135c-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="2135c-135">Může být také nutné kvalifikovat odkaz na název, pokud má aplikace přístup k více než jednomu programovacímu prvku, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="2135c-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="2135c-136">Například <xref:System.Windows.Forms> <xref:System.Web.UI.WebControls> obory názvů a obsahují `Label` třídu ( <xref:System.Windows.Forms.Label?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="2135c-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="2135c-137">Pokud vaše aplikace používá obojí nebo pokud definuje svou vlastní `Label` třídu, je nutné odlišit různé `Label` objekty.</span><span class="sxs-lookup"><span data-stu-id="2135c-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="2135c-138">V deklaraci proměnné zahrňte obor názvů nebo alias importu.</span><span class="sxs-lookup"><span data-stu-id="2135c-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="2135c-139">V následujícím příkladu je použit alias importu.</span><span class="sxs-lookup"><span data-stu-id="2135c-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="2135c-140">Členové ostatních obsahující prvky</span><span class="sxs-lookup"><span data-stu-id="2135c-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="2135c-141">Použijete-li nesdíleného člena jiné třídy nebo struktury, musíte nejprve kvalifikovat název člena pomocí proměnné nebo výrazu, který odkazuje na instanci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="2135c-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="2135c-142">V následujícím příkladu `demoClass` je instance třídy s názvem `class1` .</span><span class="sxs-lookup"><span data-stu-id="2135c-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="2135c-143">Samotný název třídy nelze použít k získání člena, který není [sdílen](../../../language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="2135c-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="2135c-144">Musíte nejdřív vytvořit instanci v objektové proměnné (v tomto případě `demoClass` ) a pak na ni odkazovat pomocí názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="2135c-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="2135c-145">Pokud třída nebo struktura má `Shared` člena, můžete kvalifikovat tento člen buď s názvem třídy nebo struktury, nebo s proměnnou nebo výrazem, který odkazuje na instanci.</span><span class="sxs-lookup"><span data-stu-id="2135c-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="2135c-146">Modul nemá žádné samostatné instance a všechny jeho členy jsou `Shared` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2135c-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="2135c-147">Proto jste kvalifikováni člena modulu s názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="2135c-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="2135c-148">Následující příklad ukazuje kvalifikované odkazy na členské procedury modulu.</span><span class="sxs-lookup"><span data-stu-id="2135c-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="2135c-149">Příklad deklaruje dva `Sub` postupy, oba pojmenované `perform` , v různých modulech v projektu.</span><span class="sxs-lookup"><span data-stu-id="2135c-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="2135c-150">Každý z nich je možné zadat bez kvalifikace v rámci vlastního modulu, ale musí být kvalifikován, pokud je odkazován z libovolného místa jinde.</span><span class="sxs-lookup"><span data-stu-id="2135c-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="2135c-151">Vzhledem k tomu, že cílový odkaz v `module3` není kvalifikován `perform` , kompilátor nemůže tento odkaz vyřešit.</span><span class="sxs-lookup"><span data-stu-id="2135c-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="2135c-152">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="2135c-152">References to Projects</span></span>  
 <span data-ttu-id="2135c-153">Chcete-li použít [veřejné](../../../language-reference/modifiers/public.md) prvky definované v jiném projektu, je nutné nejprve nastavit *odkaz* na sestavení projektu nebo knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="2135c-153">To use [Public](../../../language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="2135c-154">Chcete-li nastavit odkaz, klikněte na tlačítko **Přidat odkaz** v nabídce **projekt** nebo použijte možnost kompilátoru [-Reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2135c-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="2135c-155">Například můžete použít objektový model XML .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2135c-155">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="2135c-156">Pokud nastavíte odkaz na <xref:System.Xml> obor názvů, můžete deklarovat a použít kteroukoli z jeho tříd, jako je například <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2135c-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="2135c-157">Následující příklad používá <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="2135c-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="2135c-158">Import obsahující prvky</span><span class="sxs-lookup"><span data-stu-id="2135c-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="2135c-159">Můžete použít [příkaz Imports (obor názvů a typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) k *importu* oborů názvů, které obsahují moduly nebo třídy, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="2135c-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="2135c-160">Díky tomu můžete odkazovat na prvky definované v importovaném oboru názvů, aniž byste museli plně kvalifikovat jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="2135c-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="2135c-161">Následující příklad přepíše předchozí příklad pro import <xref:System.Xml> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2135c-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="2135c-162">Kromě toho `Imports` může příkaz definovat *alias importu* pro každý importovaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2135c-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="2135c-163">To může mít za krátkou a snazší čtení zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="2135c-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="2135c-164">Následující příklad přepíše předchozí příklad, který se použije `xD` jako alias pro <xref:System.Xml> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2135c-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="2135c-165">`Imports`Příkaz nezpřístupňuje prvky z jiných projektů, které jsou k dispozici pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2135c-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="2135c-166">To znamená, že nevezme místo nastavení odkaz.</span><span class="sxs-lookup"><span data-stu-id="2135c-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="2135c-167">Import oboru názvů pouhým odebráním požadavku vyřadíte názvy definované v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2135c-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="2135c-168">Pomocí příkazu můžete také `Imports` importovat moduly, třídy, struktury a výčty.</span><span class="sxs-lookup"><span data-stu-id="2135c-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="2135c-169">Pak můžete použít členy takových importovaných prvků bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="2135c-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="2135c-170">Je však nutné vždy kvalifikovat nesdílené členy tříd a struktur s proměnnou nebo výrazem, který je vyhodnocen jako instance třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="2135c-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="2135c-171">Pokyny k pojmenování</span><span class="sxs-lookup"><span data-stu-id="2135c-171">Naming Guidelines</span></span>  
 <span data-ttu-id="2135c-172">Pokud definujete dva nebo více programovacích prvků, které mají stejný název, může dojít k *nejednoznačnosti názvu* , pokud se kompilátor pokusí přeložit odkaz na tento název.</span><span class="sxs-lookup"><span data-stu-id="2135c-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="2135c-173">Pokud je v oboru více než jedna definice nebo pokud není v oboru žádná definice, je odkaz nevyřešitelná.</span><span class="sxs-lookup"><span data-stu-id="2135c-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="2135c-174">Příklad naleznete v části "kvalifikovaný referenční příklad" na této stránce s nápovědu.</span><span class="sxs-lookup"><span data-stu-id="2135c-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="2135c-175">Nejednoznačnosti názvů můžete zabránit tím, že všem vašim prvkům udělíte jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="2135c-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="2135c-176">Pak můžete vytvořit odkaz na libovolný prvek bez nutnosti kvalifikovat jeho název pomocí oboru názvů, modulu nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="2135c-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="2135c-177">Také snížíte pravděpodobnost nechtěného odkazování na nesprávný prvek.</span><span class="sxs-lookup"><span data-stu-id="2135c-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="2135c-178">Stínování</span><span class="sxs-lookup"><span data-stu-id="2135c-178">Shadowing</span></span>  
 <span data-ttu-id="2135c-179">Pokud dva programovací prvky mají stejný název, jeden z nich může skrýt nebo *stín*, druhý.</span><span class="sxs-lookup"><span data-stu-id="2135c-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="2135c-180">Stínovaný element není pro referenci k dispozici. místo toho, když kód používá stínovaný název elementu, kompilátor Visual Basic ho přeloží na stínový element.</span><span class="sxs-lookup"><span data-stu-id="2135c-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="2135c-181">Podrobnější vysvětlení s příklady najdete v tématu [vytváření stínových kopií v Visual Basic](shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="2135c-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2135c-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="2135c-182">See also</span></span>

- [<span data-ttu-id="2135c-183">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="2135c-183">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="2135c-184">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="2135c-184">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="2135c-185">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="2135c-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="2135c-186">Proměnné</span><span class="sxs-lookup"><span data-stu-id="2135c-186">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="2135c-187">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="2135c-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="2135c-188">New – operátor</span><span class="sxs-lookup"><span data-stu-id="2135c-188">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="2135c-189">Republik</span><span class="sxs-lookup"><span data-stu-id="2135c-189">Public</span></span>](../../../language-reference/modifiers/public.md)
