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
ms.openlocfilehash: 82a0adc9e821df3a789cf19e798d4bad9e9a69e3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-netcf"></a><span data-ttu-id="1a122-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="1a122-102">-netcf</span></span>
<span data-ttu-id="1a122-103">Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a122-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a122-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a122-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a122-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a122-105">Remarks</span></span>  
 <span data-ttu-id="1a122-106">`-netcf` Možnost příčiny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru k cíli [!INCLUDE[Compact](~/includes/compact-md.md)] místo kompletní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a122-106">The `-netcf` option causes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1a122-107">Funkce jazyka, které je k dispozici pouze v úplném [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] je zakázána.</span><span class="sxs-lookup"><span data-stu-id="1a122-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="1a122-108">`-netcf` Možnost je určena pro použití s [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="1a122-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="1a122-109">Jazykové funkce zakázal `-netcf` jsou stejné funkce jazyka, nejsou k dispozici v souborech cílit s `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="1a122-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a122-110">`-netcf` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="1a122-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="1a122-111">`-netcf` Když je možnost nastavena [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] načtení projektu zařízení.</span><span class="sxs-lookup"><span data-stu-id="1a122-111">The `-netcf` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="1a122-112">`-netcf` Možnost změní následující funkce jazyka:</span><span class="sxs-lookup"><span data-stu-id="1a122-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="1a122-113">[End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) – klíčové slovo, které ukončí provádění programu, je zakázán.</span><span class="sxs-lookup"><span data-stu-id="1a122-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="1a122-114">Následující program sestavuje a spouští bez `-netcf` ale selže při kompilaci s `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="1a122-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="1a122-115">Rozpoznání s pozdní vazby ve všech formulářů, je zakázán.</span><span class="sxs-lookup"><span data-stu-id="1a122-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="1a122-116">Chyby při kompilaci jsou generovány, pokud došlo k rozpoznaný pozdní vazba scénáře.</span><span class="sxs-lookup"><span data-stu-id="1a122-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="1a122-117">Následující program sestavuje a spouští bez `-netcf` ale selže při kompilaci s `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="1a122-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="1a122-118">[Automaticky](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), a [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifikátory jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="1a122-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="1a122-119">Syntaxe [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) příkaz je také upravit tak, aby `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="1a122-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="1a122-120">Následující kód ukazuje účinku `-netcf` na kompilace.</span><span class="sxs-lookup"><span data-stu-id="1a122-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="1a122-121">Použití klíčových slov jazyka Visual Basic 6.0, které byly odebrány z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generuje jiné chybě při `-netcf` se používá.</span><span class="sxs-lookup"><span data-stu-id="1a122-121">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="1a122-122">Tato akce ovlivní chybové zprávy pro následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="1a122-122">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1a122-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a122-123">Example</span></span>  
 <span data-ttu-id="1a122-124">Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], pomocí verze mscorlib.dll a souboru Microsoft.VisualBasic.dll najde v adresáři výchozí instalace z [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="1a122-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="1a122-125">Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a122-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a122-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a122-126">See Also</span></span>  
 [<span data-ttu-id="1a122-127">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="1a122-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1a122-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="1a122-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1a122-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="1a122-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
