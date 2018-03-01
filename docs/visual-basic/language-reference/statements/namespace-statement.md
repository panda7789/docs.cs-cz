---
title: "Namespace – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a><span data-ttu-id="a24ca-102">Namespace – příkaz</span><span class="sxs-lookup"><span data-stu-id="a24ca-102">Namespace Statement</span></span>
<span data-ttu-id="a24ca-103">Deklaruje název oboru názvů a způsobí, že zdrojový kód, který odpovídá deklaraci sestavují v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a24ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a24ca-104">Syntax</span></span>  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="a24ca-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a24ca-105">Parts</span></span>  
 <span data-ttu-id="a24ca-106">Globální</span><span class="sxs-lookup"><span data-stu-id="a24ca-106">Global</span></span>  
 <span data-ttu-id="a24ca-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a24ca-107">Optional.</span></span> <span data-ttu-id="a24ca-108">Můžete zadat obor názvů z kořenového oboru názvů vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="a24ca-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="a24ca-109">V tématu [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a24ca-109">See [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="a24ca-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a24ca-110">Required.</span></span> <span data-ttu-id="a24ca-111">Jedinečný název, který identifikuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="a24ca-112">Musí být platný identifikátor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a24ca-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="a24ca-113">Další informace najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a24ca-113">For more information, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="a24ca-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a24ca-114">Optional.</span></span> <span data-ttu-id="a24ca-115">Prvky, které tvoří obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-115">Elements that make up the namespace.</span></span> <span data-ttu-id="a24ca-116">Ty zahrnují, ale nejsou omezeny na výčty, struktury, rozhraní, třídy, moduly, delegáti a jiných oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="a24ca-117">Ukončí `Namespace` bloku.</span><span class="sxs-lookup"><span data-stu-id="a24ca-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a24ca-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a24ca-118">Remarks</span></span>  
 <span data-ttu-id="a24ca-119">Obory názvů se používají jako organizační systému.</span><span class="sxs-lookup"><span data-stu-id="a24ca-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="a24ca-120">Poskytují způsob, jak klasifikovat a prezentovat programovací elementy, které jsou umístěny do jiných aplikací a aplikací.</span><span class="sxs-lookup"><span data-stu-id="a24ca-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="a24ca-121">Všimněte si, že je obor názvů *typ* v tom smyslu, že třídu nebo strukturu – nelze deklarovat jako programovací element mít datový typ oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="a24ca-122">Všechny programovací elementy deklarovaný po `Namespace` příkaz patří do daného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="a24ca-123">Visual Basic nadále kompilována elementy poslední deklarované obor názvů, dokud buď zjistí `End Namespace` příkaz nebo jiné `Namespace` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a24ca-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="a24ca-124">Pokud obor názvů je již definován i mimo projekt, do něj může přidat elementům programování.</span><span class="sxs-lookup"><span data-stu-id="a24ca-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="a24ca-125">K tomuto účelu můžete použít `Namespace` příkaz směrovat jazyka Visual Basic ke kompilaci elementy do daného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="a24ca-126">Můžete použít `Namespace` příkaz jenom na úrovni souboru nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="a24ca-127">To znamená *deklarace kontextu* pro obor názvů musí být zdrojový soubor nebo jiném oboru názvů a nemůže být třída, struktura, modulu, rozhraní nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="a24ca-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="a24ca-128">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a24ca-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="a24ca-129">Je možné deklarovat jeden obor názvů v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="a24ca-129">You can declare one namespace within another.</span></span> <span data-ttu-id="a24ca-130">Neexistuje žádné striktní omezení úrovní vnoření deklarovat, ale mějte na paměti, že když jiný kód získá přístup k elementy deklarované v nejvnitřnější oboru názvů, musí používat kvalifikace řetězec, který obsahuje všechny názvy oborů názvů v hierarchii vnoření.</span><span class="sxs-lookup"><span data-stu-id="a24ca-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="a24ca-131">Úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="a24ca-131">Access Level</span></span>  
 <span data-ttu-id="a24ca-132">Obory názvů jsou zpracovány jako v případě, že mají `Public` úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="a24ca-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="a24ca-133">Obor názvů je přístupný z kódu kamkoli ve stejném projektu, od jiné projekty, které odkazují na projektu a z libovolného sestavení vytvořené z projektu.</span><span class="sxs-lookup"><span data-stu-id="a24ca-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="a24ca-134">Programovací elementy deklarovat na úrovni oboru názvů, což znamená v oboru názvů, ale ne do žádného jiného elementu, může mít `Public` nebo `Friend` přístup.</span><span class="sxs-lookup"><span data-stu-id="a24ca-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="a24ca-135">Pokud tento parametr nezadáte, úroveň přístupu tohoto například element používá `Friend` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a24ca-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="a24ca-136">Prvky, které lze deklarovat na úrovni oboru názvů zahrnují třídy, struktury, moduly, rozhraní, výčty a delegáti.</span><span class="sxs-lookup"><span data-stu-id="a24ca-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="a24ca-137">Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a24ca-137">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="a24ca-138">Namespace kořenové</span><span class="sxs-lookup"><span data-stu-id="a24ca-138">Root Namespace</span></span>  
 <span data-ttu-id="a24ca-139">Všechny názvy oborů názvů ve vašem projektu jsou založené na *kořenový obor názvů*.</span><span class="sxs-lookup"><span data-stu-id="a24ca-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="a24ca-140">Visual Studio přiřadí název projektu jako výchozí kořenový obor názvů pro všechny kódu v projektu.</span><span class="sxs-lookup"><span data-stu-id="a24ca-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="a24ca-141">Například pokud je název projektu `Payroll`, jeho programovací elementy patří do oboru názvů `Payroll`.</span><span class="sxs-lookup"><span data-stu-id="a24ca-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="a24ca-142">Pokud je deklarovat `Namespace funding`, úplný název tohoto oboru názvů je `Payroll.funding`.</span><span class="sxs-lookup"><span data-stu-id="a24ca-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="a24ca-143">Pokud chcete určit existujícího oboru názvů v `Namespace` příkazu, jako v příkladu třída obecné seznamu, můžete nastavit kořenový obor názvů na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a24ca-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="a24ca-144">Chcete-li to provést, klikněte na tlačítko **vlastnosti projektu** z **projektu** nabídky a zrušte zaškrtnutí **kořenový obor názvů** položky tak, aby pole je prázdné.</span><span class="sxs-lookup"><span data-stu-id="a24ca-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="a24ca-145">Pokud není to uděláte v příkladu třída obecný seznam, Visual Basic – kompilátor by trvat `System.Collections.Generic` jako nový obor názvů v rámci projektu `Payroll`, s úplným názvem `Payroll.System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="a24ca-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="a24ca-146">Alternativně můžete použít `Global` – klíčové slovo k odkazování na elementy oborů názvů definovaných mimo projekt.</span><span class="sxs-lookup"><span data-stu-id="a24ca-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="a24ca-147">Tímto způsobem můžete uchovávat název vašeho projektu jako kořenového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="a24ca-148">Tím se snižuje riziko neúmyslně slučování vaší elementům programování společně s ty z existujících oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="a24ca-149">Další informace najdete v části "Globální – klíčové slovo ve plně kvalifikované názvy" v [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a24ca-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="a24ca-150">`Global` – Klíčové slovo lze také použít v příkazu Namespace.</span><span class="sxs-lookup"><span data-stu-id="a24ca-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="a24ca-151">To umožňuje definovat oboru názvů z kořenového oboru názvů vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="a24ca-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="a24ca-152">Další informace najdete v části "Globální – klíčové slovo v Namespace příkazy" v [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a24ca-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="a24ca-153">**Řešení potíží.**</span><span class="sxs-lookup"><span data-stu-id="a24ca-153">**Troubleshooting.**</span></span> <span data-ttu-id="a24ca-154">Kořenového oboru názvů může vést k neočekávaným zřetězování názvy oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="a24ca-155">Pokud provedete odkaz na obory názvů definované mimo projekt, můžete je jako vnořené obory názvů v kořenového oboru názvů construe kompilátoru jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a24ca-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="a24ca-156">V takovém případě kompilátor nemůže rozpoznat všechny typy, které byla již definována v externí obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="a24ca-157">Abyste tomu předešli, buď nastavit na hodnotu null, jak je popsáno v "Kořenový Namespace" kořenový obor názvů nebo použijte `Global` – klíčové slovo na elementy přístup externích oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="a24ca-158">Atributy a modifikátory</span><span class="sxs-lookup"><span data-stu-id="a24ca-158">Attributes and Modifiers</span></span>  
 <span data-ttu-id="a24ca-159">Atributy nelze použít do oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="a24ca-160">Atribut přispívá informace metadat sestavení, která není smysl pro třídění zdroj, například obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="a24ca-161">Všechny přístupy nebo postup modifikátory nebo jiných modifikátory nemůže použít na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="a24ca-162">Protože není typu, nejsou tyto modifikátory smysluplný.</span><span class="sxs-lookup"><span data-stu-id="a24ca-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a24ca-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="a24ca-163">Example</span></span>  
 <span data-ttu-id="a24ca-164">Následující příklad uvádí dva obory názvů, jeden v druhém vnořený.</span><span class="sxs-lookup"><span data-stu-id="a24ca-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a24ca-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="a24ca-165">Example</span></span>  
 <span data-ttu-id="a24ca-166">Následující příklad deklaruje více vnořené obory názvů na jeden řádek, a je ekvivalentní k předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="a24ca-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a24ca-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="a24ca-167">Example</span></span>  
 <span data-ttu-id="a24ca-168">Následující příklad používá třídy definované v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="a24ca-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="a24ca-169">Příklad</span><span class="sxs-lookup"><span data-stu-id="a24ca-169">Example</span></span>  
 <span data-ttu-id="a24ca-170">V následujícím příkladu definuje kostře novou třídu obecný seznam a přidává ji k <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a24ca-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="a24ca-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="a24ca-171">See Also</span></span>  
 [<span data-ttu-id="a24ca-172">Imports – příkaz (Namespace .NET a typ)</span><span class="sxs-lookup"><span data-stu-id="a24ca-172">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="a24ca-173">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="a24ca-173">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="a24ca-174">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a24ca-174">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
