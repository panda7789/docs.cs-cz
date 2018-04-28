---
title: Bitové operátory (F#)
description: 'Další informace o bitové operátory, které jsou k dispozici v programovací jazyk F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4d5abff564a5d1dcbe52b99edf431ca10e442061
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="bitwise-operators"></a><span data-ttu-id="3f004-103">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="3f004-103">Bitwise Operators</span></span>

<span data-ttu-id="3f004-104">Toto téma popisuje bitové operátory, které jsou k dispozici v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="3f004-104">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="3f004-105">Souhrn bitové operátory</span><span class="sxs-lookup"><span data-stu-id="3f004-105">Summary of Bitwise Operators</span></span>
<span data-ttu-id="3f004-106">Následující tabulka popisuje bitové operátory, které jsou podporovány pro nezabalený integrální typy v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="3f004-106">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="3f004-107">Operátor</span><span class="sxs-lookup"><span data-stu-id="3f004-107">Operator</span></span>|<span data-ttu-id="3f004-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f004-108">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="3f004-109">Bitový operátor AND.</span><span class="sxs-lookup"><span data-stu-id="3f004-109">Bitwise AND operator.</span></span> <span data-ttu-id="3f004-110">BITS ve výsledku mít hodnotu 1, pokud odpovídající bity v obou operandy zdroje jsou 1.</span><span class="sxs-lookup"><span data-stu-id="3f004-110">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="3f004-111">Bitový operátor OR.</span><span class="sxs-lookup"><span data-stu-id="3f004-111">Bitwise OR operator.</span></span> <span data-ttu-id="3f004-112">Služba BITS ve výsledku mít hodnotu 1, pokud buď odpovídající bitů ve zdroji jsou operandy 1.</span><span class="sxs-lookup"><span data-stu-id="3f004-112">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="3f004-113">Bitový exkluzivní operátor OR.</span><span class="sxs-lookup"><span data-stu-id="3f004-113">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="3f004-114">BITS ve výsledku mít hodnotu 1, pokud bitů operandy zdroje mají nerovné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3f004-114">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="3f004-115">Operátor bitovou negaci.</span><span class="sxs-lookup"><span data-stu-id="3f004-115">Bitwise negation operator.</span></span> <span data-ttu-id="3f004-116">Toto je unární operátor a vytváří výsledek, ve kterém všechny 0 bitů operand zdroje se převedou na 1 bits a všechny 1 bits se převedou na 0 bits.</span><span class="sxs-lookup"><span data-stu-id="3f004-116">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="3f004-117">Bitový operátor posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="3f004-117">Bitwise left-shift operator.</span></span> <span data-ttu-id="3f004-118">Výsledkem je, že první operand s bity zapuštěno podle počtu bitů Druhý operand doleva.</span><span class="sxs-lookup"><span data-stu-id="3f004-118">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="3f004-119">Nejsou BITS přesunout mimo nejvýznamnějších pozice otočen do nejméně významný pozici.</span><span class="sxs-lookup"><span data-stu-id="3f004-119">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="3f004-120">Nejméně významný bits se vyplní nul.</span><span class="sxs-lookup"><span data-stu-id="3f004-120">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="3f004-121">Typ druhý argument je `int32`.</span><span class="sxs-lookup"><span data-stu-id="3f004-121">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="3f004-122">Bitový operátor posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="3f004-122">Bitwise right-shift operator.</span></span> <span data-ttu-id="3f004-123">Výsledkem je první operand s bity zapuštěno právo podle počtu bitů Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="3f004-123">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="3f004-124">Nejsou BITS přesunout mimo nejméně významný pozice otočen do nejvýznamnějších pozici.</span><span class="sxs-lookup"><span data-stu-id="3f004-124">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="3f004-125">Pro typy bez znaménka se vyplní nejvýznamnějších bity s nulami.</span><span class="sxs-lookup"><span data-stu-id="3f004-125">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="3f004-126">Pro typy signed se s těmi, které vyplní nejvýznamnějších bits.</span><span class="sxs-lookup"><span data-stu-id="3f004-126">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="3f004-127">Typ druhý argument je `int32`.</span><span class="sxs-lookup"><span data-stu-id="3f004-127">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="3f004-128">Bitové operátory můžete použít následující typy: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, a `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="3f004-128">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f004-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f004-129">See Also</span></span>
[<span data-ttu-id="3f004-130">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="3f004-130">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="3f004-131">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="3f004-131">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="3f004-132">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="3f004-132">Boolean Operators</span></span>](boolean-operators.md)

