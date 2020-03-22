---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266726"
---
# <a name="-optionexplicit"></a><span data-ttu-id="15c79-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="15c79-102">-optionexplicit</span></span>
<span data-ttu-id="15c79-103">Způsobí, že kompilátor hlásit chyby, pokud proměnné nejsou deklarovány před jejich použitím.</span><span class="sxs-lookup"><span data-stu-id="15c79-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c79-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="15c79-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="15c79-105">Arguments</span></span>  
 <span data-ttu-id="15c79-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="15c79-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="15c79-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="15c79-107">Optional.</span></span> <span data-ttu-id="15c79-108">Určete, `-optionexplicit+` chcete-li vyžadovat explicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="15c79-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="15c79-109">Tato `-optionexplicit+` možnost je výchozí a `-optionexplicit`je stejná jako .</span><span class="sxs-lookup"><span data-stu-id="15c79-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="15c79-110">Tato `-optionexplicit-` možnost umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="15c79-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15c79-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15c79-111">Remarks</span></span>  
 <span data-ttu-id="15c79-112">Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../../visual-basic/language-reference/statements/option-explicit-statement.md)Explicit `-optionexplicit` , příkaz přepíše nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="15c79-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="15c79-113">Nastavení -optionexplicit v ide sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15c79-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="15c79-114">V **Průzkumníku řešení**je vybrán projekt .</span><span class="sxs-lookup"><span data-stu-id="15c79-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="15c79-115">V nabídce **Project** klepněte na **položku Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="15c79-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="15c79-116">Klikněte na kartu **Kompilace.**</span><span class="sxs-lookup"><span data-stu-id="15c79-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="15c79-117">Upravte hodnotu v poli **Explicitní možnost.**</span><span class="sxs-lookup"><span data-stu-id="15c79-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15c79-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="15c79-118">Example</span></span>  
 <span data-ttu-id="15c79-119">Následující kód zkompiluje při `-optionexplicit-` použití.</span><span class="sxs-lookup"><span data-stu-id="15c79-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="15c79-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="15c79-120">See also</span></span>

- [<span data-ttu-id="15c79-121">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15c79-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="15c79-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="15c79-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="15c79-123">-optionstrict -optionstrict -optionstrict -option</span><span class="sxs-lookup"><span data-stu-id="15c79-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="15c79-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="15c79-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="15c79-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="15c79-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="15c79-126">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="15c79-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="15c79-127">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="15c79-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
