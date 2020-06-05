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
ms.openlocfilehash: 524660fca7c56fa490cc85169898bf2bf6d1a16e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400575"
---
# <a name="-optioninfer"></a><span data-ttu-id="3785a-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="3785a-102">-optioninfer</span></span>
<span data-ttu-id="3785a-103">Povoluje použití odvození místního typu v deklaracích proměnných.</span><span class="sxs-lookup"><span data-stu-id="3785a-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3785a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3785a-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3785a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3785a-105">Arguments</span></span>  
  
|<span data-ttu-id="3785a-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="3785a-106">Term</span></span>|<span data-ttu-id="3785a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3785a-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="3785a-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="3785a-108">`+` &#124; `-`</span></span>|<span data-ttu-id="3785a-109">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3785a-109">Optional.</span></span> <span data-ttu-id="3785a-110">Zadejte `-optioninfer+` , chcete-li povolit odvození místního typu, nebo `-optioninfer-` jej zablokovat.</span><span class="sxs-lookup"><span data-stu-id="3785a-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="3785a-111">`-optioninfer`Možnost bez zadané hodnoty je stejná jako `-optioninfer+` .</span><span class="sxs-lookup"><span data-stu-id="3785a-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="3785a-112">Výchozí hodnota, pokud není k `-optioninfer` dispozici přepínač, je také `-optioninfer+` .</span><span class="sxs-lookup"><span data-stu-id="3785a-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="3785a-113">Výchozí hodnota je nastavena v souboru odpovědí Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="3785a-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3785a-114">Můžete použít `-noconfig` možnost pro zachování vnitřních výchozích hodnot kompilátoru místo těch, které jsou určeny v Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="3785a-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="3785a-115">Výchozí hodnota kompilátoru pro tuto možnost je `-optioninfer-` .</span><span class="sxs-lookup"><span data-stu-id="3785a-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3785a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3785a-116">Remarks</span></span>  
 <span data-ttu-id="3785a-117">Pokud soubor zdrojového kódu obsahuje [příkaz Option](../../language-reference/statements/option-infer-statement.md), přepíše příkaz `-optioninfer` nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3785a-117">If the source code file contains an [Option Infer Statement](../../language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="3785a-118">Nastavení-optioninfer – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3785a-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="3785a-119">Vyberte projekt v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="3785a-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="3785a-120">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3785a-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="3785a-121">Na kartě **kompilovat** upravte hodnotu v poli **možnost odvodit** .</span><span class="sxs-lookup"><span data-stu-id="3785a-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3785a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="3785a-122">Example</span></span>  
 <span data-ttu-id="3785a-123">Následující kód je zkompilován `test.vb` s povoleným odvozením lokálního typu.</span><span class="sxs-lookup"><span data-stu-id="3785a-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3785a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3785a-124">See also</span></span>

- [<span data-ttu-id="3785a-125">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3785a-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3785a-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3785a-126">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="3785a-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3785a-127">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="3785a-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="3785a-128">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="3785a-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="3785a-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="3785a-130">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="3785a-130">Option Infer Statement</span></span>](../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3785a-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="3785a-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3785a-132">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="3785a-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="3785a-133">Stránka Kompilovat, návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3785a-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="3785a-134">-noconfig</span><span class="sxs-lookup"><span data-stu-id="3785a-134">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="3785a-135">Sestavení z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3785a-135">Building from the Command Line</span></span>](building-from-the-command-line.md)
