---
title: /main
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2697b837a536b1b879196bd10843a2b76314747a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="main"></a><span data-ttu-id="90026-102">/main</span><span class="sxs-lookup"><span data-stu-id="90026-102">/main</span></span>
<span data-ttu-id="90026-103">Určuje třídu nebo modul, který obsahuje `Sub Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="90026-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90026-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90026-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="90026-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="90026-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="90026-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="90026-106">Required.</span></span> <span data-ttu-id="90026-107">Úplné kvalifikace ke třídě nebo modul, který obsahuje `Sub Main` postupu, která se má volat při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="90026-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="90026-108">To může být ve tvaru **/main:module** nebo **/main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="90026-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90026-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90026-109">Remarks</span></span>  
 <span data-ttu-id="90026-110">Tuto možnost použijte, když vytvoříte spustitelného souboru nebo spustitelný program Windows.</span><span class="sxs-lookup"><span data-stu-id="90026-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="90026-111">Pokud **/main** není zadán parametr, kompilátor hledá platný sdílené `Sub Main` v všechny veřejné třídy a moduly.</span><span class="sxs-lookup"><span data-stu-id="90026-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="90026-112">V tématu [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) diskuzi o různé formy `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="90026-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="90026-113">Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí `Main` procedury, která spustí aplikaci, pokud třída nemá žádné `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="90026-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="90026-114">Díky tomu můžete zkompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="90026-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="90026-115">Chcete-li nastavit/Main v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="90026-115">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="90026-116">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="90026-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="90026-117">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="90026-117">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="90026-118">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="90026-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="90026-119">Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="90026-119">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="90026-120">Zajistěte, aby **Povolit aplikační rozhraní** není zaškrtnuto zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="90026-120">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="90026-121">Změňte hodnotu v **spouštěcí objekt** pole.</span><span class="sxs-lookup"><span data-stu-id="90026-121">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90026-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="90026-122">Example</span></span>  
 <span data-ttu-id="90026-123">Následující kód zkompiluje `T2.vb` a `T3.vb`, zadání, `Sub Main` najdete postup ve `Test2` třídy.</span><span class="sxs-lookup"><span data-stu-id="90026-123">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="90026-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="90026-124">See Also</span></span>  
 [<span data-ttu-id="90026-125">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="90026-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="90026-126">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90026-126">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="90026-127">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="90026-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="90026-128">NIB: verze jazyka Visual Basic Hello, World</span><span class="sxs-lookup"><span data-stu-id="90026-128">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="90026-129">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90026-129">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
