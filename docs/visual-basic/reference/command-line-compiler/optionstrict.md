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
ms.openlocfilehash: da1bd6d3b6746561655a82cd49aa0014563a1d40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652906"
---
# <a name="-optionstrict"></a><span data-ttu-id="7e302-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="7e302-102">-optionstrict</span></span>
<span data-ttu-id="7e302-103">Vynucuje přísné typ sémantiku jako omezení typu implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="7e302-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e302-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e302-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7e302-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7e302-105">Arguments</span></span>  
 <span data-ttu-id="7e302-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7e302-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="7e302-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7e302-107">Optional.</span></span> <span data-ttu-id="7e302-108">`-optionstrict+` Možnost omezuje typ implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="7e302-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="7e302-109">Výchozí hodnota pro tuto možnost je `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="7e302-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="7e302-110">`-optionstrict+` Možnost je stejný jako `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="7e302-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="7e302-111">Můžete použít pro sémantika projektovou typu.</span><span class="sxs-lookup"><span data-stu-id="7e302-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="7e302-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7e302-112">Required.</span></span> <span data-ttu-id="7e302-113">Upozornit, pokud sémantiku striktní jazyk nejsou.</span><span class="sxs-lookup"><span data-stu-id="7e302-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e302-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e302-114">Remarks</span></span>  
 <span data-ttu-id="7e302-115">Když `-optionstrict+` je platná, pouze rozšiřující převody typu můžete provedeny implicitně.</span><span class="sxs-lookup"><span data-stu-id="7e302-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="7e302-116">Implicitní zužující převody typu, jako je například přiřazení `Decimal` typ objektu na objekt typu integer, jsou hlášena jako chyby.</span><span class="sxs-lookup"><span data-stu-id="7e302-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="7e302-117">Chcete-li vygenerovat upozornění pro implicitní zužující převody typu, použijte `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="7e302-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="7e302-118">Použití `-nowarn:numberlist` ignorovat konkrétní varování a `-warnaserror:numberlist` zacházet s konkrétní upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="7e302-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="7e302-119">Chcete-li nastavit - optionstrict v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e302-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="7e302-120">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7e302-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7e302-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="7e302-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="7e302-122">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="7e302-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="7e302-123">Změňte hodnotu v **možnost striktní** pole.</span><span class="sxs-lookup"><span data-stu-id="7e302-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="7e302-124">Chcete-li nastavit - optionstrict prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="7e302-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="7e302-125">V tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7e302-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e302-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e302-126">Example</span></span>  
 <span data-ttu-id="7e302-127">Následující kód zkompiluje `Test.vb` pomocí sémantiky striktní typu.</span><span class="sxs-lookup"><span data-stu-id="7e302-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e302-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e302-128">See Also</span></span>  
 [<span data-ttu-id="7e302-129">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7e302-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7e302-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="7e302-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="7e302-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="7e302-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="7e302-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="7e302-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="7e302-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="7e302-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="7e302-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e302-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="7e302-135">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7e302-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="7e302-136">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="7e302-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="7e302-137">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e302-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
