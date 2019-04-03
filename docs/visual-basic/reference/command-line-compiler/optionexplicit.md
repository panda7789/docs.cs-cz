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
ms.openlocfilehash: 4aca6e9c20dbce7aa8a94067c96fcf44329a6fe4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814871"
---
# <a name="-optionexplicit"></a><span data-ttu-id="70d46-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="70d46-102">-optionexplicit</span></span>
<span data-ttu-id="70d46-103">Pokud proměnné nejsou deklarovány před jejich použití způsobí, že kompilátor pro hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="70d46-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70d46-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="70d46-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="70d46-105">Arguments</span></span>  
 <span data-ttu-id="70d46-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="70d46-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="70d46-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="70d46-107">Optional.</span></span> <span data-ttu-id="70d46-108">Zadejte `-optionexplicit+` tak, aby vyžadovala explicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="70d46-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="70d46-109">`-optionexplicit+` Možnost je výchozí a je stejný jako `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="70d46-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="70d46-110">`-optionexplicit-` Možnost umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="70d46-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70d46-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70d46-111">Remarks</span></span>  
 <span data-ttu-id="70d46-112">Pokud soubor zdrojového kódu obsahuje [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz `-optionexplicit` nastavení příkazového řádku kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="70d46-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="70d46-113">Chcete-li nastavit - optionexplicit v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70d46-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="70d46-114">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="70d46-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="70d46-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="70d46-115">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="70d46-116">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="70d46-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="70d46-117">Upravte hodnotu v **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="70d46-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70d46-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="70d46-118">Example</span></span>  
 <span data-ttu-id="70d46-119">Následující kód zkompiluje, kdy `-optionexplicit-` se používá.</span><span class="sxs-lookup"><span data-stu-id="70d46-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="70d46-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70d46-120">See also</span></span>

- [<span data-ttu-id="70d46-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="70d46-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="70d46-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="70d46-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="70d46-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="70d46-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="70d46-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="70d46-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="70d46-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="70d46-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="70d46-126">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="70d46-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="70d46-127">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="70d46-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
