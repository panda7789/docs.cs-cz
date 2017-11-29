---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="2ff55-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="2ff55-102">/optionstrict</span></span>
<span data-ttu-id="2ff55-103">Vynucuje přísné typ sémantiku jako omezení typu implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="2ff55-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ff55-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ff55-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ff55-105">Arguments</span></span>  
 <span data-ttu-id="2ff55-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2ff55-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2ff55-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2ff55-107">Optional.</span></span> <span data-ttu-id="2ff55-108">`/optionstrict+` Možnost omezuje typ implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="2ff55-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="2ff55-109">Výchozí hodnota pro tuto možnost je `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="2ff55-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="2ff55-110">`/optionstrict+` Možnost je stejný jako `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="2ff55-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="2ff55-111">Můžete použít pro sémantika projektovou typu.</span><span class="sxs-lookup"><span data-stu-id="2ff55-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="2ff55-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2ff55-112">Required.</span></span> <span data-ttu-id="2ff55-113">Upozornit, pokud sémantiku striktní jazyk nejsou.</span><span class="sxs-lookup"><span data-stu-id="2ff55-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff55-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ff55-114">Remarks</span></span>  
 <span data-ttu-id="2ff55-115">Když `/optionstrict+` je platná, pouze rozšiřující převody typu můžete provedeny implicitně.</span><span class="sxs-lookup"><span data-stu-id="2ff55-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="2ff55-116">Implicitní zužující převody typu, jako je například přiřazení `Decimal` typ objektu na objekt typu integer, jsou hlášena jako chyby.</span><span class="sxs-lookup"><span data-stu-id="2ff55-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="2ff55-117">Chcete-li vygenerovat upozornění pro implicitní zužující převody typu, použijte `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="2ff55-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="2ff55-118">Použití `/nowarn:numberlist` ignorovat konkrétní varování a `/warnaserror:numberlist` zacházet s konkrétní upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="2ff55-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="2ff55-119">Chcete-li nastavit/optionstrict v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ff55-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="2ff55-120">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="2ff55-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2ff55-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="2ff55-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="2ff55-122">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="2ff55-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="2ff55-123">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="2ff55-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="2ff55-124">Změňte hodnotu v **možnost striktní** pole.</span><span class="sxs-lookup"><span data-stu-id="2ff55-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="2ff55-125">Chcete-li nastavit/optionstrict prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="2ff55-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="2ff55-126">V tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2ff55-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ff55-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ff55-127">Example</span></span>  
 <span data-ttu-id="2ff55-128">Následující kód zkompiluje `Test.vb` pomocí sémantiky striktní typu.</span><span class="sxs-lookup"><span data-stu-id="2ff55-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ff55-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff55-129">See Also</span></span>  
 [<span data-ttu-id="2ff55-130">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2ff55-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2ff55-131">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="2ff55-131">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="2ff55-132">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="2ff55-132">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="2ff55-133">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="2ff55-133">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="2ff55-134">/ nowarn</span><span class="sxs-lookup"><span data-stu-id="2ff55-134">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="2ff55-135">/ warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ff55-135">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="2ff55-136">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2ff55-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="2ff55-137">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="2ff55-137">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="2ff55-138">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ff55-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
