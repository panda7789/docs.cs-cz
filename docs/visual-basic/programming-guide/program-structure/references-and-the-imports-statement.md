---
title: Odkazy a příkaz Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347278"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="6548c-102">Odkazy a příkaz Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6548c-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="6548c-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span><span class="sxs-lookup"><span data-stu-id="6548c-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="6548c-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span><span class="sxs-lookup"><span data-stu-id="6548c-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="6548c-105">The Imports Statement</span><span class="sxs-lookup"><span data-stu-id="6548c-105">The Imports Statement</span></span>  
 <span data-ttu-id="6548c-106">Assemblies include one or more namespaces.</span><span class="sxs-lookup"><span data-stu-id="6548c-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="6548c-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span><span class="sxs-lookup"><span data-stu-id="6548c-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="6548c-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span><span class="sxs-lookup"><span data-stu-id="6548c-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="6548c-109">The `Imports` statement has the following syntax:</span><span class="sxs-lookup"><span data-stu-id="6548c-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="6548c-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span><span class="sxs-lookup"><span data-stu-id="6548c-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="6548c-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="6548c-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="6548c-112">A module may contain any number of `Imports` statements.</span><span class="sxs-lookup"><span data-stu-id="6548c-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="6548c-113">They must appear after any `Option` statements, if present, but before any other code.</span><span class="sxs-lookup"><span data-stu-id="6548c-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6548c-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span><span class="sxs-lookup"><span data-stu-id="6548c-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="6548c-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span><span class="sxs-lookup"><span data-stu-id="6548c-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="6548c-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span><span class="sxs-lookup"><span data-stu-id="6548c-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="6548c-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span><span class="sxs-lookup"><span data-stu-id="6548c-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="6548c-118">Using Aliases with the Imports Statement</span><span class="sxs-lookup"><span data-stu-id="6548c-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="6548c-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span><span class="sxs-lookup"><span data-stu-id="6548c-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="6548c-120">Aliases let you assign a friendlier name to just one part of a namespace.</span><span class="sxs-lookup"><span data-stu-id="6548c-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="6548c-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="6548c-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6548c-122">To use this constant in a program without an alias, you would need to type the following code:</span><span class="sxs-lookup"><span data-stu-id="6548c-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="6548c-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span><span class="sxs-lookup"><span data-stu-id="6548c-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="6548c-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span><span class="sxs-lookup"><span data-stu-id="6548c-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="6548c-125">Future references to this namespace can be considerably shorter:</span><span class="sxs-lookup"><span data-stu-id="6548c-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="6548c-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span><span class="sxs-lookup"><span data-stu-id="6548c-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="6548c-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span><span class="sxs-lookup"><span data-stu-id="6548c-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6548c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6548c-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="6548c-129">Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6548c-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="6548c-130">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="6548c-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="6548c-131">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="6548c-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
