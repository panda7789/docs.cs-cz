---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781296"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="91fd4-102">Číselné a porovnávací operátory</span><span class="sxs-lookup"><span data-stu-id="91fd4-102">Numeric and Comparison Operators</span></span>

<span data-ttu-id="91fd4-103">Aritmetické a relační operátory pracují podle očekávání v modulu CLR (Common Language Runtime), s výjimkou následujících:</span><span class="sxs-lookup"><span data-stu-id="91fd4-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="91fd4-104">SQL nepodporuje operátor dělení na číslech s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="91fd4-104">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="91fd4-105">SQL nepodporuje nekontrolované aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="91fd4-105">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="91fd4-106">Operátory přírůstku a snížení způsobují vedlejší účinky při jejich použití ve výrazech, které nelze replikovat v SQL a jsou proto podporovány.</span><span class="sxs-lookup"><span data-stu-id="91fd4-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="91fd4-107">Podporované operátory</span><span class="sxs-lookup"><span data-stu-id="91fd4-107">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="91fd4-108">podporuje následující operátory.</span><span class="sxs-lookup"><span data-stu-id="91fd4-108">supports the following operators.</span></span>

- <span data-ttu-id="91fd4-109">Základní aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="91fd4-109">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="91fd4-110">`-`odčítání</span><span class="sxs-lookup"><span data-stu-id="91fd4-110">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="91fd4-111">Visual Basic celočíselné dělení`\`()</span><span class="sxs-lookup"><span data-stu-id="91fd4-111">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="91fd4-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="91fd4-112">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="91fd4-113">`-`(unární negace)</span><span class="sxs-lookup"><span data-stu-id="91fd4-113">`-` (unary negation)</span></span>

- <span data-ttu-id="91fd4-114">Základní operátory porovnání:</span><span class="sxs-lookup"><span data-stu-id="91fd4-114">Basic comparison operators:</span></span>

  - <span data-ttu-id="91fd4-115">Visual Basic `=` a C#`==`</span><span class="sxs-lookup"><span data-stu-id="91fd4-115">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="91fd4-116">Visual Basic `<>` a C#`!=`</span><span class="sxs-lookup"><span data-stu-id="91fd4-116">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="91fd4-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="91fd4-117">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="91fd4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91fd4-118">See also</span></span>

- [<span data-ttu-id="91fd4-119">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="91fd4-119">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="91fd4-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91fd4-120">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="91fd4-121">Operátory</span><span class="sxs-lookup"><span data-stu-id="91fd4-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
