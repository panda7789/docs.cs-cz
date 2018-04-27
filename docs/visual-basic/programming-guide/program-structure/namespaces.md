---
title: Obory názvů v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ec038a17b4a6b10dbe339fe33969c4ade57e2a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="e34f0-102">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e34f0-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="e34f0-103">Obory názvů uspořádat objekty definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e34f0-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="e34f0-104">Sestavení může obsahovat více obory názvů, který zase mohou obsahovat jiných oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="e34f0-105">Obory názvů zabránilo nejednoznačnosti a zjednodušit odkazy, při použití velké skupiny objektů, například knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="e34f0-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="e34f0-106">Například [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definuje <xref:System.Windows.Forms.ListBox> třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-106">For example, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e34f0-107">Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaný název pro tuto třídu:</span><span class="sxs-lookup"><span data-stu-id="e34f0-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="e34f0-108">Zamezení kolize názvů</span><span class="sxs-lookup"><span data-stu-id="e34f0-108">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]<span data-ttu-id="e34f0-109"> obory názvů vyřešit problém se někdy označuje jako *znečištění oboru názvů*, ve které je na vývojáře knihovny tříd pomocí podobné názvy v jiné knihovny omezován.</span><span class="sxs-lookup"><span data-stu-id="e34f0-109"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="e34f0-110">Tyto je v konfliktu s existující součásti se někdy označuje jako *název kolizí*.</span><span class="sxs-lookup"><span data-stu-id="e34f0-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="e34f0-111">Například pokud vytvoříte novou třídu s názvem `ListBox`, můžete ji použít v projektu bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="e34f0-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="e34f0-112">Ale pokud chcete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> třídy ve stejném projektu, musíte použít plně kvalifikovaný odkaz aby jedinečný odkaz.</span><span class="sxs-lookup"><span data-stu-id="e34f0-112">However, if you want to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="e34f0-113">Pokud není jedinečný odkaz, vyvolá jazyka Visual Basic chyba oznamující, že název je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="e34f0-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="e34f0-114">Následující příklad kódu ukazuje, jak deklarovat tyto objekty:</span><span class="sxs-lookup"><span data-stu-id="e34f0-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 <span data-ttu-id="e34f0-115">Následující obrázek znázorňuje dvěma hierarchiemi obor názvů, jak obsahuje objekt s názvem `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="e34f0-116">![Namespace hierarchie](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="e34f0-116">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="e34f0-117">Ve výchozím nastavení obsahuje každý spustitelný soubor, který vytvoříte v jazyce Visual Basic obor názvů se stejným názvem jako projektu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="e34f0-118">Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject`, spustitelný soubor ListBoxProject.exe obsahuje obor názvů s názvem `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="e34f0-119">Více sestavení můžete použít stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="e34f0-120">Visual Basic je považuje za jednu sadu názvy.</span><span class="sxs-lookup"><span data-stu-id="e34f0-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="e34f0-121">Například můžete definovat třídy pro obor názvů s názvem `SomeNameSpace` v sestavení s názvem `Assemb1`a definovat další třídy pro stejného oboru názvů ze sestavení s názvem `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="e34f0-122">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="e34f0-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="e34f0-123">Plně kvalifikované názvy jsou odkazy na objekty, které mají předponu název oboru názvů, ve kterém je definovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="e34f0-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="e34f0-124">Můžete použít objekty, které jsou definovány v jiné projekty, je-li vytvořit odkaz na třídu (výběrem **přidat odkaz na** z **projektu** nabídky) a pak použít plně kvalifikovaný název objektu v kódu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="e34f0-125">Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název pro objekt z jiného projektu názvů:</span><span class="sxs-lookup"><span data-stu-id="e34f0-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 <span data-ttu-id="e34f0-126">Plně kvalifikované názvy zabránit pojmenování konfliktu, protože možnost pro kompilátor k určení, který objekt je používán.</span><span class="sxs-lookup"><span data-stu-id="e34f0-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="e34f0-127">Názvy sami, můžete však získat dlouhé a komplikované.</span><span class="sxs-lookup"><span data-stu-id="e34f0-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="e34f0-128">Chcete-li se tomuto problému vyhnout, můžete použít `Imports` příkaz k definování *alias*– zkrácený název budete moct používat místo plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="e34f0-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="e34f0-129">Například následující příklad kódu vytvoří aliasy pro dvě plně kvalifikované názvy a používá tyto aliasy pro definování dva objekty.</span><span class="sxs-lookup"><span data-stu-id="e34f0-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 <span data-ttu-id="e34f0-130">Pokud použijete `Imports` příkaz bez alias, můžete použít všechny názvy v tom, že zadaný obor názvů bez kvalifikace, jsou jedinečné pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e34f0-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="e34f0-131">Pokud projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, musíte plně před tímto názvem pokud ji používáte.</span><span class="sxs-lookup"><span data-stu-id="e34f0-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="e34f0-132">Předpokládejme například projektu obsažena následující dva `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e34f0-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 <span data-ttu-id="e34f0-133">Pokud pokus o použití `Class1` bez plně kvalifikovaného, Visual Basic vytvoří chybu oznamující, že název `Class1` je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="e34f0-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="e34f0-134">Úroveň Namespace příkazy</span><span class="sxs-lookup"><span data-stu-id="e34f0-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="e34f0-135">V oboru názvů můžete definovat položek, jako jsou moduly, rozhraní, třídy, delegáti, struktury, výčty a jiných oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="e34f0-136">Nelze definovat položek, jako jsou vlastnosti, postupy, proměnné a události na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="e34f0-137">Tyto položky musí být deklarován v rámci kontejnery, jako jsou moduly, struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="e34f0-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="e34f0-138">Global – klíčové slovo ve plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="e34f0-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="e34f0-139">Pokud jsou definovány vnořené hierarchie oborů názvů, kód v této hierarchii mohou blokovat přístup k <xref:System?displayProperty=nameWithType> obor názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e34f0-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="e34f0-140">Následující příklad ilustruje hierarchie, ve kterém `SpecialSpace.System` obor názvů blokuje přístup k <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e34f0-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="e34f0-141">V důsledku toho kompilátoru jazyka Visual Basic nelze úspěšně vyhodnotit odkaz na <xref:System.Int32?displayProperty=nameWithType>, protože `SpecialSpace.System` nedefinuje `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="e34f0-142">Můžete použít `Global` – klíčové slovo zahájíte řetězu kvalifikace na úrovni nejkrajnější knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e34f0-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="e34f0-143">Umožňuje zadat <xref:System?displayProperty=nameWithType> oboru názvů nebo jiný obor názvů v knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="e34f0-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="e34f0-144">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e34f0-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="e34f0-145">Můžete použít `Global` do jiných oborech názvů kořenové úrovně přístupu, jako například <xref:Microsoft.VisualBasic?displayProperty=nameWithType>a obor názvů přidružené k projektu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="e34f0-146">Global – klíčové slovo v příkazech Namespace</span><span class="sxs-lookup"><span data-stu-id="e34f0-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="e34f0-147">Můžete také `Global` – klíčové slovo v [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e34f0-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="e34f0-148">To umožňuje definovat oboru názvů z kořenového oboru názvů vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="e34f0-149">Všechny obory názvů v projektu jsou založené na kořenového oboru názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e34f0-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="e34f0-150">Visual Studio přiřadí název projektu jako výchozí kořenový obor názvů pro všechny kódu v projektu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="e34f0-151">Například pokud je název projektu `ConsoleApplication1`, jeho programovací elementy patří do oboru názvů `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="e34f0-152">Pokud je deklarovat `Namespace Magnetosphere`, odkazuje na `Magnetosphere` v projektu budou přistupovat k `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="e34f0-153">Následující příklady použití `Global` – klíčové slovo k deklaraci oboru názvů z kořenového oboru názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e34f0-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 <span data-ttu-id="e34f0-154">V deklaraci oboru názvů `Global` nelze vnořit v jiném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="e34f0-155">Můžete použít [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) zobrazovat a upravovat **kořenové Namespace** projektu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="e34f0-156">Pro nové projekty **kořenové Namespace** výchozí hodnota je název projektu.</span><span class="sxs-lookup"><span data-stu-id="e34f0-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="e34f0-157">Způsobí `Global` na nejvyšší úrovni oboru názvů, můžete vymazat **kořenové Namespace** položky tak, aby pole je prázdné.</span><span class="sxs-lookup"><span data-stu-id="e34f0-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="e34f0-158">Vymazání **kořenové Namespace** odebírá potřebu, `Global` – klíčové slovo v deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="e34f0-159">Pokud `Namespace` příkaz deklaruje název, který je taky obor názvů v rozhraní .NET Framework, obor názvů rozhraní .NET Framework nedostupný. Pokud `Global` – klíčové slovo není používáno ve plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="e34f0-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="e34f0-160">Pro povolení přístupu do daného oboru názvů rozhraní .NET Framework bez použití `Global` – klíčové slovo, můžete zahrnout `Global` – klíčové slovo v `Namespace` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e34f0-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="e34f0-161">V následujícím příkladu má `Global` – klíčové slovo v `System.Text` deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e34f0-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="e34f0-162">Pokud `Global` – klíčové slovo nebylo v deklaraci oboru názvů <xref:System.Text.StringBuilder> nelze získat přístup bez zadání `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e34f0-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="e34f0-163">Pro projekt s názvem `ConsoleApplication1`, odkazuje na `System.Text` by přístup `ConsoleApplication1.System.Text` Pokud `Global` – klíčové slovo nebyl použit.</span><span class="sxs-lookup"><span data-stu-id="e34f0-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e34f0-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="e34f0-164">See Also</span></span>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [<span data-ttu-id="e34f0-165">Sestavení a globální mezipaměť sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="e34f0-165">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="e34f0-166">Postupy: Vytváření a použití sestavení s pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e34f0-166">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="e34f0-167">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="e34f0-167">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="e34f0-168">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="e34f0-168">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="e34f0-169">Psaní kódu v řešeních pro systém Office</span><span class="sxs-lookup"><span data-stu-id="e34f0-169">Writing Code in Office Solutions</span></span>](https://msdn.microsoft.com/library/bb608596)
