---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005505"
---
# <a name="-main"></a><span data-ttu-id="f5cf6-102">-main</span><span class="sxs-lookup"><span data-stu-id="f5cf6-102">-main</span></span>
<span data-ttu-id="f5cf6-103">Určuje třídu nebo modul, který obsahuje `Sub Main` proceduru.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5cf6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5cf6-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5cf6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f5cf6-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="f5cf6-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-106">Required.</span></span> <span data-ttu-id="f5cf6-107">Název třídy nebo modulu, který obsahuje `Sub Main` proceduru, která má být volána při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="f5cf6-108">Může to být v podobě **: hlavní: modul** nebo **-hlavní: obor názvů. Module**.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5cf6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5cf6-109">Remarks</span></span>  
 <span data-ttu-id="f5cf6-110">Tuto možnost použijte při vytváření spustitelného souboru nebo spustitelného programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="f5cf6-111">Pokud je možnost **-Main** vynechána, kompilátor vyhledá platnou sdílenou `Sub Main` ve všech veřejných třídách a modulech.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="f5cf6-112">Diskuzi o různých formulářích `Main` postupu najdete v tématu [hlavní postup v Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) .</span><span class="sxs-lookup"><span data-stu-id="f5cf6-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="f5cf6-113">Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí `Main` proceduru, která spustí aplikaci, pokud třída nemá žádnou `Main` proceduru.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="f5cf6-114">To umožňuje kompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="f5cf6-115">Nastavení – hlavní v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f5cf6-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="f5cf6-116">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f5cf6-117">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="f5cf6-118">Klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="f5cf6-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="f5cf6-119">Ujistěte se, že není zaškrtnuté políčko **Povolit aplikační rozhraní** .</span><span class="sxs-lookup"><span data-stu-id="f5cf6-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="f5cf6-120">Upravte hodnotu v poli **spouštěcí objekt** .</span><span class="sxs-lookup"><span data-stu-id="f5cf6-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cf6-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5cf6-121">Example</span></span>  
 <span data-ttu-id="f5cf6-122">`T2.vb` Následující kód zkompiluje `T3.vb`a určí, že `Sub Main` procedura bude nalezena ve `Test2` třídě.</span><span class="sxs-lookup"><span data-stu-id="f5cf6-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5cf6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5cf6-123">See also</span></span>

- [<span data-ttu-id="f5cf6-124">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f5cf6-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f5cf6-125">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5cf6-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="f5cf6-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f5cf6-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="f5cf6-127">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5cf6-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
