---
title: "Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="500c2-102">Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.</span><span class="sxs-lookup"><span data-stu-id="500c2-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="500c2-103">Pokusili jste se deklarace konstanty jako třída, struktura nebo typ pole, nebo jako parametr typu definované obsahující obecného typu.</span><span class="sxs-lookup"><span data-stu-id="500c2-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="500c2-104">Konstanty musí být vnitřního typu (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, nebo `UShort`), nebo `Enum` typu na základě jedné z integrální typy.</span><span class="sxs-lookup"><span data-stu-id="500c2-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="500c2-105">**ID chyby:** BC30424</span><span class="sxs-lookup"><span data-stu-id="500c2-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="500c2-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="500c2-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="500c2-107">Deklarace konstanty jako vnitřní nebo `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="500c2-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="500c2-108">Konstanta může být také speciální hodnotu, jako `True`, `False`, nebo `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="500c2-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="500c2-109">Kompilátor zvažuje tyto předem definovaných hodnot jako vnitřní příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="500c2-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500c2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="500c2-110">See Also</span></span>  
 [<span data-ttu-id="500c2-111">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="500c2-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="500c2-112">Datové typy</span><span class="sxs-lookup"><span data-stu-id="500c2-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="500c2-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="500c2-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
