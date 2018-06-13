---
title: Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9039376fc4d1f67ca9b526e46eaf28a0b1a3943c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587479"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="3d288-102">Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.</span><span class="sxs-lookup"><span data-stu-id="3d288-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="3d288-103">Pokusili jste se deklarace konstanty jako třída, struktura nebo typ pole, nebo jako parametr typu definované obsahující obecného typu.</span><span class="sxs-lookup"><span data-stu-id="3d288-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="3d288-104">Konstanty musí být vnitřního typu (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, nebo `UShort`), nebo `Enum` typu na základě jedné z integrální typy.</span><span class="sxs-lookup"><span data-stu-id="3d288-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="3d288-105">**ID chyby:** BC30424</span><span class="sxs-lookup"><span data-stu-id="3d288-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d288-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3d288-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="3d288-107">Deklarace konstanty jako vnitřní nebo `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="3d288-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="3d288-108">Konstanta může být také speciální hodnotu, jako `True`, `False`, nebo `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3d288-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="3d288-109">Kompilátor zvažuje tyto předem definovaných hodnot jako vnitřní příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="3d288-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d288-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d288-110">See Also</span></span>  
 [<span data-ttu-id="3d288-111">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="3d288-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="3d288-112">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3d288-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="3d288-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3d288-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
