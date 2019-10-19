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
ms.openlocfilehash: 19ff8cf1dbcdb941e38f23be4cb68d3a5e5b83a8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582583"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="58e05-102">Option Explicit – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58e05-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="58e05-103">Vynutí explicitní deklaraci všech proměnných v souboru nebo umožňuje implicitní deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="58e05-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e05-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="58e05-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="58e05-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="58e05-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="58e05-106">Optional.</span></span> <span data-ttu-id="58e05-107">Povolí `Option Explicit` kontrolu.</span><span class="sxs-lookup"><span data-stu-id="58e05-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="58e05-108">Pokud není zadán `On` nebo `Off`, výchozí hodnota je `On`.</span><span class="sxs-lookup"><span data-stu-id="58e05-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="58e05-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="58e05-109">Optional.</span></span> <span data-ttu-id="58e05-110">Zakáže kontrolu `Option Explicit`.</span><span class="sxs-lookup"><span data-stu-id="58e05-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58e05-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58e05-111">Remarks</span></span>  
 <span data-ttu-id="58e05-112">Když se `Option Explicit On` nebo `Option Explicit` objeví v souboru, musíte explicitně deklarovat všechny proměnné pomocí příkazů `Dim` nebo `ReDim`.</span><span class="sxs-lookup"><span data-stu-id="58e05-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="58e05-113">Pokud se pokusíte použít nedeklarovaný název proměnné, dojde k chybě v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="58e05-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="58e05-114">Příkaz `Option Explicit Off` umožňuje implicitní deklaraci proměnných.</span><span class="sxs-lookup"><span data-stu-id="58e05-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="58e05-115">Při použití musí být příkaz `Option Explicit` uveden v souboru před jakýmkoli jiným příkazy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="58e05-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58e05-116">Nastavení `Option Explicit` na `Off` není většinou dobrým zvykem.</span><span class="sxs-lookup"><span data-stu-id="58e05-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="58e05-117">V jednom nebo více umístěních byste mohli nastavovat navýšení názvu proměnné, což způsobí, že při spuštění programu dojde k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="58e05-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="58e05-118">Pokud není k dispozici příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="58e05-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="58e05-119">Pokud zdrojový kód neobsahuje příkaz `Option Explicit`, je použita **možnost explicitní** nastavení na [stránce kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="58e05-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="58e05-120">Pokud je použit kompilátor příkazového řádku, je použita možnost kompilátoru [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) .</span><span class="sxs-lookup"><span data-stu-id="58e05-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="58e05-121">Nastavení možnosti Explicit v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="58e05-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="58e05-122">V **Průzkumník řešení**vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="58e05-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="58e05-123">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="58e05-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="58e05-124">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="58e05-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="58e05-125">Nastavte hodnotu v poli **explicitní možnosti** .</span><span class="sxs-lookup"><span data-stu-id="58e05-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="58e05-126">Při vytváření nového projektu je **možnost explicitní** nastavení na kartě **kompilovat** nastavena na **možnost explicitní** nastavení v dialogovém okně **výchozí hodnoty VB** .</span><span class="sxs-lookup"><span data-stu-id="58e05-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="58e05-127">Chcete-li získat přístup k dialogovému oknu **výchozí hodnoty VB** , v nabídce **nástroje** klikněte na možnost **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="58e05-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="58e05-128">V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**.</span><span class="sxs-lookup"><span data-stu-id="58e05-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="58e05-129">Počáteční výchozí nastavení ve **výchozích hodnotách VB** je `On`.</span><span class="sxs-lookup"><span data-stu-id="58e05-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="58e05-130">Nastavení možnosti Explicit na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="58e05-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="58e05-131">Do příkazu **Vbc** zahrňte možnost kompilátoru [/OptionExplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) .</span><span class="sxs-lookup"><span data-stu-id="58e05-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e05-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="58e05-132">Example</span></span>  
 <span data-ttu-id="58e05-133">Následující příklad používá příkaz `Option Explicit` k vynucení explicitní deklarace všech proměnných.</span><span class="sxs-lookup"><span data-stu-id="58e05-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="58e05-134">Pokus o použití nedeklarované proměnné způsobí chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="58e05-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="58e05-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58e05-135">See also</span></span>

- [<span data-ttu-id="58e05-136">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="58e05-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="58e05-137">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="58e05-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="58e05-138">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="58e05-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="58e05-139">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="58e05-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="58e05-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="58e05-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="58e05-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="58e05-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="58e05-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="58e05-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="58e05-143">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="58e05-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
