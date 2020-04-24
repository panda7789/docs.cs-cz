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
# <a name="-optionexplicit"></a><span data-ttu-id="a929a-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="a929a-102">-optionexplicit</span></span>
<span data-ttu-id="a929a-103">Způsobí, že kompilátor ohlásí chyby, pokud proměnné nejsou deklarovány dříve, než budou použity.</span><span class="sxs-lookup"><span data-stu-id="a929a-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a929a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a929a-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a929a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a929a-105">Arguments</span></span>  
 <span data-ttu-id="a929a-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="a929a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a929a-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a929a-107">Optional.</span></span> <span data-ttu-id="a929a-108">Určete `-optionexplicit+` , aby vyžadoval explicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="a929a-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="a929a-109">`-optionexplicit+` Možnost je výchozí a je stejná jako `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="a929a-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="a929a-110">`-optionexplicit-` Možnost umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="a929a-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a929a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a929a-111">Remarks</span></span>  
 <span data-ttu-id="a929a-112">Pokud soubor zdrojového kódu obsahuje [příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), příkaz přepíše nastavení kompilátoru `-optionexplicit` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a929a-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="a929a-113">Nastavení-OptionExplicit – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a929a-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="a929a-114">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="a929a-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a929a-115">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a929a-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="a929a-116">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="a929a-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="a929a-117">Upravte hodnotu v poli **explicitní možnosti** .</span><span class="sxs-lookup"><span data-stu-id="a929a-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a929a-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a929a-118">Example</span></span>  
 <span data-ttu-id="a929a-119">Následující kód kompiluje při `-optionexplicit-` použití.</span><span class="sxs-lookup"><span data-stu-id="a929a-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a929a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a929a-120">See also</span></span>

- [<span data-ttu-id="a929a-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a929a-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a929a-122">– OptionCompare –</span><span class="sxs-lookup"><span data-stu-id="a929a-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="a929a-123">– OptionStrict –</span><span class="sxs-lookup"><span data-stu-id="a929a-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="a929a-124">– optioninfer –</span><span class="sxs-lookup"><span data-stu-id="a929a-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="a929a-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a929a-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a929a-126">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a929a-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="a929a-127">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="a929a-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
