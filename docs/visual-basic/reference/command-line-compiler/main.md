---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337237"
---
# <a name="-main"></a><span data-ttu-id="7d5de-102">-main</span><span class="sxs-lookup"><span data-stu-id="7d5de-102">-main</span></span>
<span data-ttu-id="7d5de-103">Určuje třídu nebo modul, který obsahuje `Sub Main` postup.</span><span class="sxs-lookup"><span data-stu-id="7d5de-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d5de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d5de-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d5de-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d5de-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="7d5de-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7d5de-106">Required.</span></span> <span data-ttu-id="7d5de-107">Název třídy nebo modul, který obsahuje `Sub Main` proceduru, která se má volat při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="7d5de-108">To může být ve tvaru **-main: modul** nebo **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="7d5de-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d5de-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d5de-109">Remarks</span></span>  
 <span data-ttu-id="7d5de-110">Tuto možnost použijte, když vytvoříte spustitelného souboru nebo spustitelný program Windows.</span><span class="sxs-lookup"><span data-stu-id="7d5de-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="7d5de-111">Pokud **– hlavní** možnost vynecháte, kompilátor hledá platný sdílený `Sub Main` v všechny veřejné třídy a moduly.</span><span class="sxs-lookup"><span data-stu-id="7d5de-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="7d5de-112">Zobrazit [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) diskuzi o různých způsobech `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="7d5de-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="7d5de-113">Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí `Main` proceduru, která spustí aplikaci, pokud třída nemá žádné `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="7d5de-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="7d5de-114">To umožňuje kompilaci kódu na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="7d5de-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="7d5de-115">Chcete-li nastavit – hlavní v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d5de-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="7d5de-116">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="7d5de-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7d5de-117">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7d5de-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="7d5de-118">Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="7d5de-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="7d5de-119">Ujistěte se, **Povolit aplikační framework** políčko není zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="7d5de-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="7d5de-120">Upravte hodnotu v **spouštěcí objekt** pole.</span><span class="sxs-lookup"><span data-stu-id="7d5de-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d5de-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d5de-121">Example</span></span>  
 <span data-ttu-id="7d5de-122">Následující kód zkompiluje `T2.vb` a `T3.vb`, určující, který `Sub Main` postup najdete v `Test2` třídy.</span><span class="sxs-lookup"><span data-stu-id="7d5de-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d5de-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d5de-123">See also</span></span>

- [<span data-ttu-id="7d5de-124">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d5de-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7d5de-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d5de-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="7d5de-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7d5de-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="7d5de-127">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d5de-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
