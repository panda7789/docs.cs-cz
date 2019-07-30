---
title: Vstupní bod
description: Naučte se, jak nastavit vstupní bod na F# program, který je kompilován jako spustitelný soubor, kde se spouští formulář pro spuštění.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630517"
---
# <a name="entry-point"></a><span data-ttu-id="13beb-103">Vstupní bod</span><span class="sxs-lookup"><span data-stu-id="13beb-103">Entry Point</span></span>

<span data-ttu-id="13beb-104">Toto téma popisuje metodu, kterou použijete k nastavení vstupního bodu na F# program.</span><span class="sxs-lookup"><span data-stu-id="13beb-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="13beb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13beb-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="13beb-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13beb-106">Remarks</span></span>

<span data-ttu-id="13beb-107">V předchozí syntaxi je *let-Function-Binding* definicí funkce ve `let` vazbě.</span><span class="sxs-lookup"><span data-stu-id="13beb-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="13beb-108">Vstupním bodem programu, který je kompilován jako spustitelný soubor, je místo, kde se spouští formulář pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="13beb-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="13beb-109">Vstupní bod do F# aplikace určíte tak, že použijete `EntryPoint` atribut `main` pro funkci programu.</span><span class="sxs-lookup"><span data-stu-id="13beb-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="13beb-110">Tato funkce (vytvořená pomocí `let` vazby) musí být poslední funkcí v posledním kompilovaném souboru.</span><span class="sxs-lookup"><span data-stu-id="13beb-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="13beb-111">Poslední kompilovaný soubor je poslední soubor v projektu nebo poslední soubor, který je předán do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="13beb-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="13beb-112">Funkce vstupního bodu má typ `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="13beb-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="13beb-113">Argumenty uvedené na příkazovém řádku jsou předány `main` funkci v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="13beb-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="13beb-114">Prvním prvkem pole je první argument; název spustitelného souboru není zahrnutý v poli, protože je v některých jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="13beb-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="13beb-115">Návratová hodnota se používá jako ukončovací kód pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="13beb-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="13beb-116">Nula obvykle indikuje úspěch; nenulové hodnoty označují chybu.</span><span class="sxs-lookup"><span data-stu-id="13beb-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="13beb-117">Neexistuje žádná úmluva pro konkrétní význam nenulových návratových kódů; význam návratových kódů je specifický pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="13beb-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="13beb-118">Následující příklad ilustruje jednoduchou `main` funkci.</span><span class="sxs-lookup"><span data-stu-id="13beb-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="13beb-119">Když se tento kód spustí s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="13beb-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="13beb-120">Implicitní vstupní bod</span><span class="sxs-lookup"><span data-stu-id="13beb-120">Implicit Entry Point</span></span>

<span data-ttu-id="13beb-121">Pokud program nemá žádný atribut **EntryPoint** , který explicitně indikuje vstupní bod, použijí se jako vstupní bod vazby nejvyšší úrovně v posledním souboru, který se má zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="13beb-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="13beb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13beb-122">See also</span></span>

- [<span data-ttu-id="13beb-123">Funkce</span><span class="sxs-lookup"><span data-stu-id="13beb-123">Functions</span></span>](index.md)
- [<span data-ttu-id="13beb-124">Vazby let</span><span class="sxs-lookup"><span data-stu-id="13beb-124">let Bindings</span></span>](let-bindings.md)
