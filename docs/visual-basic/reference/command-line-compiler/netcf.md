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
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397472"
---
# <a name="-netcf"></a><span data-ttu-id="9ca15-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="9ca15-102">-netcf</span></span>

<span data-ttu-id="9ca15-103">Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="9ca15-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ca15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca15-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="9ca15-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ca15-105">Remarks</span></span>

<span data-ttu-id="9ca15-106">`-netcf`Možnost způsobí, že kompilátor Visual Basic cílí na prostředí .NET Compact Framework, nikoli na úplný .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ca15-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="9ca15-107">Funkce jazyka, které jsou k dispozici pouze v plném .NET Framework, jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="9ca15-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="9ca15-108">`-netcf`Možnost je navržena pro použití s parametrem [-SdkPath –](sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="9ca15-108">The `-netcf` option is designed to be used with [-sdkpath](sdkpath.md).</span></span> <span data-ttu-id="9ca15-109">Funkce jazyka zakázané nástrojem `-netcf` jsou stejné funkce jazyka, které nejsou k dispozici v souborech cílících na `-sdkpath` .</span><span class="sxs-lookup"><span data-stu-id="9ca15-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="9ca15-110">Tato `-netcf` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9ca15-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="9ca15-111">`-netcf`Možnost je nastavena při načtení projektu Visual Basic zařízení.</span><span class="sxs-lookup"><span data-stu-id="9ca15-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="9ca15-112">`-netcf`Možnost změní následující jazykové funkce:</span><span class="sxs-lookup"><span data-stu-id="9ca15-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="9ca15-113">Klíčové slovo [End \<keyword> příkaz](../../language-reference/statements/end-keyword-statement.md) , který ukončí provádění programu, je zakázané.</span><span class="sxs-lookup"><span data-stu-id="9ca15-113">The [End \<keyword> Statement](../../language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="9ca15-114">Následující program zkompiluje a spustí bez `-netcf` chyby v době kompilace s `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9ca15-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="9ca15-115">Pozdní vazba je ve všech formulářích zakázaná.</span><span class="sxs-lookup"><span data-stu-id="9ca15-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="9ca15-116">Chyby při kompilaci jsou generovány při zjištění rozpoznaných scénářů s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="9ca15-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="9ca15-117">Následující program zkompiluje a spustí bez `-netcf` chyby v době kompilace s `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9ca15-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="9ca15-118">Modifikátory [auto](../../language-reference/modifiers/auto.md), [ANSI](../../language-reference/modifiers/ansi.md)a [Unicode](../../language-reference/modifiers/unicode.md) jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="9ca15-118">The [Auto](../../language-reference/modifiers/auto.md), [Ansi](../../language-reference/modifiers/ansi.md), and [Unicode](../../language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="9ca15-119">Syntaxe [příkazu Declare](../../language-reference/statements/declare-statement.md) je také změněna na `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` .</span><span class="sxs-lookup"><span data-stu-id="9ca15-119">The syntax of the [Declare Statement](../../language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="9ca15-120">Následující kód ukazuje účinek `-netcf` na kompilaci.</span><span class="sxs-lookup"><span data-stu-id="9ca15-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="9ca15-121">Pomocí klíčových slov Visual Basic 6,0 odebraných z Visual Basic vygeneruje při použití jinou chybu `-netcf` .</span><span class="sxs-lookup"><span data-stu-id="9ca15-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="9ca15-122">To má vliv na chybové zprávy pro následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="9ca15-122">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="9ca15-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ca15-123">Example</span></span>

<span data-ttu-id="9ca15-124">Následující kód `Myfile.vb` se zkompiluje s prostředí .NET Compact Framework pomocí verzí knihovny mscorlib. dll a Microsoft. VisualBasic. dll, která se nachází ve výchozím instalačním adresáři prostředí .NET Compact Framework na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="9ca15-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="9ca15-125">Obvykle byste použili nejnovější verzi prostředí .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="9ca15-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="9ca15-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ca15-126">See also</span></span>

- [<span data-ttu-id="9ca15-127">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="9ca15-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9ca15-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="9ca15-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="9ca15-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="9ca15-129">-sdkpath</span></span>](sdkpath.md)
