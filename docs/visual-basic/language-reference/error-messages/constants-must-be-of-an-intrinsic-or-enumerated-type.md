---
title: Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 4d635d289ed99aed48c296c278bc546971af51da
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999198"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="19d67-102">Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.</span><span class="sxs-lookup"><span data-stu-id="19d67-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="19d67-103">Pokusili jste se deklarace konstanty jako třídy, struktury nebo typ pole nebo jako parametr typu určené nadřazeného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="19d67-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="19d67-104">Konstanty musí být vnitřního typu (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, nebo `UShort`), nebo `Enum` typ na základě jedné z celočíselných typů.</span><span class="sxs-lookup"><span data-stu-id="19d67-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="19d67-105">**ID chyby:** BC30424</span><span class="sxs-lookup"><span data-stu-id="19d67-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19d67-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="19d67-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="19d67-107">Deklarace konstanty jako vnitřní nebo `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="19d67-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="19d67-108">Konstanta může být také zvláštní hodnota jako například `True`, `False`, nebo `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="19d67-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="19d67-109">Kompilátor považuje za tyto předdefinované hodnoty bude vhodné vnitřního typu.</span><span class="sxs-lookup"><span data-stu-id="19d67-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d67-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="19d67-110">See Also</span></span>  
 [<span data-ttu-id="19d67-111">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="19d67-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="19d67-112">Datové typy</span><span class="sxs-lookup"><span data-stu-id="19d67-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="19d67-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="19d67-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
