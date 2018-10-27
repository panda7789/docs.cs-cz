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
ms.openlocfilehash: 1d50a3bb739bbde09fa10d2adf03ec7c1ff5d344
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180797"
---
# <a name="-optioncompare"></a><span data-ttu-id="6c64e-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="6c64e-102">-optioncompare</span></span>
<span data-ttu-id="6c64e-103">Určuje způsob porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="6c64e-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c64e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c64e-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="6c64e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c64e-105">Remarks</span></span>  
 <span data-ttu-id="6c64e-106">Můžete zadat `-optioncompare` v jednom z těchto dvou tvarů: `-optioncompare:binary` použít porovnávání binárních řetězců a `-optioncompare:text` používat textové porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="6c64e-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="6c64e-107">Ve výchozím nastavení, kterou kompilátor používá `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="6c64e-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="6c64e-108">V Microsoft Windows určuje aktuální znakové stránce binární řazení.</span><span class="sxs-lookup"><span data-stu-id="6c64e-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="6c64e-109">Typické binární řazení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6c64e-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="6c64e-110">Textový řetězec porovnání jsou založeny na pořadí řazení nerozlišujícího velikost písmen textu určuje podle národního prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="6c64e-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="6c64e-111">Typické textové řazení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6c64e-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="6c64e-112">Chcete-li nastavit - optioncompare v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c64e-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="6c64e-113">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="6c64e-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6c64e-114">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6c64e-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="6c64e-115">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="6c64e-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="6c64e-116">Upravte hodnotu v **Option Compare** pole.</span><span class="sxs-lookup"><span data-stu-id="6c64e-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="6c64e-117">Chcete-li nastavit - optioncompare prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6c64e-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="6c64e-118">Zobrazit [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6c64e-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c64e-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c64e-119">Example</span></span>  
 <span data-ttu-id="6c64e-120">Následující kód zkompiluje `ProjFile.vb` a používá binární porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="6c64e-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c64e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c64e-121">See Also</span></span>  
 [<span data-ttu-id="6c64e-122">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c64e-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6c64e-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="6c64e-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="6c64e-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="6c64e-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="6c64e-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="6c64e-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="6c64e-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="6c64e-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="6c64e-127">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="6c64e-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="6c64e-128">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="6c64e-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
