---
title: Obory názvů v jazyce Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 6b320d21c33fa798ca2fd3ef5a04363d141f99f2
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367889"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="74987-102">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74987-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="74987-103">Obory názvů uspořádávají objekty definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="74987-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="74987-104">Sestavení může obsahovat více oborů názvů, který pak může obsahovat další obory názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="74987-105">Obory názvů zabránilo nejednoznačnosti a při použití velké skupiny objektů, jako je například knihovny tříd zjednodušení odkazy.</span><span class="sxs-lookup"><span data-stu-id="74987-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="74987-106">Například [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definuje <xref:System.Windows.Forms.ListBox> třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-106">For example, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="74987-107">Následující fragment kódu ukazuje, jak deklarovat pomocí plně kvalifikovaného názvu pro tuto třídu:</span><span class="sxs-lookup"><span data-stu-id="74987-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="74987-108">Předcházení kolizi názvů</span><span class="sxs-lookup"><span data-stu-id="74987-108">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]<span data-ttu-id="74987-109"> obory názvů řešení problému říká se jim \*znečištění oboru názvů\*, ve které vývojář knihovny tříd komplikují užívání podobnými názvy v jiné knihovny.</span><span class="sxs-lookup"><span data-stu-id="74987-109"> namespaces address a problem sometimes called \*namespace pollution\*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="74987-110">Tyto je v konfliktu s existující součásti jsou někdy označovány jako *byly kolize názvů*.</span><span class="sxs-lookup"><span data-stu-id="74987-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="74987-111">Například, pokud vytvoříte novou třídu s názvem `ListBox`, můžete ji použít uvnitř projektu bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="74987-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="74987-112">Nicméně pokud chcete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> třídy ve stejném projektu, musíte použít plně kvalifikovaný odkaz aby odkaz na jedinečný.</span><span class="sxs-lookup"><span data-stu-id="74987-112">However, if you want to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="74987-113">Pokud odkaz není jedinečný, Visual Basic vytvoří chybu s informacemi o tom, že název je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="74987-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="74987-114">Následující příklad kódu ukazuje, jak deklarovat tyto objekty:</span><span class="sxs-lookup"><span data-stu-id="74987-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 <span data-ttu-id="74987-115">Následující obrázek znázorňuje dvěma hierarchiemi obor názvů, obě obsahující objekt s názvem `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="74987-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="74987-116">![Hierarchie Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="74987-116">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="74987-117">Ve výchozím nastavení obsahuje každý spustitelného souboru, který vytvoříte pomocí jazyka Visual Basic obor názvů se stejným názvem jako váš projekt.</span><span class="sxs-lookup"><span data-stu-id="74987-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="74987-118">Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject`, obsahuje obor názvů s názvem spustitelného souboru ListBoxProject.exe `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="74987-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="74987-119">Více sestavení můžete použít stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="74987-120">Visual Basic je zpracovává jako jednu sadu názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="74987-121">Například můžete definovat třídy pro obor názvů s názvem `SomeNameSpace` v sestavení s názvem `Assemb1`a definovat další třídy pro stejný obor názvů ze sestavení s názvem `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="74987-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="74987-122">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="74987-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="74987-123">Plně kvalifikované názvy jsou odkazy na objekty, které mají předponu názvu oboru názvů, ve kterém je definována objektu.</span><span class="sxs-lookup"><span data-stu-id="74987-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="74987-124">Můžete použít objekty definované v jiných projektech, je-li vytvořit odkaz na třídu (výběrem **přidat odkaz** z **projektu** nabídky) a pak použít plně kvalifikovaný název pro objekt v kódu.</span><span class="sxs-lookup"><span data-stu-id="74987-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="74987-125">Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název pro objekt z oboru názvů jiného projektu:</span><span class="sxs-lookup"><span data-stu-id="74987-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 <span data-ttu-id="74987-126">Plně kvalifikované názvy zabránit pojmenování je v konfliktu vzhledem k tomu, že umožňují kompilátoru k určení, který objekt se používá.</span><span class="sxs-lookup"><span data-stu-id="74987-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="74987-127">Nicméně názvy samy můžete získat dlouhé a těžkopádný proces.</span><span class="sxs-lookup"><span data-stu-id="74987-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="74987-128">Chcete-li se tomuto problému vyhnout, můžete použít `Imports` příkaz k definování *alias*– zkrácený název použijete místo plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="74987-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="74987-129">Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a pomocí těchto aliasů definuje dva objekty.</span><span class="sxs-lookup"><span data-stu-id="74987-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 <span data-ttu-id="74987-130">Pokud používáte `Imports` příkaz bez alias, můžete použít všechny názvy v tom, že obor názvů bez kvalifikace, k dispozici jsou jedinečné pro projekt.</span><span class="sxs-lookup"><span data-stu-id="74987-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="74987-131">Pokud váš projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, plně musíte tento název použijete.</span><span class="sxs-lookup"><span data-stu-id="74987-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="74987-132">Předpokládejme například, váš projekt obsahoval následující dva `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="74987-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 <span data-ttu-id="74987-133">Pokud se pokusíte použít `Class1` bez plně kvalifikovaného, Visual Basic vygeneruje chybu oznamující, že název `Class1` je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="74987-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="74987-134">Příkazy Namespace úroveň</span><span class="sxs-lookup"><span data-stu-id="74987-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="74987-135">V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegátů, výčty, struktury a ostatní obory názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="74987-136">Nejde definovat položky, jako jsou vlastnosti, procedury, proměnné a události na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="74987-137">Tyto položky musí být deklarována v rámci kontejnery, jako jsou moduly, struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="74987-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="74987-138">Global – klíčové slovo v plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="74987-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="74987-139">Pokud jste definovali vnořené hierarchie oborů názvů, kód uvnitř této hierarchii mohou blokovat přístup k <xref:System?displayProperty=nameWithType> obor názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74987-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="74987-140">Následující příklad ukazuje hierarchie, ve kterém `SpecialSpace.System` obor názvů blokuje přístup k <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74987-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="74987-141">V důsledku toho kompilátor jazyka Visual Basic nelze úspěšně vyhodnotit odkaz na <xref:System.Int32?displayProperty=nameWithType>, protože `SpecialSpace.System` nedefinuje `Int32`.</span><span class="sxs-lookup"><span data-stu-id="74987-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="74987-142">Můžete použít `Global` – klíčové slovo spustit kvalifikace řetězce na vnější úrovni v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74987-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="74987-143">Díky tomu můžete určit <xref:System?displayProperty=nameWithType> oboru názvů nebo jiný obor názvů v knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="74987-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="74987-144">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="74987-144">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="74987-145">Můžete použít `Global` k jiných oborech názvů kořenové úrovně <xref:Microsoft.VisualBasic?displayProperty=nameWithType>a libovolný obor názvů související s projektem.</span><span class="sxs-lookup"><span data-stu-id="74987-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="74987-146">Global – klíčové slovo v příkazy Namespace</span><span class="sxs-lookup"><span data-stu-id="74987-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="74987-147">Můžete také použít `Global` – klíčové slovo v [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="74987-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="74987-148">Tímto způsobem můžete definovat obor názvů mimo kořenový obor názvů vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="74987-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="74987-149">Všechny obory názvů v projektu jsou založeny na kořenového oboru názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="74987-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="74987-150">Jako výchozí obor názvů root pro veškerý kód v projektu sady Visual Studio přiřadí název vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="74987-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="74987-151">Například, pokud je název vašeho projektu `ConsoleApplication1`, jeho programovací prvky patří do oboru názvů `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="74987-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="74987-152">Pokud deklarujete `Namespace Magnetosphere`, odkazy na `Magnetosphere` v projektu bude mít přístup k `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="74987-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="74987-153">Následující příklady používají `Global` – klíčové slovo k deklarování oboru názvů mimo kořenový obor názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="74987-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 <span data-ttu-id="74987-154">V deklaraci oboru názvů `Global` nemůže být vnořená v jiném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="74987-155">Můžete použít [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) zobrazovat a upravovat **kořenové Namespace** projektu.</span><span class="sxs-lookup"><span data-stu-id="74987-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="74987-156">Pro nové projekty **kořenové Namespace** výchozí hodnoty na název projektu.</span><span class="sxs-lookup"><span data-stu-id="74987-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="74987-157">Způsobí `Global` na nejvyšší úrovni oboru názvů, zrušte **kořenové Namespace** položky tak, že je pole prázdné.</span><span class="sxs-lookup"><span data-stu-id="74987-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="74987-158">Vymazání **kořenové Namespace** eliminuje potřebu `Global` – klíčové slovo v deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="74987-159">Pokud `Namespace` příkaz deklaruje název, který je taky obor názvů v rozhraní .NET Framework, obor názvů rozhraní .NET Framework přestane být k dispozici Pokud `Global` – klíčové slovo se nepoužívá v plně kvalifikovaném názvu.</span><span class="sxs-lookup"><span data-stu-id="74987-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="74987-160">Umožňuje přístup na tento obor názvů rozhraní .NET Framework bez použití `Global` – klíčové slovo, můžete zahrnout `Global` – klíčové slovo v `Namespace` příkazu.</span><span class="sxs-lookup"><span data-stu-id="74987-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="74987-161">V následujícím příkladu má `Global` – klíčové slovo v `System.Text` deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74987-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="74987-162">Pokud `Global` – klíčové slovo nebyl k dispozici v deklaraci oboru názvů <xref:System.Text.StringBuilder> nelze získat přístup bez zadání `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="74987-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="74987-163">Pro projekt s názvem `ConsoleApplication1`, odkazy na `System.Text` byste přistupovali k `ConsoleApplication1.System.Text` Pokud `Global` – klíčové slovo se nepoužil.</span><span class="sxs-lookup"><span data-stu-id="74987-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="74987-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74987-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>  
- <xref:System.Windows.Forms?displayProperty=nameWithType>  
- [<span data-ttu-id="74987-165">Sestavení a globální mezipaměť sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="74987-165">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="74987-166">Postupy: Vytváření a použití sestavení s pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="74987-166">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [<span data-ttu-id="74987-167">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="74987-167">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
- [<span data-ttu-id="74987-168">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="74987-168">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [<span data-ttu-id="74987-169">Psaní kódu v řešeních pro systém Office</span><span class="sxs-lookup"><span data-stu-id="74987-169">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
