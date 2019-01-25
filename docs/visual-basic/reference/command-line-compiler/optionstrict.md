---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: fdea071f8c41f2e707d10c96c8b6ab1fbb44bad0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733308"
---
# <a name="-optionstrict"></a><span data-ttu-id="77b86-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="77b86-102">-optionstrict</span></span>
<span data-ttu-id="77b86-103">Vynutí sémantiku přísného typu pro omezení převodů implicitních typů.</span><span class="sxs-lookup"><span data-stu-id="77b86-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77b86-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="77b86-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="77b86-105">Arguments</span></span>  
 <span data-ttu-id="77b86-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="77b86-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="77b86-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="77b86-107">Optional.</span></span> <span data-ttu-id="77b86-108">`-optionstrict+` Omezí implicitní převod typu.</span><span class="sxs-lookup"><span data-stu-id="77b86-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="77b86-109">Výchozí hodnota pro tuto možnost je `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="77b86-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="77b86-110">`-optionstrict+` Možnost je stejný jako `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="77b86-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="77b86-111">Můžete je používat pro typ povolující sémantiku.</span><span class="sxs-lookup"><span data-stu-id="77b86-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="77b86-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="77b86-112">Required.</span></span> <span data-ttu-id="77b86-113">Zobrazit upozornění, pokud není respektována striktní sémantika jazyka.</span><span class="sxs-lookup"><span data-stu-id="77b86-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77b86-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77b86-114">Remarks</span></span>  
 <span data-ttu-id="77b86-115">Když `-optionstrict+` platí, pouze rozšiřující převody typu lze implicitně.</span><span class="sxs-lookup"><span data-stu-id="77b86-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="77b86-116">Implicitní zužující převody typů, jako je například přiřazení `Decimal` zadejte objekt na objekt typu celé číslo, které jsou hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="77b86-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="77b86-117">Chcete-li generovat upozornění pro implicitní zužující převody typů, použijte `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="77b86-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="77b86-118">Použití `-nowarn:numberlist` ignorovat konkrétní varování a `-warnaserror:numberlist` považovat konkrétní upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="77b86-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="77b86-119">Chcete-li nastavit - optionstrict v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77b86-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="77b86-120">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="77b86-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="77b86-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="77b86-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="77b86-122">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="77b86-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="77b86-123">Upravte hodnotu v **Option Strict** pole.</span><span class="sxs-lookup"><span data-stu-id="77b86-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="77b86-124">Chcete-li nastavit - optionstrict prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="77b86-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="77b86-125">Zobrazit [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b86-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77b86-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="77b86-126">Example</span></span>  
 <span data-ttu-id="77b86-127">Následující kód zkompiluje `Test.vb` pomocí sémantiku přísného typu.</span><span class="sxs-lookup"><span data-stu-id="77b86-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="77b86-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77b86-128">See also</span></span>
- [<span data-ttu-id="77b86-129">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="77b86-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="77b86-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="77b86-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="77b86-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="77b86-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="77b86-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="77b86-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="77b86-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="77b86-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="77b86-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b86-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="77b86-135">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="77b86-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="77b86-136">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="77b86-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="77b86-137">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="77b86-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
