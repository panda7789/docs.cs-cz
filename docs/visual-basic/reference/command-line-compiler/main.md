---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 5530da4c784346df4a1088998b8d2027feee08e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403158"
---
# <a name="-main"></a><span data-ttu-id="67fb7-102">-main</span><span class="sxs-lookup"><span data-stu-id="67fb7-102">-main</span></span>
<span data-ttu-id="67fb7-103">Určuje třídu nebo modul, který obsahuje `Sub Main` proceduru.</span><span class="sxs-lookup"><span data-stu-id="67fb7-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67fb7-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="67fb7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="67fb7-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="67fb7-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="67fb7-106">Required.</span></span> <span data-ttu-id="67fb7-107">Název třídy nebo modulu, který obsahuje `Sub Main` proceduru, která má být volána při spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="67fb7-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="67fb7-108">Může to být v podobě **: hlavní: modul** nebo **-hlavní: obor názvů. Module**.</span><span class="sxs-lookup"><span data-stu-id="67fb7-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67fb7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67fb7-109">Remarks</span></span>  
 <span data-ttu-id="67fb7-110">Tuto možnost použijte při vytváření spustitelného souboru nebo spustitelného programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="67fb7-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="67fb7-111">Pokud je možnost **-Main** vynechána, kompilátor vyhledá platnou sdílenou `Sub Main` ve všech veřejných třídách a modulech.</span><span class="sxs-lookup"><span data-stu-id="67fb7-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="67fb7-112">Diskuzi o různých formulářích postupu najdete [v tématu hlavní postup v Visual Basic](../../programming-guide/program-structure/main-procedure.md) `Main` .</span><span class="sxs-lookup"><span data-stu-id="67fb7-112">See [Main Procedure in Visual Basic](../../programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="67fb7-113">Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form> , kompilátor poskytuje výchozí `Main` proceduru, která spustí aplikaci, pokud třída nemá žádnou `Main` proceduru.</span><span class="sxs-lookup"><span data-stu-id="67fb7-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="67fb7-114">To umožňuje kompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="67fb7-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="67fb7-115">Nastavení – hlavní v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67fb7-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="67fb7-116">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="67fb7-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="67fb7-117">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="67fb7-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="67fb7-118">Klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="67fb7-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="67fb7-119">Ujistěte se, že není zaškrtnuté políčko **Povolit aplikační rozhraní** .</span><span class="sxs-lookup"><span data-stu-id="67fb7-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="67fb7-120">Upravte hodnotu v poli **spouštěcí objekt** .</span><span class="sxs-lookup"><span data-stu-id="67fb7-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67fb7-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="67fb7-121">Example</span></span>  
 <span data-ttu-id="67fb7-122">Následující kód zkompiluje `T2.vb` a `T3.vb` určí, že `Sub Main` procedura bude nalezena ve `Test2` třídě.</span><span class="sxs-lookup"><span data-stu-id="67fb7-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="67fb7-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="67fb7-123">See also</span></span>

- [<span data-ttu-id="67fb7-124">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="67fb7-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="67fb7-125">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67fb7-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="67fb7-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="67fb7-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="67fb7-127">Hlavní procedura v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67fb7-127">Main Procedure in Visual Basic</span></span>](../../programming-guide/program-structure/main-procedure.md)
