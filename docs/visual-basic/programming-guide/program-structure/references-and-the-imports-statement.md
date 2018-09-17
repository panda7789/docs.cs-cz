---
title: Odkazy a příkaz Imports (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 89d360e5caa3cdb0dd1ecb985ea7ba727e5a6d9d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45692668"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="24e3b-102">Odkazy a příkaz Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24e3b-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="24e3b-103">Můžete zpřístupnit externí objekty do vašeho projektu výběrem **přidat odkaz** příkaz **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="24e3b-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="24e3b-104">Odkazy v jazyce Visual Basic se může odkazovat na sestavení, které jsou podobné, ale obsahují další informace o knihovnách typů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="24e3b-105">Příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="24e3b-105">The Imports Statement</span></span>  
 <span data-ttu-id="24e3b-106">Sestavení obsahují jeden nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="24e3b-107">Když přidáte odkaz na sestavení, můžete také přidat `Imports` příkazu pro modul, který určuje, zda se toto sestavení obory názvů v rámci modulu.</span><span class="sxs-lookup"><span data-stu-id="24e3b-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="24e3b-108">`Imports` Příkaz poskytuje oboru kontext, který vám umožní používat pouze část oboru názvů, který je nutné zadat jedinečný odkaz.</span><span class="sxs-lookup"><span data-stu-id="24e3b-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="24e3b-109">`Imports` Příkaz má následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="24e3b-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="24e3b-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="24e3b-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="24e3b-111">`Aliasname` odkazuje na krátký název, který můžete použít v kódu k odkazování na importované oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="24e3b-112">`Namespace` je k dispozici prostřednictvím obor názvů odkazu na projekt, prostřednictvím definice v rámci projektu, nebo předchozí `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="24e3b-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="24e3b-113">Modul může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="24e3b-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="24e3b-114">Musí být uvedena po všech `Option` příkazy, pokud jsou k dispozici, ale před spuštěním kódu.</span><span class="sxs-lookup"><span data-stu-id="24e3b-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24e3b-115">Nepleťte si odkazy na projekt s `Imports` příkazu nebo `Declare` příkazu.</span><span class="sxs-lookup"><span data-stu-id="24e3b-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="24e3b-116">Odkazy na projekt zpřístupnit externí objekty, jako jsou objekty v sestaveních pro projekty jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="24e3b-116">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="24e3b-117">`Imports` Prohlášení se používá pro zjednodušení přístupu do odkazů projektu, ale neposkytuje přístup k těmto objektům.</span><span class="sxs-lookup"><span data-stu-id="24e3b-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="24e3b-118">`Declare` Prohlášení se používá k deklarování odkazu na externí procedura v dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="24e3b-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="24e3b-119">Aliasy Using se příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="24e3b-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="24e3b-120">`Imports` Příkaz usnadňuje přístup metod tříd pomocí tím eliminuje nutnost explicitně zadejte plně kvalifikované názvy odkazů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="24e3b-121">Aliasy umožňují lépe vyhovující název přiřadit pouze jednu část oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="24e3b-122">Například sekvence, která způsobí, že každé text, který se má zobrazit na více řádcích vrátit návrat na začátek řádku a nového řádku je součástí <xref:Microsoft.VisualBasic.ControlChars> v modulu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="24e3b-123">Použití této konstanty v programu bez alias, je třeba zadáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="24e3b-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="24e3b-124">`Imports` příkazy musí být vždy první řádky hned za všechny `Option` příkazy v modulu.</span><span class="sxs-lookup"><span data-stu-id="24e3b-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="24e3b-125">Následující fragment kódu ukazuje, jak importovat a přiřadit alias <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modul:</span><span class="sxs-lookup"><span data-stu-id="24e3b-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="24e3b-126">Budoucí odkazy na tento obor názvů může být podstatně kratší:</span><span class="sxs-lookup"><span data-stu-id="24e3b-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="24e3b-127">Pokud `Imports` příkaz neobsahuje název aliasu, prvky definované v rámci importované oboru názvů lze použít v modulu bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="24e3b-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="24e3b-128">Pokud je zadán název aliasu, se musí použít jako kvalifikátoru pro názvy obsažené v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="24e3b-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e3b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24e3b-129">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="24e3b-130">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24e3b-130">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
- [<span data-ttu-id="24e3b-131">Sestavení a globální mezipaměť sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="24e3b-131">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="24e3b-132">Postupy: Vytváření a použití sestavení s pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="24e3b-132">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [<span data-ttu-id="24e3b-133">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="24e3b-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
