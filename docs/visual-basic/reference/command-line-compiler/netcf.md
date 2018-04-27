---
title: -netcf
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f07fc7988c4329397e464f05d334648e98cb129d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="-netcf"></a><span data-ttu-id="05c1b-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="05c1b-102">-netcf</span></span>
<span data-ttu-id="05c1b-103">Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05c1b-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05c1b-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="05c1b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05c1b-105">Remarks</span></span>  
 <span data-ttu-id="05c1b-106">`-netcf` Možnost způsobí, že Visual Basic – kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)] místo kompletní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05c1b-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="05c1b-107">Funkce jazyka, které je k dispozici pouze v úplném [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] je zakázána.</span><span class="sxs-lookup"><span data-stu-id="05c1b-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="05c1b-108">`-netcf` Možnost je určena pro použití s [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="05c1b-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="05c1b-109">Jazykové funkce zakázal `-netcf` jsou stejné funkce jazyka, nejsou k dispozici v souborech cílit s `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="05c1b-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c1b-110">`-netcf` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="05c1b-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="05c1b-111">`-netcf` Je možnost nastavena při načtení projektu Visual Basic zařízení.</span><span class="sxs-lookup"><span data-stu-id="05c1b-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="05c1b-112">`-netcf` Možnost změní následující funkce jazyka:</span><span class="sxs-lookup"><span data-stu-id="05c1b-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="05c1b-113">[End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) – klíčové slovo, které ukončí provádění programu, je zakázán.</span><span class="sxs-lookup"><span data-stu-id="05c1b-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="05c1b-114">Následující program sestavuje a spouští bez `-netcf` ale selže při kompilaci s `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="05c1b-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="05c1b-115">Rozpoznání s pozdní vazby ve všech formulářů, je zakázán.</span><span class="sxs-lookup"><span data-stu-id="05c1b-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="05c1b-116">Chyby při kompilaci jsou generovány, pokud došlo k rozpoznaný pozdní vazba scénáře.</span><span class="sxs-lookup"><span data-stu-id="05c1b-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="05c1b-117">Následující program sestavuje a spouští bez `-netcf` ale selže při kompilaci s `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="05c1b-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="05c1b-118">[Automaticky](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), a [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifikátory jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="05c1b-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="05c1b-119">Syntaxe [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) příkaz je také upravit tak, aby `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="05c1b-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="05c1b-120">Následující kód ukazuje účinku `-netcf` na kompilace.</span><span class="sxs-lookup"><span data-stu-id="05c1b-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="05c1b-121">Použití klíčových slov jazyka Visual Basic 6.0, které byly odebrány z jazyka Visual Basic generuje jiné chybě při `-netcf` se používá.</span><span class="sxs-lookup"><span data-stu-id="05c1b-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="05c1b-122">Tato akce ovlivní chybové zprávy pro následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="05c1b-122">This affects the error messages for the following keywords:</span></span>  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a><span data-ttu-id="05c1b-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="05c1b-123">Example</span></span>  
 <span data-ttu-id="05c1b-124">Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], pomocí verze mscorlib.dll a souboru Microsoft.VisualBasic.dll najde v adresáři výchozí instalace z [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="05c1b-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="05c1b-125">Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05c1b-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="05c1b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="05c1b-126">See Also</span></span>  
 [<span data-ttu-id="05c1b-127">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="05c1b-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="05c1b-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="05c1b-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="05c1b-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="05c1b-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
