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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347333"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="e95af-102">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e95af-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="e95af-103">Obory názvů organizují objekty definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e95af-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="e95af-104">Sestavení mohou obsahovat více oborů názvů, které mohou zase obsahovat jiné obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e95af-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="e95af-105">Obory názvů zabraňují nejednoznačnosti a zjednodušují odkazy při použití velkých skupin objektů, jako jsou knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="e95af-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="e95af-106">Například .NET Framework definuje třídu <xref:System.Windows.Forms.ListBox> v oboru názvů <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e95af-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e95af-107">Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaného názvu pro tuto třídu:</span><span class="sxs-lookup"><span data-stu-id="e95af-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="e95af-108">Zamezení kolizí názvů</span><span class="sxs-lookup"><span data-stu-id="e95af-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="e95af-109">.NET Framework obory názvů řeší problém, který se někdy nazývá *znečišťování oboru názvů*, ve kterém je vývojář knihovny tříd zabráněno použitím podobných názvů v jiné knihovně.</span><span class="sxs-lookup"><span data-stu-id="e95af-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="e95af-110">Konflikty se stávajícími součástmi jsou někdy označovány jako *kolize názvů*.</span><span class="sxs-lookup"><span data-stu-id="e95af-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="e95af-111">Například pokud vytvoříte novou třídu s názvem `ListBox`, můžete ji použít uvnitř projektu bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="e95af-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="e95af-112">Pokud však chcete použít třídu .NET Framework <xref:System.Windows.Forms.ListBox> ve stejném projektu, je nutné použít plně kvalifikovaný odkaz, který odkaz nastaví jako jedinečný.</span><span class="sxs-lookup"><span data-stu-id="e95af-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="e95af-113">Pokud odkaz není jedinečný, Visual Basic vytvoří chybu oznamující, že název je nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="e95af-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="e95af-114">Následující příklad kódu ukazuje, jak deklarovat tyto objekty:</span><span class="sxs-lookup"><span data-stu-id="e95af-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="e95af-115">Následující ilustrace znázorňuje dvě hierarchie oboru názvů, které obsahují objekt s názvem `ListBox`:</span><span class="sxs-lookup"><span data-stu-id="e95af-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Snímek obrazovky, který ukazuje dvě hierarchie oboru názvů.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="e95af-117">Ve výchozím nastavení každý spustitelný soubor, který vytvoříte pomocí Visual Basic, obsahuje obor názvů se stejným názvem jako váš projekt.</span><span class="sxs-lookup"><span data-stu-id="e95af-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="e95af-118">Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject`, spustitelný soubor ListBoxProject. exe obsahuje obor názvů nazvaný `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="e95af-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="e95af-119">Více sestavení může používat stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e95af-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="e95af-120">Visual Basic je považuje za jednu sadu názvů.</span><span class="sxs-lookup"><span data-stu-id="e95af-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="e95af-121">Můžete například definovat třídy pro obor názvů s názvem `SomeNameSpace` v sestavení s názvem `Assemb1`a definovat další třídy pro stejný obor názvů ze sestavení s názvem `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="e95af-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="e95af-122">Plně kvalifikované názvy</span><span class="sxs-lookup"><span data-stu-id="e95af-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="e95af-123">Plně kvalifikované názvy jsou odkazy na objekty, které jsou s předponou názvu oboru názvů, ve kterém je objekt definován.</span><span class="sxs-lookup"><span data-stu-id="e95af-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="e95af-124">Můžete použít objekty definované v jiných projektech, pokud vytvoříte odkaz na třídu (kliknutím na **Přidat odkaz** z nabídky **projekt** ) a potom použijete plně kvalifikovaný název objektu v kódu.</span><span class="sxs-lookup"><span data-stu-id="e95af-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="e95af-125">Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název objektu z jiného oboru názvů projektu:</span><span class="sxs-lookup"><span data-stu-id="e95af-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="e95af-126">Plně kvalifikované názvy zabraňují konfliktům názvů, protože umožňují kompilátoru určit, který objekt se používá.</span><span class="sxs-lookup"><span data-stu-id="e95af-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="e95af-127">Vlastní jména ale můžou být dlouhá a nenáročný.</span><span class="sxs-lookup"><span data-stu-id="e95af-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="e95af-128">Chcete-li se tomuto problému vyhnout, můžete použít příkaz `Imports` k definování *aliasu*– zkrácený název, který můžete použít místo plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="e95af-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="e95af-129">Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a použije tyto aliasy k definování dvou objektů.</span><span class="sxs-lookup"><span data-stu-id="e95af-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="e95af-130">Použijete-li příkaz `Imports` bez aliasu, můžete použít všechny názvy v tomto oboru názvů bez kvalifikace, pokud jsou pro projekt jedinečné.</span><span class="sxs-lookup"><span data-stu-id="e95af-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="e95af-131">Pokud váš projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, je nutné plně kvalifikovat tento název při použití.</span><span class="sxs-lookup"><span data-stu-id="e95af-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="e95af-132">Předpokládejme například, že váš projekt obsahuje následující dva `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="e95af-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="e95af-133">Pokud se pokusíte použít `Class1` bez úplného zařazení, Visual Basic vytvoří chybu s oznámením, že název `Class1` je dvojznačný.</span><span class="sxs-lookup"><span data-stu-id="e95af-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="e95af-134">Příkazy na úrovni oboru názvů</span><span class="sxs-lookup"><span data-stu-id="e95af-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="e95af-135">V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegáty, výčty, struktury a jiné obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e95af-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="e95af-136">Na úrovni oboru názvů nelze definovat položky, jako jsou vlastnosti, procedury, proměnné a události.</span><span class="sxs-lookup"><span data-stu-id="e95af-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="e95af-137">Tyto položky musí být deklarovány v rámci kontejnerů, jako jsou moduly, struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="e95af-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="e95af-138">Klíčové slovo Global v plně kvalifikovaném názvu</span><span class="sxs-lookup"><span data-stu-id="e95af-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="e95af-139">Pokud jste definovali vnořenou hierarchii oborů názvů, kód uvnitř této hierarchie může být zablokován pro přístup k oboru názvů <xref:System?displayProperty=nameWithType> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e95af-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="e95af-140">Následující příklad znázorňuje hierarchii, ve které `SpecialSpace.System` obor názvů blokuje přístup k <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e95af-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="e95af-141">V důsledku toho kompilátor Visual Basic nemůže úspěšně přeložit odkaz na <xref:System.Int32?displayProperty=nameWithType>, protože `SpecialSpace.System` nedefinuje `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e95af-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="e95af-142">Pomocí klíčového slova `Global` můžete spustit řetěz kvalifikace na krajní úrovni .NET Framework knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="e95af-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="e95af-143">To umožňuje zadat obor názvů <xref:System?displayProperty=nameWithType> nebo jakýkoli jiný obor názvů v knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="e95af-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="e95af-144">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e95af-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="e95af-145">`Global` můžete použít pro přístup k dalším oborům názvů na kořenové úrovni, jako je například <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, a jakémukoli oboru názvů přidruženému k vašemu projektu.</span><span class="sxs-lookup"><span data-stu-id="e95af-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="e95af-146">Klíčové slovo Global v příkazech Namespace</span><span class="sxs-lookup"><span data-stu-id="e95af-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="e95af-147">Můžete také použít klíčové slovo `Global` v [příkazu Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e95af-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="e95af-148">To umožňuje definovat obor názvů mimo kořenový obor názvů vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="e95af-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="e95af-149">Všechny obory názvů v projektu jsou založené na kořenovém oboru názvů projektu.</span><span class="sxs-lookup"><span data-stu-id="e95af-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="e95af-150">Visual Studio přiřadí název vašeho projektu jako výchozí kořenový obor názvů pro veškerý kód v projektu.</span><span class="sxs-lookup"><span data-stu-id="e95af-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="e95af-151">Například pokud je projekt pojmenován `ConsoleApplication1`, jeho programovací prvky patří do oboru názvů `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="e95af-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="e95af-152">Pokud deklarujete `Namespace Magnetosphere`, odkazy na `Magnetosphere` v projektu budou přistupovat `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="e95af-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="e95af-153">Následující příklady používají klíčové slovo `Global` k deklaraci oboru názvů mimo kořenový obor názvů pro projekt.</span><span class="sxs-lookup"><span data-stu-id="e95af-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="e95af-154">V deklaraci oboru názvů nelze `Global` vnořovat do jiného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e95af-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="e95af-155">Můžete použít [stránku aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) k zobrazení a úpravě **kořenového oboru názvů** projektu.</span><span class="sxs-lookup"><span data-stu-id="e95af-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="e95af-156">Pro nové projekty je výchozím **kořenovým oborem názvů** název projektu.</span><span class="sxs-lookup"><span data-stu-id="e95af-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="e95af-157">Chcete-li `Global` být oborem názvů nejvyšší úrovně, můžete vymazat položku **kořenového oboru názvů** tak, aby bylo pole prázdné.</span><span class="sxs-lookup"><span data-stu-id="e95af-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="e95af-158">Vymazání **kořenového oboru názvů** odebere potřebu klíčového slova `Global` v deklaracích oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e95af-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="e95af-159">Pokud příkaz `Namespace` deklaruje název, který je také obor názvů v .NET Framework, .NET Framework obor názvů bude k dispozici, pokud klíčové slovo `Global` není použito v plně kvalifikovaném názvu.</span><span class="sxs-lookup"><span data-stu-id="e95af-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="e95af-160">Chcete-li povolit přístup k tomuto oboru názvů .NET Framework bez použití klíčového slova `Global`, můžete do příkazu `Namespace` zahrnout klíčové slovo `Global`.</span><span class="sxs-lookup"><span data-stu-id="e95af-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="e95af-161">V následujícím příkladu je klíčové slovo `Global` v deklaraci oboru názvů `System.Text`.</span><span class="sxs-lookup"><span data-stu-id="e95af-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="e95af-162">Pokud klíčové slovo `Global` nebylo v deklaraci oboru názvů přítomno, <xref:System.Text.StringBuilder> nelze přistupovat bez zadání `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e95af-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="e95af-163">V případě projektu s názvem `ConsoleApplication1`má odkaz na `System.Text` přístup `ConsoleApplication1.System.Text`, pokud nebylo použito klíčové slovo `Global`.</span><span class="sxs-lookup"><span data-stu-id="e95af-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="e95af-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e95af-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="e95af-165">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="e95af-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="e95af-166">Odkazy a příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="e95af-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="e95af-167">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="e95af-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="e95af-168">Psaní kódu v řešeních pro systém Office</span><span class="sxs-lookup"><span data-stu-id="e95af-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
