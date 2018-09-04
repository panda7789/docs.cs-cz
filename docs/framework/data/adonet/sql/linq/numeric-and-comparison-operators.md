---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: a7a455730860e2b11a5ceff5a70934502b312e19
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515063"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="ddf89-102">Číselné a porovnávací operátory</span><span class="sxs-lookup"><span data-stu-id="ddf89-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="ddf89-103">Aritmetické operace a porovnání operátory fungovat podle očekávání v modulu common language runtime (CLR) s výjimkou následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ddf89-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="ddf89-104">SQL nepodporuje operátor numerického zbytku na čísla s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="ddf89-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="ddf89-105">SQL nepodporuje Nekontrolovaná aritmetické operace.</span><span class="sxs-lookup"><span data-stu-id="ddf89-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="ddf89-106">Operátory přírůstku a snížení způsobit vedlejší účinky při použití ve výrazech, které nelze replikovat v SQL a, proto nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="ddf89-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="ddf89-107">Podporované operátory</span><span class="sxs-lookup"><span data-stu-id="ddf89-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ddf89-108"> podporuje následující operátory.</span><span class="sxs-lookup"><span data-stu-id="ddf89-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="ddf89-109">Základní aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="ddf89-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="ddf89-110">`-` (odčítání)</span><span class="sxs-lookup"><span data-stu-id="ddf89-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="ddf89-111">Dělení celého čísla v jazyce Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="ddf89-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="ddf89-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="ddf89-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="ddf89-113">`-` (unární negace)</span><span class="sxs-lookup"><span data-stu-id="ddf89-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="ddf89-114">Základní relační operátory:</span><span class="sxs-lookup"><span data-stu-id="ddf89-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="ddf89-115">Visual Basic `=` a C# `==`</span><span class="sxs-lookup"><span data-stu-id="ddf89-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="ddf89-116">Visual Basic `<>` a C# `!=`</span><span class="sxs-lookup"><span data-stu-id="ddf89-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="ddf89-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="ddf89-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="ddf89-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddf89-118">See Also</span></span>  
 [<span data-ttu-id="ddf89-119">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="ddf89-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="ddf89-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ddf89-120">C# Operators</span></span>](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="ddf89-121">Operátory</span><span class="sxs-lookup"><span data-stu-id="ddf89-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
