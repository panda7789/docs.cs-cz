---
title: Odkazy na deklarované elementy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 0fca02ab2dcb507c1129f18f31a25c7809fc9710
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296703"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="1263f-102">Odkazy na deklarované elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1263f-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="1263f-103">Pokud váš kód odkazuje na element deklarovaný, kompilátor jazyka Visual Basic odpovídá názvu v referenci na příslušné prohlášení s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="1263f-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="1263f-104">Pokud je teď deklarována více než jeden element se stejným názvem, můžete určit, které z těchto elementů je odkazovat *oprávněným* jeho název.</span><span class="sxs-lookup"><span data-stu-id="1263f-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="1263f-105">Kompilátor se pokusí porovnat název odkazu na deklarace názvu s *od nejužšího oboru po*.</span><span class="sxs-lookup"><span data-stu-id="1263f-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="1263f-106">To znamená, že začne s kódem odkazu a funguje směrem ven. prostřednictvím po sobě jdoucích úrovně obsahující prvky.</span><span class="sxs-lookup"><span data-stu-id="1263f-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="1263f-107">Následující příklad ukazuje, odkazy na dvě proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="1263f-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="1263f-108">Příklad deklaruje dvě proměnné, každý s názvem `totalCount`, na různých úrovních oboru v modulu `container`.</span><span class="sxs-lookup"><span data-stu-id="1263f-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="1263f-109">Když postup `showCount` zobrazí `totalCount` bez kvalifikace, kompilátor jazyka Visual Basic přeloží odkaz na prohlášení s zpomalit, a to místní deklarace uvnitř `showCount`.</span><span class="sxs-lookup"><span data-stu-id="1263f-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="1263f-110">Když kvalifikuje `totalCount` s modulem obsahující `container`, přeloží kompilátor odkaz na prohlášení s širším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="1263f-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
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
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="1263f-111">Název elementu kvalifikace</span><span class="sxs-lookup"><span data-stu-id="1263f-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="1263f-112">Pokud chcete tento proces hledání a zadejte název deklarovaný v širším rozsahem je nutné *kvalifikovat* k názvu obsahující element širším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="1263f-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="1263f-113">V některých případech budete také muset kvalifikovat nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="1263f-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="1263f-114">Kvalifikováním názvu prostředky před ve vámi zdroje s informacemi, které určuje, kde je definován cílový element.</span><span class="sxs-lookup"><span data-stu-id="1263f-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="1263f-115">Tyto informace se volá *kvalifikace řetězec*.</span><span class="sxs-lookup"><span data-stu-id="1263f-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="1263f-116">Může obsahovat jednu nebo více oborů názvů a modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1263f-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="1263f-117">Řetězec kvalifikace musí jednoznačně určovat modulu, třídy nebo struktury obsahující cílového prvku.</span><span class="sxs-lookup"><span data-stu-id="1263f-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="1263f-118">Kontejner může zase nacházet v jiné nadřazeného elementu, obvykle obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1263f-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="1263f-119">Možná budete muset obsahují několik obsahující prvky v řetězci kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="1263f-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="1263f-120">Pro přístup k element deklarovaný kvalifikováním názvu</span><span class="sxs-lookup"><span data-stu-id="1263f-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="1263f-121">Určení umístění, ve kterém je definována elementu.</span><span class="sxs-lookup"><span data-stu-id="1263f-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="1263f-122">To může zahrnovat obor názvů nebo dokonce hierarchie oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="1263f-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="1263f-123">V rámci oboru názvů nejnižší úrovně elementu musí být součástí modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1263f-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
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
  
