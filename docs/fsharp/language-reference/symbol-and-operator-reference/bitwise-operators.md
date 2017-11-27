---
title: "Bitové operátory (F#)"
description: "Další informace o bitové operátory, které jsou k dispozici v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a><span data-ttu-id="573fc-104">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="573fc-104">Bitwise Operators</span></span>

<span data-ttu-id="573fc-105">Toto téma popisuje bitové operátory, které jsou k dispozici v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="573fc-105">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="573fc-106">Souhrn bitové operátory</span><span class="sxs-lookup"><span data-stu-id="573fc-106">Summary of Bitwise Operators</span></span>
<span data-ttu-id="573fc-107">Následující tabulka popisuje bitové operátory, které jsou podporovány pro nezabalený integrální typy v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="573fc-107">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="573fc-108">Operátor</span><span class="sxs-lookup"><span data-stu-id="573fc-108">Operator</span></span>|<span data-ttu-id="573fc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="573fc-109">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="573fc-110">Bitový operátor AND.</span><span class="sxs-lookup"><span data-stu-id="573fc-110">Bitwise AND operator.</span></span> <span data-ttu-id="573fc-111">BITS ve výsledku mít hodnotu 1, pokud odpovídající bity v obou operandy zdroje jsou 1.</span><span class="sxs-lookup"><span data-stu-id="573fc-111">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="573fc-112">Bitový operátor OR.</span><span class="sxs-lookup"><span data-stu-id="573fc-112">Bitwise OR operator.</span></span> <span data-ttu-id="573fc-113">Služba BITS ve výsledku mít hodnotu 1, pokud buď odpovídající bitů ve zdroji jsou operandy 1.</span><span class="sxs-lookup"><span data-stu-id="573fc-113">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="573fc-114">Bitový exkluzivní operátor OR.</span><span class="sxs-lookup"><span data-stu-id="573fc-114">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="573fc-115">BITS ve výsledku mít hodnotu 1, pokud bitů operandy zdroje mají nerovné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="573fc-115">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="573fc-116">Operátor bitovou negaci.</span><span class="sxs-lookup"><span data-stu-id="573fc-116">Bitwise negation operator.</span></span> <span data-ttu-id="573fc-117">Toto je unární operátor a vytváří výsledek, ve kterém všechny 0 bitů operand zdroje se převedou na 1 bits a všechny 1 bits se převedou na 0 bits.</span><span class="sxs-lookup"><span data-stu-id="573fc-117">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="573fc-118">Bitový operátor posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="573fc-118">Bitwise left-shift operator.</span></span> <span data-ttu-id="573fc-119">Výsledkem je, že první operand s bity zapuštěno podle počtu bitů Druhý operand doleva.</span><span class="sxs-lookup"><span data-stu-id="573fc-119">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="573fc-120">Nejsou BITS přesunout mimo nejvýznamnějších pozice otočen do nejméně významný pozici.</span><span class="sxs-lookup"><span data-stu-id="573fc-120">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="573fc-121">Nejméně významný bits se vyplní nul.</span><span class="sxs-lookup"><span data-stu-id="573fc-121">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="573fc-122">Typ druhý argument je `int32`.</span><span class="sxs-lookup"><span data-stu-id="573fc-122">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="573fc-123">Bitový operátor posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="573fc-123">Bitwise right-shift operator.</span></span> <span data-ttu-id="573fc-124">Výsledkem je první operand s bity zapuštěno právo podle počtu bitů Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="573fc-124">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="573fc-125">Nejsou BITS přesunout mimo nejméně významný pozice otočen do nejvýznamnějších pozici.</span><span class="sxs-lookup"><span data-stu-id="573fc-125">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="573fc-126">Pro typy bez znaménka se vyplní nejvýznamnějších bity s nulami.</span><span class="sxs-lookup"><span data-stu-id="573fc-126">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="573fc-127">Pro typy signed se s těmi, které vyplní nejvýznamnějších bits.</span><span class="sxs-lookup"><span data-stu-id="573fc-127">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="573fc-128">Typ druhý argument je `int32`.</span><span class="sxs-lookup"><span data-stu-id="573fc-128">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="573fc-129">Bitové operátory můžete použít následující typy: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, a `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="573fc-129">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="573fc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="573fc-130">See Also</span></span>
[<span data-ttu-id="573fc-131">Operátor referenční dokumentace symbolů a</span><span class="sxs-lookup"><span data-stu-id="573fc-131">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="573fc-132">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="573fc-132">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="573fc-133">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="573fc-133">Boolean Operators</span></span>](boolean-operators.md)

