---
title: Vstupní bod (F#)
description: 'Zjistěte, jak nastavit vstupní bod programu F #, který se zkompiluje jako spustitelného souboru, kde oficiálně spustí provádění.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 42e5fe7f85285f990ef92e9791ed5bdfacb85059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="entry-point"></a><span data-ttu-id="05706-103">Vstupní bod</span><span class="sxs-lookup"><span data-stu-id="05706-103">Entry Point</span></span>

<span data-ttu-id="05706-104">Toto téma popisuje metodu, můžete použít k nastavení vstupní bod programu F #.</span><span class="sxs-lookup"><span data-stu-id="05706-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="05706-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05706-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="05706-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05706-106">Remarks</span></span>
<span data-ttu-id="05706-107">V předchozích syntaxi *vazba funkce umožňují* je definice funkce v `let` vazby.</span><span class="sxs-lookup"><span data-stu-id="05706-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="05706-108">Vstupní bod k programu, který se zkompiluje jako spustitelný soubor je, kde oficiálně spustí provádění.</span><span class="sxs-lookup"><span data-stu-id="05706-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="05706-109">Zadejte vstupní bod aplikace F # s použitím `EntryPoint` atribut program `main` funkce.</span><span class="sxs-lookup"><span data-stu-id="05706-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="05706-110">Tato funkce (vytvořili pomocí `let` vazba) musí být poslední funkce v poslední zkompilovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="05706-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="05706-111">Poslední zkompilovaný soubor je posledního souboru v projektu nebo posledního souboru, který je předán do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="05706-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="05706-112">Funkce vstupního bodu má typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="05706-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="05706-113">Argumenty zadat na příkazovém řádku `main` funkce v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="05706-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="05706-114">První prvek pole je první argument; název spustitelného souboru není součástí pole, protože je v některých dalších jazycích.</span><span class="sxs-lookup"><span data-stu-id="05706-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="05706-115">Návratová hodnota slouží jako kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="05706-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="05706-116">Nula obvykle označuje úspěch; nenulové hodnoty udávající chybu.</span><span class="sxs-lookup"><span data-stu-id="05706-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="05706-117">Neexistuje žádné názvů pro zvláštní význam nenulové hodnoty návratových kódů; významy návratových kódů jsou specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="05706-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="05706-118">Následující příklad ukazuje jednoduchý `main` funkce.</span><span class="sxs-lookup"><span data-stu-id="05706-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="05706-119">Při spuštění tohoto kódu s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="05706-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="05706-120">Implicitní vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="05706-120">Implicit Entry Point</span></span>
<span data-ttu-id="05706-121">Když program neobsahuje žádné **EntryPoint** atribut, který explicitně určuje vstupní bod, vazby nejvyšší úrovně v posledního souboru mají být zkompilovány, do se používají jako vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="05706-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="05706-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="05706-122">See Also</span></span>
[<span data-ttu-id="05706-123">Funkce</span><span class="sxs-lookup"><span data-stu-id="05706-123">Functions</span></span>](index.md)

[<span data-ttu-id="05706-124">Vazby let</span><span class="sxs-lookup"><span data-stu-id="05706-124">let Bindings</span></span>](let-bindings.md)
