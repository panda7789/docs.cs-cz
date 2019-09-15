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
ms.openlocfilehash: 5b810af86f8659ffbe27d23d36aece408516a9bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972049"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="1e219-102">Odkazy a příkaz Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e219-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="1e219-103">Můžete zpřístupnit externí objekty projektu výběrem příkazu **Přidat odkaz** v nabídce **projekt** .</span><span class="sxs-lookup"><span data-stu-id="1e219-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="1e219-104">Odkazy v Visual Basic mohou odkazovat na sestavení, která jsou jako knihovny typů, ale obsahují více informací.</span><span class="sxs-lookup"><span data-stu-id="1e219-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="1e219-105">Příkaz Imports</span><span class="sxs-lookup"><span data-stu-id="1e219-105">The Imports Statement</span></span>  
 <span data-ttu-id="1e219-106">Sestavení zahrnují jeden nebo více oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="1e219-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="1e219-107">Když přidáte odkaz na sestavení, můžete také přidat `Imports` příkaz do modulu, který ovládá viditelnost oborů názvů tohoto sestavení v rámci modulu.</span><span class="sxs-lookup"><span data-stu-id="1e219-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="1e219-108">`Imports` Příkaz poskytuje obor kontextu, který umožňuje používat pouze část oboru názvů, který je nezbytný k poskytnutí jedinečného odkazu.</span><span class="sxs-lookup"><span data-stu-id="1e219-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="1e219-109">`Imports` Příkaz má následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="1e219-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="1e219-110">`Aliasname`odkazuje na krátký název, který lze použít v rámci kódu pro odkazování na importovaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1e219-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="1e219-111">`Namespace`je obor názvů dostupný prostřednictvím odkazu na projekt, prostřednictvím definice v rámci projektu nebo prostřednictvím předchozího `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1e219-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="1e219-112">Modul může obsahovat libovolný počet `Imports` příkazů.</span><span class="sxs-lookup"><span data-stu-id="1e219-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="1e219-113">Musí se vyskytovat po všech `Option` příkazech, pokud jsou přítomny, ale před jakýmkoli jiným kódem.</span><span class="sxs-lookup"><span data-stu-id="1e219-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e219-114">Nezaměňujte odkazy na projekt pomocí `Imports` příkazu `Declare` nebo příkazu.</span><span class="sxs-lookup"><span data-stu-id="1e219-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="1e219-115">Odkazy na projekt zpřístupňují externí objekty, například objekty v sestaveních, k dispozici pro Visual Basic projekty.</span><span class="sxs-lookup"><span data-stu-id="1e219-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="1e219-116">`Imports` Příkaz slouží k zjednodušení přístupu k odkazům na projekt, ale neposkytuje přístup k těmto objektům.</span><span class="sxs-lookup"><span data-stu-id="1e219-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="1e219-117">`Declare` Příkaz se používá k deklaraci odkazu na externí proceduru v knihovně DLL (Dynamic-Link Library).</span><span class="sxs-lookup"><span data-stu-id="1e219-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="1e219-118">Použití aliasů s příkazem Imports</span><span class="sxs-lookup"><span data-stu-id="1e219-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="1e219-119">`Imports` Příkaz usnadňuje přístup k metodám tříd tím, že eliminuje nutnost explicitně zadat plně kvalifikované názvy odkazů.</span><span class="sxs-lookup"><span data-stu-id="1e219-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="1e219-120">Aliasy umožňují přiřadit název příjemnější pouze jedné části oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e219-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="1e219-121">Například sekvence návratového a řádkového kanálu, která způsobuje, že se na více řádcích zobrazí jedna část textu, je součástí <xref:Microsoft.VisualBasic.ControlChars> modulu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e219-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1e219-122">Chcete-li použít tuto konstantu v programu bez aliasu, je třeba zadat následující kód:</span><span class="sxs-lookup"><span data-stu-id="1e219-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1e219-123">`Imports`příkazy musí být vždy první řádky hned za všemi `Option` příkazy v modulu.</span><span class="sxs-lookup"><span data-stu-id="1e219-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="1e219-124">Následující fragment kódu ukazuje, jak importovat a přiřadit k <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modulu alias:</span><span class="sxs-lookup"><span data-stu-id="1e219-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1e219-125">Budoucí odkazy na tento obor názvů můžou být výrazně kratší:</span><span class="sxs-lookup"><span data-stu-id="1e219-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="1e219-126">`Imports` Pokud příkaz neobsahuje název aliasu, prvky definované v rámci importovaného oboru názvů lze v modulu použít bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="1e219-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="1e219-127">Pokud je název aliasu zadán, je nutné jej použít jako kvalifikátor názvů obsažených v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e219-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e219-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e219-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="1e219-129">Obory názvů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e219-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="1e219-130">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="1e219-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="1e219-131">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="1e219-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
