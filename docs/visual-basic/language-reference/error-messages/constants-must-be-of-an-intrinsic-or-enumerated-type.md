---
title: Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: f82a548c820aec7d2ae13c30a67d778fc167a8b6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813105"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
Pokusili jste se deklarace konstanty jako třídy, struktury nebo typ pole nebo jako parametr typu určené nadřazeného obecného typu.  
  
 Konstanty musí být vnitřního typu (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, nebo `UShort`), nebo `Enum` typ na základě jedné z celočíselných typů.  
  
 **ID chyby:** BC30424  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Deklarace konstanty jako vnitřní nebo `Enum` typu.  
  
2.  Konstanta může být také zvláštní hodnota jako například `True`, `False`, nebo `Nothing`. Kompilátor považuje za tyto předdefinované hodnoty bude vhodné vnitřního typu.  
  
## <a name="see-also"></a>Viz také:

- [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Datové typy](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
