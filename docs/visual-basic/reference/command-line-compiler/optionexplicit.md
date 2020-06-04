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
ms.openlocfilehash: b004acb0c1c7d145c59a1e3a88ef7f1d405a91c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400553"
---
# <a name="-optionexplicit"></a><span data-ttu-id="922cf-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="922cf-102">-optionexplicit</span></span>
<span data-ttu-id="922cf-103">Způsobí, že kompilátor ohlásí chyby, pokud proměnné nejsou deklarovány dříve, než budou použity.</span><span class="sxs-lookup"><span data-stu-id="922cf-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="922cf-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="922cf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="922cf-105">Arguments</span></span>  
 <span data-ttu-id="922cf-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="922cf-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="922cf-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="922cf-107">Optional.</span></span> <span data-ttu-id="922cf-108">Určete `-optionexplicit+` , aby vyžadoval explicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="922cf-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="922cf-109">`-optionexplicit+`Možnost je výchozí a je stejná jako `-optionexplicit` .</span><span class="sxs-lookup"><span data-stu-id="922cf-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="922cf-110">`-optionexplicit-`Možnost umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="922cf-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="922cf-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="922cf-111">Remarks</span></span>  
 <span data-ttu-id="922cf-112">Pokud soubor zdrojového kódu obsahuje [příkaz Option Explicit](../../language-reference/statements/option-explicit-statement.md), příkaz přepíše `-optionexplicit` nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="922cf-112">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="922cf-113">Nastavení-OptionExplicit – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="922cf-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="922cf-114">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="922cf-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="922cf-115">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="922cf-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="922cf-116">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="922cf-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="922cf-117">Upravte hodnotu v poli **explicitní možnosti** .</span><span class="sxs-lookup"><span data-stu-id="922cf-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="922cf-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="922cf-118">Example</span></span>  
 <span data-ttu-id="922cf-119">Následující kód kompiluje při `-optionexplicit-` použití.</span><span class="sxs-lookup"><span data-stu-id="922cf-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="922cf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="922cf-120">See also</span></span>

- [<span data-ttu-id="922cf-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="922cf-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="922cf-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="922cf-122">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="922cf-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="922cf-123">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="922cf-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="922cf-124">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="922cf-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="922cf-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="922cf-126">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="922cf-126">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="922cf-127">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="922cf-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
