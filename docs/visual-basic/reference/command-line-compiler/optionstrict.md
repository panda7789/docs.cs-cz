---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583079"
---
# <a name="-optionstrict"></a><span data-ttu-id="06322-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="06322-102">-optionstrict</span></span>

<span data-ttu-id="06322-103">Vynutila striktní sémantiku typu pro omezení implicitních převodů typu.</span><span class="sxs-lookup"><span data-stu-id="06322-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="06322-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06322-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="06322-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="06322-105">Arguments</span></span>

<span data-ttu-id="06322-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="06322-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="06322-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="06322-107">Optional.</span></span> <span data-ttu-id="06322-108">Možnost `-optionstrict+` omezuje implicitní převod typu.</span><span class="sxs-lookup"><span data-stu-id="06322-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="06322-109">Výchozí hodnota pro tuto možnost je `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="06322-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="06322-110">Možnost `-optionstrict+` je stejná jako `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="06322-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="06322-111">Pro sémantiku typu lze použít obojí.</span><span class="sxs-lookup"><span data-stu-id="06322-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="06322-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="06322-112">Required.</span></span> <span data-ttu-id="06322-113">Zobrazit upozornění, pokud není respektována striktní sémantika jazyka</span><span class="sxs-lookup"><span data-stu-id="06322-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="06322-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06322-114">Remarks</span></span>

<span data-ttu-id="06322-115">Pokud je platný `-optionstrict+`, lze implicitně převést pouze rozšiřující převody typů.</span><span class="sxs-lookup"><span data-stu-id="06322-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="06322-116">Implicitně zúžené převody typů, jako je například přiřazení objektu typu `Decimal` k objektu typu Integer, jsou hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="06322-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="06322-117">Chcete-li generovat upozornění pro implicitní zužující převody typů, použijte `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="06322-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="06322-118">Pomocí `-nowarn:numberlist` můžete ignorovat konkrétní upozornění a `-warnaserror:numberlist` pro považovat konkrétní upozornění za chyby.</span><span class="sxs-lookup"><span data-stu-id="06322-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="06322-119">Nastavení-OptionStrict – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="06322-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="06322-120">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="06322-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="06322-121">V nabídce **projekt** klikněte na příkaz **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="06322-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="06322-122">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="06322-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="06322-123">Upravte hodnotu v poli **Option Strict** .</span><span class="sxs-lookup"><span data-stu-id="06322-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="06322-124">Programové nastavení – OptionStrict –</span><span class="sxs-lookup"><span data-stu-id="06322-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="06322-125">Viz [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="06322-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="06322-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="06322-126">Example</span></span>

<span data-ttu-id="06322-127">Následující kód zkompiluje `Test.vb` pomocí sémantiky striktního typu.</span><span class="sxs-lookup"><span data-stu-id="06322-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="06322-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06322-128">See also</span></span>

- [<span data-ttu-id="06322-129">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="06322-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="06322-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="06322-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="06322-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="06322-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="06322-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="06322-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="06322-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="06322-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="06322-134">-warnaserror – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06322-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="06322-135">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="06322-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="06322-136">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="06322-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="06322-137">Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti</span><span class="sxs-lookup"><span data-stu-id="06322-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
