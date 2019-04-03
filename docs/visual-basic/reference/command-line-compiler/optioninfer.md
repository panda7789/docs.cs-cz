---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 89fcd981dbb5442f6150f539db4c7d404fe8d691
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839844"
---
# <a name="-optioninfer"></a><span data-ttu-id="3e27a-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="3e27a-102">-optioninfer</span></span>
<span data-ttu-id="3e27a-103">Umožňuje použití odvození místního typu v deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="3e27a-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e27a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e27a-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e27a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3e27a-105">Arguments</span></span>  
  
|<span data-ttu-id="3e27a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="3e27a-106">Term</span></span>|<span data-ttu-id="3e27a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3e27a-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="3e27a-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="3e27a-108">`+` &#124; `-`</span></span>|<span data-ttu-id="3e27a-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e27a-109">Optional.</span></span> <span data-ttu-id="3e27a-110">Zadejte `-optioninfer+` umožňující odvození místního typu, nebo `-optioninfer-` ho blokovala.</span><span class="sxs-lookup"><span data-stu-id="3e27a-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="3e27a-111">`-optioninfer` Parametrem žádná hodnota zadána, je stejný jako `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="3e27a-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="3e27a-112">Výchozí hodnotu v případě `-optioninfer` přepínač není k dispozici je také `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="3e27a-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="3e27a-113">Výchozí hodnota je nastavena v souboru odpovědí Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="3e27a-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3e27a-114">Můžete použít `-noconfig` – možnost kompilátoru interní výchozí hodnoty namísto platformám zadaným v vbc.rsp zachovat.</span><span class="sxs-lookup"><span data-stu-id="3e27a-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="3e27a-115">Výchozí nastavení kompilátoru pro tuto možnost je `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="3e27a-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e27a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e27a-116">Remarks</span></span>  
 <span data-ttu-id="3e27a-117">Pokud soubor zdrojového kódu obsahuje [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz `-optioninfer` nastavení příkazového řádku kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3e27a-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="3e27a-118">Chcete-li nastavit - optioninfer v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e27a-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="3e27a-119">Vyberte projekt v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="3e27a-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="3e27a-120">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3e27a-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="3e27a-121">Na **kompilaci** kartu, upravte hodnotu v **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="3e27a-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e27a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e27a-122">Example</span></span>  
 <span data-ttu-id="3e27a-123">Následující kód zkompiluje `test.vb` s odvození místního typu povolené.</span><span class="sxs-lookup"><span data-stu-id="3e27a-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e27a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e27a-124">See also</span></span>

- [<span data-ttu-id="3e27a-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="3e27a-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3e27a-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3e27a-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="3e27a-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3e27a-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="3e27a-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="3e27a-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="3e27a-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="3e27a-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="3e27a-130">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="3e27a-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3e27a-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="3e27a-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3e27a-132">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="3e27a-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="3e27a-133">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e27a-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="3e27a-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="3e27a-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="3e27a-135">Sestavení z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3e27a-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
