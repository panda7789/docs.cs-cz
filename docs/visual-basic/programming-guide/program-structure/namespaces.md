---
title: Obory názvů
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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400671"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="46def-102">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46def-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="46def-103">Obory názvů uspořádají objekty definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="46def-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="46def-104">Sestavení mohou obsahovat více oborů názvů, které mohou zase obsahovat další obory názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="46def-105">Obory názvů zabraňují nejednoznačnosti a zjednodušují odkazy při použití velkých skupin objektů, jako jsou knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="46def-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="46def-106">Například rozhraní .NET Framework <xref:System.Windows.Forms.ListBox> definuje třídu v oboru <xref:System.Windows.Forms?displayProperty=nameWithType> názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="46def-107">Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaného názvu pro tuto třídu:</span><span class="sxs-lookup"><span data-stu-id="46def-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="46def-108">Předcházení kolizím názvů</span><span class="sxs-lookup"><span data-stu-id="46def-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="46def-109">Obory názvů rozhraní .NET Framework řeší problém, který se někdy nazývá *znečištění oboru názvů*, ve kterém je vývojáři knihovny tříd bráněno použitím podobných názvů v jiné knihovně.</span><span class="sxs-lookup"><span data-stu-id="46def-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="46def-110">Tyto konflikty s existujícími součástmi se někdy nazývají *kolize názvů*.</span><span class="sxs-lookup"><span data-stu-id="46def-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="46def-111">Pokud například vytvoříte novou `ListBox`třídu s názvem , můžete ji použít v rámci projektu bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="46def-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="46def-112">Pokud však chcete použít třídu <xref:System.Windows.Forms.ListBox> rozhraní .NET Framework ve stejném projektu, musíte použít plně kvalifikovaný odkaz, aby byl odkaz jedinečný.</span><span class="sxs-lookup"><span data-stu-id="46def-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="46def-113">Pokud odkaz není jedinečný, visual basic vytvoří chybu oznamující, že název je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="46def-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="46def-114">Následující příklad kódu ukazuje, jak deklarovat tyto objekty:</span><span class="sxs-lookup"><span data-stu-id="46def-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="46def-115">Následující obrázek znázorňuje dvě hierarchie oboru `ListBox`názvů, obě obsahující objekt s názvem :</span><span class="sxs-lookup"><span data-stu-id="46def-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje dvě hierarchie oboru názvů.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="46def-117">Ve výchozím nastavení obsahuje každý spustitelný soubor, který vytvoříte pomocí jazyka Visual Basic, obor názvů se stejným názvem jako projekt.</span><span class="sxs-lookup"><span data-stu-id="46def-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="46def-118">Pokud například definujete objekt v `ListBoxProject`rámci projektu s názvem , obsahuje spustitelný soubor `ListBoxProject`ListBoxProject.exe název obor názvů s názvem .</span><span class="sxs-lookup"><span data-stu-id="46def-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="46def-119">Více sestavení můžete použít stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="46def-120">Visual Basic s nimi zachází jako s jednou sadou názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="46def-121">Můžete například definovat třídy pro `SomeNameSpace` obor názvů `Assemb1`volaný v sestavení s názvem a `Assemb2`definovat další třídy pro stejný obor názvů z sestavení s názvem .</span><span class="sxs-lookup"><span data-stu-id="46def-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="46def-122">Plně kvalifikovaná jména</span><span class="sxs-lookup"><span data-stu-id="46def-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="46def-123">Plně kvalifikované názvy jsou odkazy na objekty, které jsou předponou s názvem oboru názvů, ve kterém je objekt definován.</span><span class="sxs-lookup"><span data-stu-id="46def-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="46def-124">Objekty definované v jiných projektech můžete použít, pokud vytvoříte odkaz na třídu (výběrem **možnosti Přidat odkaz** z nabídky **Projekt)** a potom použijete plně kvalifikovaný název objektu v kódu.</span><span class="sxs-lookup"><span data-stu-id="46def-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="46def-125">Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název pro objekt z oboru názvů jiného projektu:</span><span class="sxs-lookup"><span data-stu-id="46def-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="46def-126">Plně kvalifikované názvy zabránit konfliktům názvů, protože umožňují kompilátoru určit, který objekt se používá.</span><span class="sxs-lookup"><span data-stu-id="46def-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="46def-127">Nicméně, jména samotná mohou být dlouhá a těžkopádná.</span><span class="sxs-lookup"><span data-stu-id="46def-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="46def-128">Chcete-li tento problém obejít, můžete pomocí příkazu `Imports` definovat *alias*– zkrácený název, který můžete použít místo plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="46def-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="46def-129">Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a používá tyto aliasy k definování dvou objektů.</span><span class="sxs-lookup"><span data-stu-id="46def-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="46def-130">Pokud použijete `Imports` příkaz bez aliasu, můžete použít všechny názvy v tomto oboru názvů bez kvalifikace za předpokladu, že jsou jedinečné pro projekt.</span><span class="sxs-lookup"><span data-stu-id="46def-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="46def-131">Pokud váš `Imports` projekt obsahuje příkazy pro obory názvů, které obsahují položky se stejným názvem, je nutné plně kvalifikovat tento název při jeho použití.</span><span class="sxs-lookup"><span data-stu-id="46def-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="46def-132">Předpokládejme například, že projekt obsahuje `Imports` následující dva příkazy:</span><span class="sxs-lookup"><span data-stu-id="46def-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="46def-133">Pokud se pokusíte použít `Class1` bez úplného zařazení, Visual Basic `Class1` vytvoří chybu oznamující, že název je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="46def-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="46def-134">Příkazy úrovně oboru názvů</span><span class="sxs-lookup"><span data-stu-id="46def-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="46def-135">V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegáty, výčty, struktury a další obory názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="46def-136">Nelze definovat položky, jako jsou vlastnosti, procedury, proměnné a události na úrovni oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="46def-137">Tyto položky musí být deklarovány v rámci kontejnerů, jako jsou moduly, struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="46def-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="46def-138">Globální klíčové slovo v plně kvalifikovaných názvech</span><span class="sxs-lookup"><span data-stu-id="46def-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="46def-139">Pokud jste definovali vnořenou hierarchii oborů názvů, může <xref:System?displayProperty=nameWithType> být kód uvnitř této hierarchie blokován v přístupu k oboru názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46def-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="46def-140">Následující příklad ilustruje hierarchii, `SpecialSpace.System` ve které obor <xref:System?displayProperty=nameWithType>názvů blokuje přístup k aplikaci .</span><span class="sxs-lookup"><span data-stu-id="46def-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="46def-141">V důsledku toho kompilátor jazyka visual basic <xref:System.Int32?displayProperty=nameWithType>nemůže `SpecialSpace.System` úspěšně přeložit `Int32`odkaz na , protože nedefinuje .</span><span class="sxs-lookup"><span data-stu-id="46def-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="46def-142">`Global` Klíčové slovo můžete použít ke spuštění řetězce kvalifikace na nejkrajnější úrovni knihovny tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46def-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="46def-143">To umožňuje zadat <xref:System?displayProperty=nameWithType> obor názvů nebo jiný obor názvů v knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="46def-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="46def-144">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="46def-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="46def-145">Můžete použít `Global` pro přístup k jiným oborům <xref:Microsoft.VisualBasic?displayProperty=nameWithType>názvů kořenové úrovně, jako je například aplikace , a ke všem oborům názvů přidruženým k projektu.</span><span class="sxs-lookup"><span data-stu-id="46def-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="46def-146">Globální klíčové slovo v příkazech oboru názvů</span><span class="sxs-lookup"><span data-stu-id="46def-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="46def-147">Klíčové `Global` slovo můžete také použít v [prohlášení oboru názvů](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="46def-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="46def-148">To umožňuje definovat obor názvů z kořenového oboru názvů projektu.</span><span class="sxs-lookup"><span data-stu-id="46def-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="46def-149">Všechny obory názvů v projektu jsou založeny na kořenovém oboru názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="46def-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="46def-150">Visual Studio přiřadí název projektu jako výchozí kořenový obor názvů pro veškerý kód v projektu.</span><span class="sxs-lookup"><span data-stu-id="46def-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="46def-151">Pokud je například projekt `ConsoleApplication1`pojmenován , jeho programovací prvky patří do oboru názvů `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="46def-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="46def-152">Pokud deklarujete `Namespace Magnetosphere`, odkazy `Magnetosphere` v projektu budou mít přístup `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="46def-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="46def-153">Následující příklady používají `Global` klíčové slovo k deklarování oboru názvů mimo kořenový obor názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="46def-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="46def-154">V deklaraci `Global` oboru názvů nelze vnořit do jiného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="46def-155">Můžete použít [stránku aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) k zobrazení a úpravě **kořenového oboru názvů** projektu.</span><span class="sxs-lookup"><span data-stu-id="46def-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="46def-156">U nových projektů je výchozí výchozí **obor kořenového názvového serveru** název projektu.</span><span class="sxs-lookup"><span data-stu-id="46def-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="46def-157">Chcete-li způsobit, `Global` že se jedná o obor názvů nejvyšší úrovně, můžete vymazat položku **Kořenového oboru názvů,** aby bylo pole prázdné.</span><span class="sxs-lookup"><span data-stu-id="46def-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="46def-158">**Vymazáním kořenového oboru** názvů `Global` odeberete potřebu klíčového slova v deklaracích oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="46def-159">Pokud `Namespace` příkaz deklaruje název, který je také obor názvů v rozhraní .NET `Global` Framework, obor názvů rozhraní .NET Framework přestane být k dispozici, pokud klíčové slovo není použito v plně kvalifikovaném názvu.</span><span class="sxs-lookup"><span data-stu-id="46def-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="46def-160">Chcete-li povolit přístup k tomuto `Global` oboru názvů rozhraní `Global` .NET `Namespace` Framework bez použití klíčového slova, můžete klíčové slovo zahrnout do příkazu.</span><span class="sxs-lookup"><span data-stu-id="46def-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="46def-161">Následující příklad má `Global` klíčové `System.Text` slovo v deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46def-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="46def-162">Pokud `Global` klíčové slovo nebylo přítomno v <xref:System.Text.StringBuilder> deklaraci oboru názvů, `Global.System.Text.StringBuilder`nebylo možné získat přístup bez zadání .</span><span class="sxs-lookup"><span data-stu-id="46def-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="46def-163">Pro projekt `ConsoleApplication1`s názvem `System.Text` , `ConsoleApplication1.System.Text` odkazy `Global` na přístup, pokud klíčové slovo nebylo použito.</span><span class="sxs-lookup"><span data-stu-id="46def-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="46def-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="46def-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="46def-165">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="46def-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="46def-166">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="46def-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="46def-167">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="46def-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="46def-168">Psaní kódu v řešeních pro systém Office</span><span class="sxs-lookup"><span data-stu-id="46def-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
