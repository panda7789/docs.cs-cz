---
title: Option Explicit – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: a52900f36ee20e827518598a97c7b7f867bd0d43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586823"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="e1616-102">Option Explicit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1616-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="e1616-103">Vynutí explicitní deklaraci všech proměnných do souboru nebo umožňuje implicitní deklarací proměnných.</span><span class="sxs-lookup"><span data-stu-id="e1616-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1616-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1616-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="e1616-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e1616-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="e1616-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1616-106">Optional.</span></span> <span data-ttu-id="e1616-107">Umožňuje `Option Explicit` kontrolu.</span><span class="sxs-lookup"><span data-stu-id="e1616-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="e1616-108">Pokud `On` nebo `Off` není zadán, výchozí hodnota je `On`.</span><span class="sxs-lookup"><span data-stu-id="e1616-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="e1616-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1616-109">Optional.</span></span> <span data-ttu-id="e1616-110">Zakáže `Option Explicit` kontrolu.</span><span class="sxs-lookup"><span data-stu-id="e1616-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1616-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1616-111">Remarks</span></span>  
 <span data-ttu-id="e1616-112">Když `Option Explicit On` nebo `Option Explicit` se zobrazí v souboru, musíte explicitně deklarovat všechny proměnné pomocí `Dim` nebo `ReDim` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e1616-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="e1616-113">Pokud se pokusíte použít nedeklarovaný název proměnné, dojde k chybě v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e1616-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="e1616-114">`Option Explicit Off` Příkaz umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="e1616-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="e1616-115">Pokud použijete, `Option Explicit` příkazu musí být uvedena v soubor předtím, než všechny ostatní příkazy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e1616-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1616-116">Nastavení `Option Explicit` k `Off` není obvykle vhodné.</span><span class="sxs-lookup"><span data-stu-id="e1616-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="e1616-117">Název proměnné v jedné nebo více umístění, což způsobilo neočekávané výsledky při spuštění programu může mít překlep.</span><span class="sxs-lookup"><span data-stu-id="e1616-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="e1616-118">Pokud není k dispozici Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="e1616-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="e1616-119">Pokud zdrojový kód neobsahuje `Option Explicit` příkazu **Option Explicit** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="e1616-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="e1616-120">Pokud se používá kompilátor příkazového řádku, [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru je používá.</span><span class="sxs-lookup"><span data-stu-id="e1616-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="e1616-121">Nastavení Option Explicit v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="e1616-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="e1616-122">V **Průzkumníka řešení**, vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="e1616-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="e1616-123">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e1616-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e1616-124">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="e1616-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e1616-125">Nastavte hodnotu **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="e1616-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="e1616-126">Když vytvoříte nový projekt **Option Explicit** nastavení na **kompilaci** karty nastavená na **Option Explicit** nastavení **VB výchozí**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e1616-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="e1616-127">Pro přístup **VB výchozí** dialogovém okně **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="e1616-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="e1616-128">V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="e1616-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="e1616-129">Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je `On`.</span><span class="sxs-lookup"><span data-stu-id="e1616-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="e1616-130">Chcete-li nastavit na příkazovém řádku Option Explicit</span><span class="sxs-lookup"><span data-stu-id="e1616-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="e1616-131">Zahrnout [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) – možnost kompilátoru v **Vbc –** příkazu.</span><span class="sxs-lookup"><span data-stu-id="e1616-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1616-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1616-132">Example</span></span>  
 <span data-ttu-id="e1616-133">V následujícím příkladu `Option Explicit` příkaz vynutit explicitní deklaraci všech proměnných.</span><span class="sxs-lookup"><span data-stu-id="e1616-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="e1616-134">Pokus o použití Nedeklarovaná proměnná způsobí chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e1616-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e1616-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1616-135">See also</span></span>
- [<span data-ttu-id="e1616-136">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="e1616-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="e1616-137">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="e1616-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="e1616-138">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="e1616-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="e1616-139">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="e1616-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="e1616-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="e1616-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="e1616-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e1616-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="e1616-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="e1616-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="e1616-143">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="e1616-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
