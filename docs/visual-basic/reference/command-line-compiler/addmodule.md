---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002414"
---
# <a name="-addmodule"></a><span data-ttu-id="466b1-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="466b1-102">-addmodule</span></span>
<span data-ttu-id="466b1-103">Způsobí, že kompilátor zpřístupní všechny informace o typech ze zadaných souborů pro projekt, který právě kompilujete.</span><span class="sxs-lookup"><span data-stu-id="466b1-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="466b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="466b1-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="466b1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="466b1-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="466b1-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="466b1-106">Required.</span></span> <span data-ttu-id="466b1-107">Čárkami oddělený seznam souborů, které obsahují metadata, ale neobsahují manifesty sestavení.</span><span class="sxs-lookup"><span data-stu-id="466b1-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="466b1-108">Názvy souborů, které obsahují mezery, by měly být obklopené uvozovkami ("").</span><span class="sxs-lookup"><span data-stu-id="466b1-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="466b1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="466b1-109">Remarks</span></span>  
 <span data-ttu-id="466b1-110">Soubory uvedené parametrem `fileList` musí být vytvořeny s možností `-target:module` nebo s jiným kompilátorem ekvivalentním `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="466b1-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="466b1-111">Všechny moduly přidané pomocí `-addmodule` musí být ve stejném adresáři jako výstupní soubor v době běhu.</span><span class="sxs-lookup"><span data-stu-id="466b1-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="466b1-112">To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="466b1-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="466b1-113">Pokud to tak není, zobrazí se chyba <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="466b1-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="466b1-114">Pokud zadáte (implicitně nebo explicitně) možnost libovolný[cíl (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) kromě `-target:module` s `-addmodule`, soubory, které předáte do `-addmodule`, se stanou součástí sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="466b1-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="466b1-115">Pro spuštění výstupního souboru, který obsahuje jeden nebo více souborů přidaných s `-addmodule`, je vyžadováno sestavení.</span><span class="sxs-lookup"><span data-stu-id="466b1-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="466b1-116">Použijte [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pro import metadat ze souboru, který obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="466b1-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="466b1-117">Možnost `-addmodule` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="466b1-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="466b1-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="466b1-118">Example</span></span>  
 <span data-ttu-id="466b1-119">Následující kód vytvoří modul.</span><span class="sxs-lookup"><span data-stu-id="466b1-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="466b1-120">Následující kód importuje typy modulu.</span><span class="sxs-lookup"><span data-stu-id="466b1-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="466b1-121">Když spustíte `t1`, výstup IT `802`.</span><span class="sxs-lookup"><span data-stu-id="466b1-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="466b1-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="466b1-122">See also</span></span>

- [<span data-ttu-id="466b1-123">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="466b1-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="466b1-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="466b1-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="466b1-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="466b1-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="466b1-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="466b1-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
