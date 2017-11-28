---
title: "Odkazy a příkaz Imports (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="626c5-102">Odkazy a příkaz Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="626c5-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="626c5-103">Můžete zpřístupnit externí objekty do projektu výběrem **přidat odkaz na** příkaz na **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="626c5-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="626c5-104">Odkazy na v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] může ukazovat na sestavení, které jsou jako knihovny typů ale obsahují více informací.</span><span class="sxs-lookup"><span data-stu-id="626c5-104">References in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="626c5-105">Příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="626c5-105">The Imports Statement</span></span>  
 <span data-ttu-id="626c5-106">Sestavení obsahovat jeden nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="626c5-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="626c5-107">Když přidáte odkaz na sestavení, můžete také přidat `Imports` příkaz, který má modul, který určuje, zda obory názvů toto sestavení v modulu.</span><span class="sxs-lookup"><span data-stu-id="626c5-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="626c5-108">`Imports` Příkaz poskytuje oboru kontext, který vám umožní používat jenom ta část oboru názvů, který je nutné zadat jedinečný odkaz.</span><span class="sxs-lookup"><span data-stu-id="626c5-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="626c5-109">`Imports` Příkaz má následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="626c5-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="626c5-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="626c5-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="626c5-111">`Aliasname`odkazuje na krátký název, který můžete použít v kódu odkazovat na importovaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="626c5-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="626c5-112">`Namespace`je k dispozici prostřednictvím buď obor názvů odkaz na projekt, prostřednictvím definice v rámci projektu nebo předchozí `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="626c5-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="626c5-113">Modul může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="626c5-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="626c5-114">Musí být po všech `Option` příkazy, pokud existuje, ale před jakýkoli jiný kód.</span><span class="sxs-lookup"><span data-stu-id="626c5-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="626c5-115">Nezaměňujte odkazy na projekt s `Imports` příkaz nebo `Declare` příkaz.</span><span class="sxs-lookup"><span data-stu-id="626c5-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="626c5-116">Odkazy na projekt zpřístupnit externí objekty, například objekty v sestavení, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekty.</span><span class="sxs-lookup"><span data-stu-id="626c5-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projects.</span></span> <span data-ttu-id="626c5-117">`Imports` Příkaz slouží k zjednodušení přístupu k odkazy na projekt, ale neposkytuje přístup k těmto objektům.</span><span class="sxs-lookup"><span data-stu-id="626c5-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="626c5-118">`Declare` Příkaz se používá k deklaraci odkaz na externí procedura v dynamické knihovně (DLL).</span><span class="sxs-lookup"><span data-stu-id="626c5-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="626c5-119">Aliasy pomocí příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="626c5-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="626c5-120">`Imports` Příkaz usnadňuje přístup metody třídy odstraněním potřeba explicitně zadejte plně kvalifikované názvy odkazy.</span><span class="sxs-lookup"><span data-stu-id="626c5-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="626c5-121">Aliasy umožňují příjemnější název přiřadit pouze jeden součástí oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="626c5-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="626c5-122">Například pořadí, které způsobí, že jedna část textu, který se má zobrazit na více řádcích vrátit znaků CR/nového řádku je součástí <xref:Microsoft.VisualBasic.ControlChars> modulu v <xref:Microsoft.VisualBasic?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="626c5-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="626c5-123">Pokud chcete používat tuto konstanta v programu bez alias, museli byste zadáním následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="626c5-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="626c5-124">`Imports`příkazy musí být vždycky okamžitě následující všechny řádky první `Option` příkazy v modulu.</span><span class="sxs-lookup"><span data-stu-id="626c5-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="626c5-125">Následující fragment kódu ukazuje, jak importovat a přiřadit na alias <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modul:</span><span class="sxs-lookup"><span data-stu-id="626c5-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="626c5-126">Může být výrazně kratší budoucí odkazy na tento obor názvů:</span><span class="sxs-lookup"><span data-stu-id="626c5-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="626c5-127">Pokud `Imports` příkaz neobsahuje název aliasu, elementy, které jsou definované v rámci oboru názvů importované lze použít v modulu bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="626c5-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="626c5-128">Pokud je zadaný název aliasu, musíte ho použít jako kvalifikátory pro názvy obsažené v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="626c5-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626c5-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="626c5-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [<span data-ttu-id="626c5-130">NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz</span><span class="sxs-lookup"><span data-stu-id="626c5-130">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="626c5-131">Obory názvů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="626c5-131">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="626c5-132">Sestavení a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="626c5-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="626c5-133">Postupy: vytvoření a použití sestavení s pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="626c5-133">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="626c5-134">Imports – příkaz (Namespace .NET a typ)</span><span class="sxs-lookup"><span data-stu-id="626c5-134">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
