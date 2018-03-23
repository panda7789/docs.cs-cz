---
title: -optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 033be2ce3845ed470d56c2097b89b81d10275046
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-optioncompare"></a><span data-ttu-id="3b86f-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3b86f-102">-optioncompare</span></span>
<span data-ttu-id="3b86f-103">Určuje, jak jsou vytvářeny porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="3b86f-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b86f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b86f-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b86f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b86f-105">Remarks</span></span>  
 <span data-ttu-id="3b86f-106">Můžete zadat `-optioncompare` v jednom ze dvou formách: `-optioncompare:binary` použít binární porovnání řetězců, a `-optioncompare:text` použít porovnávání řetězců textu.</span><span class="sxs-lookup"><span data-stu-id="3b86f-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="3b86f-107">Ve výchozím nastavení, kompilátor použije `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="3b86f-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="3b86f-108">V systému Windows aktuální znaková stránka Určuje binární řazení.</span><span class="sxs-lookup"><span data-stu-id="3b86f-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="3b86f-109">Typické binární řazení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3b86f-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="3b86f-110">Porovnání řetězců založený na textu jsou založené na pořadí řazení velká a malá písmena text určen podle národního prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="3b86f-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="3b86f-111">Pořadí řazení typické text vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3b86f-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="3b86f-112">Chcete-li nastavit - optioncompare v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b86f-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="3b86f-113">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="3b86f-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3b86f-114">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3b86f-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="3b86f-115">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="3b86f-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="3b86f-116">Změňte hodnotu v **možnost porovnat** pole.</span><span class="sxs-lookup"><span data-stu-id="3b86f-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="3b86f-117">Chcete-li nastavit - optioncompare prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="3b86f-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="3b86f-118">V tématu [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b86f-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b86f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b86f-119">Example</span></span>  
 <span data-ttu-id="3b86f-120">Následující kód zkompiluje `ProjFile.vb` a používá porovnání binárního řetězce.</span><span class="sxs-lookup"><span data-stu-id="3b86f-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b86f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b86f-121">See Also</span></span>  
 [<span data-ttu-id="3b86f-122">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="3b86f-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3b86f-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3b86f-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="3b86f-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="3b86f-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="3b86f-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="3b86f-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="3b86f-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="3b86f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="3b86f-127">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="3b86f-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="3b86f-128">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b86f-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
