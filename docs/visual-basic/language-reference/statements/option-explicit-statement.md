---
title: "Option Explicit – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d39b3d7cf5096e3b263938d32e017eae5708e042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="eb844-102">Option Explicit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb844-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="eb844-103">Vynutí explicitní deklaraci všech proměnných v souboru nebo umožňuje implicitní deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="eb844-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb844-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb844-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="eb844-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="eb844-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="eb844-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="eb844-106">Optional.</span></span> <span data-ttu-id="eb844-107">Umožňuje `Option Explicit` kontrola.</span><span class="sxs-lookup"><span data-stu-id="eb844-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="eb844-108">Pokud `On` nebo `Off` není určena, výchozí hodnota je `On`.</span><span class="sxs-lookup"><span data-stu-id="eb844-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="eb844-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="eb844-109">Optional.</span></span> <span data-ttu-id="eb844-110">Zakáže `Option Explicit` kontrola.</span><span class="sxs-lookup"><span data-stu-id="eb844-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb844-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb844-111">Remarks</span></span>  
 <span data-ttu-id="eb844-112">Když `Option Explicit On` nebo `Option Explicit` se zobrazí v souboru, je potřeba explicitně deklarovat všechny proměnné pomocí `Dim` nebo `ReDim` příkazy.</span><span class="sxs-lookup"><span data-stu-id="eb844-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="eb844-113">Pokud se pokusíte použít nedeklarovaný název proměnné, dojde k chybě při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="eb844-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="eb844-114">`Option Explicit Off` Příkaz umožňuje implicitní deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="eb844-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="eb844-115">Pokud se používá, `Option Explicit` příkazu musí být v souboru před jakékoli jiné příkazy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="eb844-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb844-116">Nastavení `Option Explicit` k `Off` je obecně není vhodné.</span><span class="sxs-lookup"><span data-stu-id="eb844-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="eb844-117">Může chybně název proměnné v jedné nebo více umístění, což by způsobilo neočekávané výsledky při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="eb844-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="eb844-118">Když se nenachází Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb844-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="eb844-119">Pokud zdrojový kód neobsahuje `Option Explicit` příkaz, **Option Explicit** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="eb844-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="eb844-120">Pokud se používá kompilátoru příkazového řádku, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru se používá.</span><span class="sxs-lookup"><span data-stu-id="eb844-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="eb844-121">Chcete-li nastavit možnost explicitní v prostředí IDE</span><span class="sxs-lookup"><span data-stu-id="eb844-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="eb844-122">V **Průzkumníku**, vyberte projektu.</span><span class="sxs-lookup"><span data-stu-id="eb844-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="eb844-123">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="eb844-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="eb844-124">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="eb844-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="eb844-125">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="eb844-125">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="eb844-126">Nastavte hodnotu v **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="eb844-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="eb844-127">Když vytvoříte nový projekt, **Option Explicit** nastavení na **zkompilovat** karta je nastaven na **Option Explicit** nastavení v **VB výchozí**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="eb844-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="eb844-128">Pro přístup k **VB výchozí** v dialogovém **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="eb844-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="eb844-129">V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="eb844-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="eb844-130">Počáteční výchozí nastavení v **VB výchozí** je `On`.</span><span class="sxs-lookup"><span data-stu-id="eb844-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="eb844-131">Chcete-li nastavit možnost explicitní na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="eb844-131">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="eb844-132">Zahrnout [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru v **Vbc –** příkaz.</span><span class="sxs-lookup"><span data-stu-id="eb844-132">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb844-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb844-133">Example</span></span>  
 <span data-ttu-id="eb844-134">Následující příklad používá `Option Explicit` příkaz vynutíte explicitní deklaraci všech proměnných.</span><span class="sxs-lookup"><span data-stu-id="eb844-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="eb844-135">Pokus o použití nedeklarované proměnná způsobí chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="eb844-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eb844-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb844-136">See Also</span></span>  
 [<span data-ttu-id="eb844-137">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb844-137">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="eb844-138">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb844-138">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="eb844-139">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb844-139">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="eb844-140">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb844-140">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="eb844-141">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="eb844-141">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="eb844-142">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="eb844-142">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="eb844-143">/ optionstrict</span><span class="sxs-lookup"><span data-stu-id="eb844-143">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="eb844-144">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb844-144">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
