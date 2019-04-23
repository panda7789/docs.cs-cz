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
ms.openlocfilehash: 54d438541e8840e4394b24b20b4f394ff8cdb820
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332388"
---
# <a name="-optionexplicit"></a><span data-ttu-id="13fcc-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="13fcc-102">-optionexplicit</span></span>
<span data-ttu-id="13fcc-103">Pokud proměnné nejsou deklarovány před jejich použití způsobí, že kompilátor pro hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="13fcc-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13fcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13fcc-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="13fcc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="13fcc-105">Arguments</span></span>  
 <span data-ttu-id="13fcc-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="13fcc-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="13fcc-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="13fcc-107">Optional.</span></span> <span data-ttu-id="13fcc-108">Zadejte `-optionexplicit+` tak, aby vyžadovala explicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="13fcc-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="13fcc-109">`-optionexplicit+` Možnost je výchozí a je stejný jako `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="13fcc-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="13fcc-110">`-optionexplicit-` Možnost umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="13fcc-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13fcc-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13fcc-111">Remarks</span></span>  
 <span data-ttu-id="13fcc-112">Pokud soubor zdrojového kódu obsahuje [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz `-optionexplicit` nastavení příkazového řádku kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="13fcc-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="13fcc-113">Chcete-li nastavit - optionexplicit v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13fcc-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="13fcc-114">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="13fcc-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="13fcc-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="13fcc-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="13fcc-116">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="13fcc-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="13fcc-117">Upravte hodnotu v **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="13fcc-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13fcc-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="13fcc-118">Example</span></span>  
 <span data-ttu-id="13fcc-119">Následující kód zkompiluje, kdy `-optionexplicit-` se používá.</span><span class="sxs-lookup"><span data-stu-id="13fcc-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="13fcc-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13fcc-120">See also</span></span>

- [<span data-ttu-id="13fcc-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="13fcc-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="13fcc-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="13fcc-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="13fcc-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="13fcc-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="13fcc-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="13fcc-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="13fcc-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="13fcc-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="13fcc-126">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="13fcc-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="13fcc-127">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="13fcc-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
