---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 987a948d739f6b9e8e5a3e8fc6eadbfd60003723
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203055"
---
# <a name="-netcf"></a><span data-ttu-id="0d2cd-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="0d2cd-102">-netcf</span></span>
<span data-ttu-id="0d2cd-103">Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d2cd-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d2cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d2cd-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="0d2cd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d2cd-105">Remarks</span></span>  
 <span data-ttu-id="0d2cd-106">`-netcf` Možnost způsobí, že kompilátor jazyka Visual Basic k cíli [!INCLUDE[Compact](~/includes/compact-md.md)] místo úplné [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d2cd-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0d2cd-107">Funkce jazyka, které je k dispozici pouze v úplném [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="0d2cd-108">`-netcf` Možnost je určena pro použití s [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="0d2cd-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="0d2cd-109">Funkce jazyka zakázal `-netcf` jsou stejné funkce jazyka, není k dispozici v souborech cílem `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d2cd-110">`-netcf` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="0d2cd-111">`-netcf` Nastavena možnost při načtení projektu Visual Basic zařízení.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="0d2cd-112">`-netcf` Možnost změní následující funkce jazyka:</span><span class="sxs-lookup"><span data-stu-id="0d2cd-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="0d2cd-113">[End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) klíčové slovo ukončí provádění programu, je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="0d2cd-114">Následující program zkompiluje a spustí bez `-netcf` , ale selže v době kompilace s `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]  
  
-   <span data-ttu-id="0d2cd-115">Pozdní vazba v všechny formuláře je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="0d2cd-116">Chyby při kompilaci jsou generovány, pokud nedojde k rozpoznaný scénáře pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="0d2cd-117">Následující program zkompiluje a spustí bez `-netcf` , ale selže v době kompilace s `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]  
  
-   <span data-ttu-id="0d2cd-118">[Automaticky](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), a [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifikátory jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="0d2cd-119">Syntaxe [deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) příkaz také upraví tak `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="0d2cd-120">Následující kód demonstruje účinek `-netcf` v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]  
  
-   <span data-ttu-id="0d2cd-121">Pomocí klíčových slov jazyka Visual Basic 6.0, které byly odebrány z jazyka Visual Basic generuje různé chyby při `-netcf` se používá.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="0d2cd-122">Tato akce ovlivní chybové zprávy pro následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="0d2cd-122">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0d2cd-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d2cd-123">Example</span></span>  
 <span data-ttu-id="0d2cd-124">Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], použití verze knihovny mscorlib.dll a Microsoft.VisualBasic.dll součástí výchozí instalační adresář [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C:.</span><span class="sxs-lookup"><span data-stu-id="0d2cd-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="0d2cd-125">Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d2cd-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d2cd-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d2cd-126">See also</span></span>
- [<span data-ttu-id="0d2cd-127">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0d2cd-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0d2cd-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0d2cd-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="0d2cd-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="0d2cd-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
