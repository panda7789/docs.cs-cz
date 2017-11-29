---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="bd586-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="bd586-102">/optioncompare</span></span>
<span data-ttu-id="bd586-103">Určuje, jak jsou vytvářeny porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="bd586-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd586-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd586-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd586-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd586-105">Remarks</span></span>  
 <span data-ttu-id="bd586-106">Můžete zadat `/optioncompare` v jednom ze dvou formách: `/optioncompare:binary` použít binární porovnání řetězců, a `/optioncompare:text` použít porovnávání řetězců textu.</span><span class="sxs-lookup"><span data-stu-id="bd586-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="bd586-107">Ve výchozím nastavení, kompilátor použije `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="bd586-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="bd586-108">V systému Windows určuje znaková stránka používá binární řazení.</span><span class="sxs-lookup"><span data-stu-id="bd586-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="bd586-109">Typické binární řazení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bd586-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="bd586-110">Porovnání řetězců založený na textu jsou založené na pořadí řazení velká a malá písmena text určen podle národního prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="bd586-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="bd586-111">Pořadí řazení typické text vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bd586-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="bd586-112">Chcete-li nastavit/optioncompare v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd586-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="bd586-113">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="bd586-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bd586-114">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="bd586-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="bd586-115">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="bd586-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="bd586-116">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="bd586-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="bd586-117">Změňte hodnotu v **možnost porovnat** pole.</span><span class="sxs-lookup"><span data-stu-id="bd586-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="bd586-118">Chcete-li nastavit/optioncompare prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="bd586-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="bd586-119">V tématu [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bd586-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd586-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd586-120">Example</span></span>  
 <span data-ttu-id="bd586-121">Následující kód zkompiluje `ProjFile.vb` a používá porovnání binárního řetězce.</span><span class="sxs-lookup"><span data-stu-id="bd586-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd586-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd586-122">See Also</span></span>  
 [<span data-ttu-id="bd586-123">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="bd586-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bd586-124">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="bd586-124">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="bd586-125">/ optionstrict</span><span class="sxs-lookup"><span data-stu-id="bd586-125">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="bd586-126">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="bd586-126">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="bd586-127">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="bd586-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="bd586-128">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="bd586-128">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="bd586-129">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd586-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
