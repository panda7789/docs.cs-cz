---
title: "Vstupní bod (F#)"
description: "Zjistěte, jak nastavit vstupní bod programu F #, který se zkompiluje jako spustitelného souboru, kde oficiálně spustí provádění."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="776e6-104">Vstupní bod</span><span class="sxs-lookup"><span data-stu-id="776e6-104">Entry Point</span></span>

<span data-ttu-id="776e6-105">Toto téma popisuje metodu, můžete použít k nastavení vstupní bod programu F #.</span><span class="sxs-lookup"><span data-stu-id="776e6-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="776e6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="776e6-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="776e6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="776e6-107">Remarks</span></span>
<span data-ttu-id="776e6-108">V předchozích syntaxi *vazba funkce umožňují* je definice funkce v `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="776e6-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="776e6-109">Vstupní bod k programu, který se zkompiluje jako spustitelný soubor je, kde oficiálně spustí provádění.</span><span class="sxs-lookup"><span data-stu-id="776e6-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="776e6-110">Zadejte vstupní bod aplikace F # s použitím `EntryPoint` atribut program `main` funkce.</span><span class="sxs-lookup"><span data-stu-id="776e6-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="776e6-111">Tato funkce (vytvořili pomocí `let` vazba) musí být poslední funkce v poslední zkompilovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="776e6-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="776e6-112">Poslední zkompilovaný soubor je posledního souboru v projektu nebo posledního souboru, který je předán do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="776e6-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="776e6-113">Funkce vstupního bodu má typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="776e6-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="776e6-114">Argumenty zadat na příkazovém řádku `main` funkce v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="776e6-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="776e6-115">První prvek pole je první argument; název spustitelného souboru není součástí pole, protože je v některých dalších jazycích.</span><span class="sxs-lookup"><span data-stu-id="776e6-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="776e6-116">Návratová hodnota slouží jako kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="776e6-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="776e6-117">Nula obvykle označuje úspěch; nenulové hodnoty udávající chybu.</span><span class="sxs-lookup"><span data-stu-id="776e6-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="776e6-118">Neexistuje žádné názvů pro zvláštní význam nenulové hodnoty návratových kódů; významy návratových kódů jsou specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="776e6-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="776e6-119">Následující příklad ukazuje jednoduchý `main` funkce.</span><span class="sxs-lookup"><span data-stu-id="776e6-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="776e6-120">Při spuštění tohoto kódu s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="776e6-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="776e6-121">Implicitní vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="776e6-121">Implicit Entry Point</span></span>
<span data-ttu-id="776e6-122">Když program neobsahuje žádné **EntryPoint** atribut, který explicitně určuje vstupní bod, vazby nejvyšší úrovně v posledního souboru mají být zkompilovány, do se používají jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="776e6-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="776e6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="776e6-123">See Also</span></span>
[<span data-ttu-id="776e6-124">Funkce</span><span class="sxs-lookup"><span data-stu-id="776e6-124">Functions</span></span>](index.md)

[<span data-ttu-id="776e6-125">let – vazby</span><span class="sxs-lookup"><span data-stu-id="776e6-125">let Bindings</span></span>](let-bindings.md)
