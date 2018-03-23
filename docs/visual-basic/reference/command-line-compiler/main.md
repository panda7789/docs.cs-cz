---
title: -main
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b22b4bb1b6649265eabc02beb6b0145f7c075b27
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-main"></a><span data-ttu-id="56628-102">-main</span><span class="sxs-lookup"><span data-stu-id="56628-102">-main</span></span>
<span data-ttu-id="56628-103">Určuje třídu nebo modul, který obsahuje `Sub Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="56628-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56628-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56628-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="56628-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="56628-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="56628-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="56628-106">Required.</span></span> <span data-ttu-id="56628-107">Název třídy nebo modul, který obsahuje `Sub Main` postupu, která se má volat při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="56628-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="56628-108">To může být ve tvaru **-main: modul** nebo **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="56628-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56628-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56628-109">Remarks</span></span>  
 <span data-ttu-id="56628-110">Tuto možnost použijte, když vytvoříte spustitelného souboru nebo spustitelný program Windows.</span><span class="sxs-lookup"><span data-stu-id="56628-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="56628-111">Pokud **– hlavní** není zadán parametr, kompilátor hledá platný sdílené `Sub Main` v všechny veřejné třídy a moduly.</span><span class="sxs-lookup"><span data-stu-id="56628-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="56628-112">V tématu [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) diskuzi o různé formy `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="56628-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="56628-113">Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí `Main` procedury, která spustí aplikaci, pokud třída nemá žádné `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="56628-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="56628-114">Díky tomu můžete zkompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="56628-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="56628-115">Chcete-li nastavit – hlavní v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56628-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="56628-116">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="56628-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="56628-117">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="56628-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="56628-118">Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="56628-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="56628-119">Zajistěte, aby **Povolit aplikační rozhraní** není zaškrtnuto zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="56628-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="56628-120">Změňte hodnotu v **spouštěcí objekt** pole.</span><span class="sxs-lookup"><span data-stu-id="56628-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56628-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="56628-121">Example</span></span>  
 <span data-ttu-id="56628-122">Následující kód zkompiluje `T2.vb` a `T3.vb`, zadání, `Sub Main` najdete postup ve `Test2` třídy.</span><span class="sxs-lookup"><span data-stu-id="56628-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="56628-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="56628-123">See Also</span></span>  
 [<span data-ttu-id="56628-124">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="56628-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="56628-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56628-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="56628-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="56628-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="56628-127">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56628-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
