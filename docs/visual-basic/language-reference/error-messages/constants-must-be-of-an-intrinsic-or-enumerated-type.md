---
title: Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9e36b84252c3d8762308e95323b8e284977df8c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409761"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="a7395-102">Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.</span><span class="sxs-lookup"><span data-stu-id="a7395-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="a7395-103">Došlo k pokusu o deklaraci konstanty jako třídy, struktury nebo typu pole nebo jako parametru typu definovaného pomocí obsahujícího obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a7395-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="a7395-104">Konstanty musí být vnitřní typ ( `Boolean` , `Byte` , `Date` , `Decimal` , `Double` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` , nebo `UShort` ), nebo `Enum` typ založený na jednom z celočíselných typů.</span><span class="sxs-lookup"><span data-stu-id="a7395-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="a7395-105">**ID chyby:** BC30424</span><span class="sxs-lookup"><span data-stu-id="a7395-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7395-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a7395-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a7395-107">Deklarujte konstantu jako vnitřní `Enum` typ nebo.</span><span class="sxs-lookup"><span data-stu-id="a7395-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2. <span data-ttu-id="a7395-108">Konstanta může být také zvláštní hodnota `True` , například, `False` nebo `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="a7395-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="a7395-109">Kompilátor považuje tyto předdefinované hodnoty za odpovídající vnitřní typ.</span><span class="sxs-lookup"><span data-stu-id="a7395-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7395-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7395-110">See also</span></span>

- [<span data-ttu-id="a7395-111">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="a7395-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="a7395-112">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a7395-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="a7395-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a7395-113">Data Types</span></span>](../data-types/index.md)
