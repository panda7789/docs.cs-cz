---
title: "Číselné a relační operátory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b89555bc71d95291c096d2e694c315720cfb41c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="34724-102">Číselné a relační operátory</span><span class="sxs-lookup"><span data-stu-id="34724-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="34724-103">Porovnání a aritmetické operátory fungovat podle očekávání v common language runtime (CLR) s výjimkou následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="34724-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="34724-104">SQL nepodporuje operátor numerického zbytku na čísla s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="34724-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="34724-105">SQL nepodporuje aritmetické nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="34724-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="34724-106">Operátory přírůstku a snížení způsobit vedlejší účinky, když je budete používat ve výrazech, které nelze replikovat v systému SQL a, proto nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="34724-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="34724-107">Podporované operátory</span><span class="sxs-lookup"><span data-stu-id="34724-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="34724-108">podporuje následující operátory.</span><span class="sxs-lookup"><span data-stu-id="34724-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="34724-109">Základní aritmetické operátory:</span><span class="sxs-lookup"><span data-stu-id="34724-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="34724-110">`-`(odčítání)</span><span class="sxs-lookup"><span data-stu-id="34724-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="34724-111">Dělení celého čísla v jazyce Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="34724-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="34724-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="34724-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="34724-113">`-`(unární negace)</span><span class="sxs-lookup"><span data-stu-id="34724-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="34724-114">Operátory porovnání základní:</span><span class="sxs-lookup"><span data-stu-id="34724-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="34724-115">Visual Basic `=` a C#`==`</span><span class="sxs-lookup"><span data-stu-id="34724-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="34724-116">Visual Basic `<>` a C#`!=`</span><span class="sxs-lookup"><span data-stu-id="34724-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="34724-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="34724-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="34724-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="34724-118">See Also</span></span>  
 [<span data-ttu-id="34724-119">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="34724-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="34724-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34724-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="34724-121">Operátory</span><span class="sxs-lookup"><span data-stu-id="34724-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
