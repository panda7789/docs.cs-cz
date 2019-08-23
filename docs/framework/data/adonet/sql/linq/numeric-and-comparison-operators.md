---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: ff54856a66ad5e9c0362c013f8df5f1147055cd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915712"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="b1baa-102">Číselné a porovnávací operátory</span><span class="sxs-lookup"><span data-stu-id="b1baa-102">Numeric and Comparison Operators</span></span>

<span data-ttu-id="b1baa-103">Aritmetické a relační operátory pracují podle očekávání v modulu CLR (Common Language Runtime), s výjimkou následujících:</span><span class="sxs-lookup"><span data-stu-id="b1baa-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="b1baa-104">SQL nepodporuje operátor dělení na číslech s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="b1baa-104">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="b1baa-105">SQL nepodporuje nekontrolované aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="b1baa-105">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="b1baa-106">Operátory přírůstku a snížení způsobují vedlejší účinky při jejich použití ve výrazech, které nelze replikovat v SQL a jsou proto podporovány.</span><span class="sxs-lookup"><span data-stu-id="b1baa-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="b1baa-107">Podporované operátory</span><span class="sxs-lookup"><span data-stu-id="b1baa-107">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b1baa-108">podporuje následující operátory.</span><span class="sxs-lookup"><span data-stu-id="b1baa-108">supports the following operators.</span></span>

- <span data-ttu-id="b1baa-109">Základní aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="b1baa-109">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="b1baa-110">`-`odčítání</span><span class="sxs-lookup"><span data-stu-id="b1baa-110">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="b1baa-111">Visual Basic celočíselné dělení`\`()</span><span class="sxs-lookup"><span data-stu-id="b1baa-111">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="b1baa-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="b1baa-112">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="b1baa-113">`-`(unární negace)</span><span class="sxs-lookup"><span data-stu-id="b1baa-113">`-` (unary negation)</span></span>

- <span data-ttu-id="b1baa-114">Základní operátory porovnání:</span><span class="sxs-lookup"><span data-stu-id="b1baa-114">Basic comparison operators:</span></span>

  - <span data-ttu-id="b1baa-115">Visual Basic `=` a C#`==`</span><span class="sxs-lookup"><span data-stu-id="b1baa-115">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="b1baa-116">Visual Basic `<>` a C#`!=`</span><span class="sxs-lookup"><span data-stu-id="b1baa-116">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="b1baa-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="b1baa-117">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="b1baa-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1baa-118">See also</span></span>

- [<span data-ttu-id="b1baa-119">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="b1baa-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [<span data-ttu-id="b1baa-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1baa-120">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="b1baa-121">Operátory</span><span class="sxs-lookup"><span data-stu-id="b1baa-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
