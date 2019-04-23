---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: b88cba4d16c5a770a72b47868d11b16cbba6cae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340435"
---
# <a name="-optioncompare"></a><span data-ttu-id="c0dc0-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c0dc0-102">-optioncompare</span></span>
<span data-ttu-id="c0dc0-103">Určuje způsob porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0dc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0dc0-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0dc0-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0dc0-105">Remarks</span></span>  
 <span data-ttu-id="c0dc0-106">Můžete zadat `-optioncompare` v jednom z těchto dvou tvarů: `-optioncompare:binary` použít porovnávání binárních řetězců a `-optioncompare:text` používat textové porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="c0dc0-107">Ve výchozím nastavení, kterou kompilátor používá `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="c0dc0-108">V Microsoft Windows určuje aktuální znakové stránce binární řazení.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="c0dc0-109">Typické binární řazení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c0dc0-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="c0dc0-110">Textový řetězec porovnání jsou založeny na pořadí řazení nerozlišujícího velikost písmen textu určuje podle národního prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="c0dc0-111">Typické textové řazení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="c0dc0-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="c0dc0-112">Chcete-li nastavit - optioncompare v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c0dc0-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="c0dc0-113">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c0dc0-114">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-114">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="c0dc0-115">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-115">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="c0dc0-116">Upravte hodnotu v **Option Compare** pole.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="c0dc0-117">Chcete-li nastavit - optioncompare prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="c0dc0-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="c0dc0-118">Zobrazit [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c0dc0-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0dc0-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0dc0-119">Example</span></span>  
 <span data-ttu-id="c0dc0-120">Následující kód zkompiluje `ProjFile.vb` a používá binární porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="c0dc0-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0dc0-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0dc0-121">See also</span></span>

- [<span data-ttu-id="c0dc0-122">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="c0dc0-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c0dc0-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c0dc0-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="c0dc0-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="c0dc0-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="c0dc0-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="c0dc0-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="c0dc0-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c0dc0-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c0dc0-127">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="c0dc0-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="c0dc0-128">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="c0dc0-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