2. <span data-ttu-id="1263f-124">Určení kvalifikace cestu na základě umístění cílového prvku.</span><span class="sxs-lookup"><span data-stu-id="1263f-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="1263f-125">Začněte s nejvyšší úrovně oboru názvů, přejít k nejnižší úrovni oboru názvů a končit modulu, třídy nebo struktury obsahující cílového prvku.</span><span class="sxs-lookup"><span data-stu-id="1263f-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="1263f-126">Každý prvek v cestě musí obsahovat element, která ji následuje.</span><span class="sxs-lookup"><span data-stu-id="1263f-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="1263f-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="1263f-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="1263f-128">Řetězec kvalifikace Příprava cílového prvku.</span><span class="sxs-lookup"><span data-stu-id="1263f-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="1263f-129">Umístit tečku (`.`) po každý prvek v cestě.</span><span class="sxs-lookup"><span data-stu-id="1263f-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="1263f-130">Aplikace musí mít přístup na každý prvek v řetězci vaše kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="1263f-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="1263f-131">Zápis výrazu nebo příkazu přiřazení odkazující na cílový element běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="1263f-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="1263f-132">Zadejte před název elementu target řetězcem kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="1263f-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="1263f-133">Název by měl bezprostředně následuje po období (`.`) modulu, třídy nebo struktury, který obsahuje element, který následuje.</span><span class="sxs-lookup"><span data-stu-id="1263f-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="1263f-134">Kompilátor používá k nalezení jednoznačnou, kompletní vymazat deklarace, na který může porovnat odkaz na element target řetězec kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="1263f-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="1263f-135">Budete také muset kvalifikovat název odkazu, pokud má vaše aplikace přístup k více než jeden programový element, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="1263f-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="1263f-136">Například <xref:System.Windows.Forms> a <xref:System.Web.UI.WebControls> obory názvů oba obsahují `Label` třídy (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> a <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="1263f-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1263f-137">Pokud vaše aplikace používá obě nebo pokud jej definuje vlastní `Label` třídy, musí rozlišovat mezi různými `Label` objekty.</span><span class="sxs-lookup"><span data-stu-id="1263f-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="1263f-138">Alias oboru názvů nebo import zahrňte v deklaraci proměnné.</span><span class="sxs-lookup"><span data-stu-id="1263f-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="1263f-139">Alias importu v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1263f-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="1263f-140">Další prvky obsahující členy</span><span class="sxs-lookup"><span data-stu-id="1263f-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="1263f-141">Při použití nesdílené členem jiné třídy nebo struktury, musí nejdřív kvalifikovat název člena proměnné nebo výraz, který odkazuje na instanci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1263f-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="1263f-142">V následujícím příkladu `demoClass` je instance třídy s názvem `class1`.</span><span class="sxs-lookup"><span data-stu-id="1263f-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="1263f-143">Samotný název třídy nelze použít k vyfiltrování člena, který není [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="1263f-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="1263f-144">Musíte nejprve vytvořit instanci v proměnné objektu (v tomto případě `demoClass`) a pak na něj odkazovat podle názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="1263f-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="1263f-145">Pokud má třída nebo struktura `Shared` člen, se můžete kvalifikovat tento člen s názvem třídy nebo struktury nebo proměnné nebo výraz, který odkazuje na instanci.</span><span class="sxs-lookup"><span data-stu-id="1263f-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="1263f-146">Modul nemá žádné samostatných instancí služby, a všechny její členy jsou `Shared` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1263f-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="1263f-147">Proto kvalifikovat člen modul s názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="1263f-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="1263f-148">Následující příklad ukazuje kvalifikované odkazy na postupy člen modulu.</span><span class="sxs-lookup"><span data-stu-id="1263f-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="1263f-149">Příklad deklaruje dvě `Sub` postupy, oba s názvem `perform`, v různých modulů v projektu.</span><span class="sxs-lookup"><span data-stu-id="1263f-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="1263f-150">Každý z nich mohou být zadány bez kvalifikace v rámci své vlastní modul však musí být kvalifikovaný, pokud na něj odkazovat z jakéhokoliv jiného místa.</span><span class="sxs-lookup"><span data-stu-id="1263f-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="1263f-151">Vzhledem k tomu, že poslední odkaz v `module3` nesplňuje `perform`, kompilátor nemůže vyřešit tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="1263f-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
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
  
