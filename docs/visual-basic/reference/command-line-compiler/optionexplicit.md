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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005306"
---
# <a name="-optionexplicit"></a><span data-ttu-id="0ff90-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0ff90-102">-optionexplicit</span></span>
<span data-ttu-id="0ff90-103">Způsobí, že kompilátor ohlásí chyby, pokud proměnné nejsou deklarovány dříve, než budou použity.</span><span class="sxs-lookup"><span data-stu-id="0ff90-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ff90-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ff90-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ff90-105">Arguments</span></span>  
 <span data-ttu-id="0ff90-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0ff90-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="0ff90-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0ff90-107">Optional.</span></span> <span data-ttu-id="0ff90-108">Zadejte `-optionexplicit+` pro vyžadování explicitní deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="0ff90-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="0ff90-109">Možnost `-optionexplicit+` je výchozí a je stejná jako `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="0ff90-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="0ff90-110">Možnost `-optionexplicit-` povoluje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="0ff90-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ff90-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ff90-111">Remarks</span></span>  
 <span data-ttu-id="0ff90-112">Pokud soubor zdrojového kódu obsahuje [příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz nastavení kompilátoru příkazového řádku `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="0ff90-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="0ff90-113">Nastavení-OptionExplicit – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ff90-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="0ff90-114">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="0ff90-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0ff90-115">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0ff90-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="0ff90-116">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="0ff90-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="0ff90-117">Upravte hodnotu v poli **explicitní možnosti** .</span><span class="sxs-lookup"><span data-stu-id="0ff90-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ff90-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ff90-118">Example</span></span>  
 <span data-ttu-id="0ff90-119">Následující kód je zkompilován při použití `-optionexplicit-`.</span><span class="sxs-lookup"><span data-stu-id="0ff90-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="0ff90-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ff90-120">See also</span></span>

- [<span data-ttu-id="0ff90-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0ff90-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0ff90-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="0ff90-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="0ff90-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="0ff90-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="0ff90-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="0ff90-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="0ff90-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0ff90-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="0ff90-126">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="0ff90-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="0ff90-127">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="0ff90-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
