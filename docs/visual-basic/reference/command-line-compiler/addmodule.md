---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2de5fe82f1969a2fdb305d45951d7d698252c0c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816431"
---
# <a name="-addmodule"></a><span data-ttu-id="baf0f-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="baf0f-102">-addmodule</span></span>
<span data-ttu-id="baf0f-103">Způsobí, že kompilátor, aby všechny informace ze zadané soubory, které jsou k dispozici do projektu je aktuálně kompilován typu.</span><span class="sxs-lookup"><span data-stu-id="baf0f-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baf0f-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="baf0f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="baf0f-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="baf0f-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="baf0f-106">Required.</span></span> <span data-ttu-id="baf0f-107">Čárkami oddělený seznam souborů, které obsahují metadata, ale nebude obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="baf0f-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="baf0f-108">Názvy souborů obsahujících mezery by měla být uzavřena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="baf0f-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baf0f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="baf0f-109">Remarks</span></span>  
 <span data-ttu-id="baf0f-110">Souborů uvedené podle `fileList` parametr musí být vytvořená s `-target:module` možnost, nebo jiného kompilátoru ekvivalentem `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="baf0f-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="baf0f-111">Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor v době běhu.</span><span class="sxs-lookup"><span data-stu-id="baf0f-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="baf0f-112">To znamená můžete zadat modulu do libovolného adresáře v době kompilace, ale modul musí být v adresáři aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="baf0f-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="baf0f-113">Pokud není, můžete získat <xref:System.TypeLoadException> chyby.</span><span class="sxs-lookup"><span data-stu-id="baf0f-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="baf0f-114">Pokud zadáte (implicitně nebo explicitně) všechny[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) možností jiných než `-target:module` s `-addmodule`, soubory předáte `-addmodule` se stanou součástí sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="baf0f-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="baf0f-115">Sestavení se vyžaduje pro spuštění výstupního souboru, který obsahuje jednu nebo více souborů se přidá s `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="baf0f-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="baf0f-116">Použití [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Import metadat ze souboru, který obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="baf0f-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baf0f-117">`-addmodule` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="baf0f-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf0f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="baf0f-118">Example</span></span>  
 <span data-ttu-id="baf0f-119">Následující kód vytvoří modul.</span><span class="sxs-lookup"><span data-stu-id="baf0f-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="baf0f-120">Následující kód naimportuje typy modulu.</span><span class="sxs-lookup"><span data-stu-id="baf0f-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="baf0f-121">Při spuštění `t1`, výstupu `802`.</span><span class="sxs-lookup"><span data-stu-id="baf0f-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf0f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="baf0f-122">See also</span></span>

- [<span data-ttu-id="baf0f-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="baf0f-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="baf0f-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baf0f-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="baf0f-125">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baf0f-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="baf0f-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="baf0f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