## <a name="references-to-projects"></a><span data-ttu-id="1263f-152">Odkazy na projekty</span><span class="sxs-lookup"><span data-stu-id="1263f-152">References to Projects</span></span>  
 <span data-ttu-id="1263f-153">Použití [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) prvky definované v jiném projektu, musíte nejprve nastavit *odkaz* pro tento projekt sestavení nebo typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="1263f-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="1263f-154">Nastavit odkaz, klikněte na tlačítko **přidat odkaz** na **projektu** nabídky, nebo použijte [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1263f-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="1263f-155">Například můžete použít objektový model XML [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1263f-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1263f-156">Pokud nastavíte na odkaz <xref:System.Xml> obor názvů, můžete deklarovat a použít některou z jeho třídy, jako například <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="1263f-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="1263f-157">Následující příklad používá <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="1263f-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="1263f-158">Import, který obsahuje prvky</span><span class="sxs-lookup"><span data-stu-id="1263f-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="1263f-159">Můžete použít [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k *importovat* obory názvů, které obsahují moduly nebo třídy, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1263f-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="1263f-160">To umožňuje odkazovat na prvky definované v importované oboru názvů bez plně kvalifikovaného jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="1263f-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="1263f-161">Následující příklad přepíše předchozí příklad import <xref:System.Xml> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1263f-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="1263f-162">Kromě toho `Imports` příkazu můžete definovat *importovat alias* pro jednotlivé importované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="1263f-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="1263f-163">Díky tomu se zdrojový kód kratší a snadněji čitelné.</span><span class="sxs-lookup"><span data-stu-id="1263f-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="1263f-164">Následující příklad přepíše předchozí příklad použití `xD` jako alias pro <xref:System.Xml> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1263f-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="1263f-165">`Imports` Příkaz neprovede elementy z jiných projektů k dispozici pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1263f-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="1263f-166">To znamená ho nepřijímá místo nastavení odkaz.</span><span class="sxs-lookup"><span data-stu-id="1263f-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="1263f-167">Import oboru názvů jenom eliminuje nutnost kvalifikovat názvy definované v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1263f-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="1263f-168">Můžete také použít `Imports` smlouvu pro import modulů, třídy, struktury a výčty.</span><span class="sxs-lookup"><span data-stu-id="1263f-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="1263f-169">Potom můžete členy z těchto prvků importované bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="1263f-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="1263f-170">Musíte však vždy kvalifikovat nesdílené členy třídy a struktury s proměnné nebo výraz, který na instance dané třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1263f-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="1263f-171">Pokyny k pojmenování</span><span class="sxs-lookup"><span data-stu-id="1263f-171">Naming Guidelines</span></span>  
 <span data-ttu-id="1263f-172">Při definování nejmíň dva programovací prvky, které mají stejný název, *název nejednoznačnost* může dojít, pokud se kompilátor pokusí přeložit odkaz na tento název.</span><span class="sxs-lookup"><span data-stu-id="1263f-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="1263f-173">Pokud více než jednu definici je v oboru nebo pokud se žádná definice není v oboru, odkaz je nevyřešitelná.</span><span class="sxs-lookup"><span data-stu-id="1263f-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="1263f-174">Příklad naleznete v části "Příklad kvalifikovaný odkaz" na tuto stránku nápovědy.</span><span class="sxs-lookup"><span data-stu-id="1263f-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="1263f-175">Mnohoznačnosti názvů můžete vyhnout tím, že všechny prvky jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="1263f-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="1263f-176">Potom můžete vytvořit odkaz na libovolný element bez nutnosti kvalifikovat stejný název jako obor názvů, modulu nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="1263f-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="1263f-177">Také snížit riziko omylem odkazující na chybný element.</span><span class="sxs-lookup"><span data-stu-id="1263f-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="1263f-178">Stínování</span><span class="sxs-lookup"><span data-stu-id="1263f-178">Shadowing</span></span>  
 <span data-ttu-id="1263f-179">Když dva programovací prvky sdílí se stejným názvem, jeden z nich můžete skrýt, nebo *stínové*, druhou.</span><span class="sxs-lookup"><span data-stu-id="1263f-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="1263f-180">Stínovaný prvek není k dispozici pro referenci; Místo toho pokud váš kód používá název stínovaný elementu, kompilátor jazyka Visual Basic to je řešeno do elementu stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="1263f-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="1263f-181">Podrobnější vysvětlení s příklady najdete v tématu [stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="1263f-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1263f-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1263f-182">See also</span></span>

- [<span data-ttu-id="1263f-183">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="1263f-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="1263f-184">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="1263f-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="1263f-185">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1263f-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="1263f-186">Proměnné</span><span class="sxs-lookup"><span data-stu-id="1263f-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="1263f-187">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="1263f-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="1263f-188">Operátor New</span><span class="sxs-lookup"><span data-stu-id="1263f-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="1263f-189">Public</span><span class="sxs-lookup"><span data-stu-id="1263f-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
