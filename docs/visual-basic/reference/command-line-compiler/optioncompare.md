---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581419"
---
# <a name="-optioncompare"></a><span data-ttu-id="e3286-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="e3286-102">-optioncompare</span></span>

<span data-ttu-id="e3286-103">Určuje, jak se provádí porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="e3286-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3286-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3286-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="e3286-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3286-105">Remarks</span></span>

<span data-ttu-id="e3286-106">Můžete zadat `-optioncompare` v jednom ze dvou forem: `-optioncompare:binary` pro použití binárního porovnávání řetězců a `-optioncompare:text` pro použití porovnávání textových řetězců.</span><span class="sxs-lookup"><span data-stu-id="e3286-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="e3286-107">Ve výchozím nastavení kompilátor používá `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="e3286-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="e3286-108">V systému Microsoft Windows aktuální znaková stránka Určuje binární pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="e3286-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="e3286-109">Typickým binárním pořadím řazení je následující:</span><span class="sxs-lookup"><span data-stu-id="e3286-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="e3286-110">Textové porovnávání řetězců je založeno na pořadí řazení textu bez rozlišování velkých a malých písmen, které určuje národní prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="e3286-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="e3286-111">Typický způsob řazení textu je následující:</span><span class="sxs-lookup"><span data-stu-id="e3286-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="e3286-112">Nastavení-OptionCompare – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e3286-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="e3286-113">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="e3286-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e3286-114">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e3286-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="e3286-115">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="e3286-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="e3286-116">Upravte hodnotu v poli **Porovnat možnost** .</span><span class="sxs-lookup"><span data-stu-id="e3286-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="e3286-117">Programové nastavení – OptionCompare –</span><span class="sxs-lookup"><span data-stu-id="e3286-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="e3286-118">Viz [příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3286-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3286-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3286-119">Example</span></span>

<span data-ttu-id="e3286-120">Následující kód zkompiluje `ProjFile.vb` a používá porovnávání binárních řetězců.</span><span class="sxs-lookup"><span data-stu-id="e3286-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="e3286-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3286-121">See also</span></span>

- [<span data-ttu-id="e3286-122">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e3286-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e3286-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e3286-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="e3286-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="e3286-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="e3286-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e3286-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="e3286-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="e3286-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e3286-127">Příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="e3286-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="e3286-128">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="e3286-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
