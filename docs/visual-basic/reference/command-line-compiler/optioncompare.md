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
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400552"
---
# <a name="-optioncompare"></a><span data-ttu-id="4ee42-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4ee42-102">-optioncompare</span></span>

<span data-ttu-id="4ee42-103">Určuje, jak se provádí porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="4ee42-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ee42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ee42-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="4ee42-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ee42-105">Remarks</span></span>

<span data-ttu-id="4ee42-106">Můžete zadat `-optioncompare` v jednom ze dvou forem: `-optioncompare:binary` Chcete-li použít porovnávání binárních řetězců a `-optioncompare:text` použít porovnávání textových řetězců.</span><span class="sxs-lookup"><span data-stu-id="4ee42-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="4ee42-107">Ve výchozím nastavení používá kompilátor `-optioncompare:binary` .</span><span class="sxs-lookup"><span data-stu-id="4ee42-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="4ee42-108">V systému Microsoft Windows aktuální znaková stránka Určuje binární pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="4ee42-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="4ee42-109">Typickým binárním pořadím řazení je následující:</span><span class="sxs-lookup"><span data-stu-id="4ee42-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="4ee42-110">Textové porovnávání řetězců je založeno na pořadí řazení textu bez rozlišování velkých a malých písmen, které určuje národní prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="4ee42-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="4ee42-111">Typický způsob řazení textu je následující:</span><span class="sxs-lookup"><span data-stu-id="4ee42-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="4ee42-112">Nastavení-OptionCompare – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ee42-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="4ee42-113">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="4ee42-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4ee42-114">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4ee42-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="4ee42-115">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="4ee42-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="4ee42-116">Upravte hodnotu v poli **Porovnat možnost** .</span><span class="sxs-lookup"><span data-stu-id="4ee42-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="4ee42-117">Programové nastavení – OptionCompare –</span><span class="sxs-lookup"><span data-stu-id="4ee42-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="4ee42-118">Viz [příkaz Option Compare](../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4ee42-118">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="4ee42-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ee42-119">Example</span></span>

<span data-ttu-id="4ee42-120">Následující kód kompiluje `ProjFile.vb` a používá porovnávání binárních řetězců.</span><span class="sxs-lookup"><span data-stu-id="4ee42-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="4ee42-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ee42-121">See also</span></span>

- [<span data-ttu-id="4ee42-122">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="4ee42-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4ee42-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4ee42-123">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="4ee42-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4ee42-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="4ee42-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="4ee42-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="4ee42-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="4ee42-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4ee42-127">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="4ee42-127">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="4ee42-128">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="4ee42-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
