---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: b29f78a13d6d0313e0ad29754f6d13ac08be1092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783133"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="a849e-102">Číselné a porovnávací operátory</span><span class="sxs-lookup"><span data-stu-id="a849e-102">Numeric and Comparison Operators</span></span>

<span data-ttu-id="a849e-103">Aritmetické operace a porovnání operátory fungovat podle očekávání v modulu common language runtime (CLR) s výjimkou následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a849e-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="a849e-104">SQL nepodporuje operátor numerického zbytku na čísla s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="a849e-104">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="a849e-105">SQL nepodporuje Nekontrolovaná aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="a849e-105">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="a849e-106">Operátory přírůstku a snížení způsobit vedlejší účinky při použití ve výrazech, které nelze replikovat v SQL a, proto nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a849e-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="a849e-107">Podporované operátory</span><span class="sxs-lookup"><span data-stu-id="a849e-107">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a849e-108">podporuje následující operátory.</span><span class="sxs-lookup"><span data-stu-id="a849e-108">supports the following operators.</span></span>

- <span data-ttu-id="a849e-109">Základní aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="a849e-109">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="a849e-110">`-` (odčítání)</span><span class="sxs-lookup"><span data-stu-id="a849e-110">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="a849e-111">Dělení celého čísla v jazyce Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="a849e-111">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="a849e-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="a849e-112">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="a849e-113">`-` (unární negace)</span><span class="sxs-lookup"><span data-stu-id="a849e-113">`-` (unary negation)</span></span>

- <span data-ttu-id="a849e-114">Základní relační operátory:</span><span class="sxs-lookup"><span data-stu-id="a849e-114">Basic comparison operators:</span></span>

  - <span data-ttu-id="a849e-115">Visual Basic `=` and C# `==`</span><span class="sxs-lookup"><span data-stu-id="a849e-115">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="a849e-116">Visual Basic `<>` and C# `!=`</span><span class="sxs-lookup"><span data-stu-id="a849e-116">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="a849e-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="a849e-117">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="a849e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a849e-118">See also</span></span>

- [<span data-ttu-id="a849e-119">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="a849e-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [<span data-ttu-id="a849e-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a849e-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)
- [<span data-ttu-id="a849e-121">Operátory</span><span class="sxs-lookup"><span data-stu-id="a849e-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
