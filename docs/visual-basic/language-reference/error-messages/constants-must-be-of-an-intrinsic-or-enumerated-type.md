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
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
Došlo k pokusu o deklaraci konstanty jako třídy, struktury nebo typu pole nebo jako parametru typu definovaného pomocí obsahujícího obecného typu.  
  
 Konstanty musí být vnitřní typ ( `Boolean` , `Byte` , `Date` , `Decimal` , `Double` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` , nebo `UShort` ), nebo `Enum` typ založený na jednom z celočíselných typů.  
  
 **ID chyby:** BC30424  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarujte konstantu jako vnitřní `Enum` typ nebo.  
  
2. Konstanta může být také zvláštní hodnota `True` , například, `False` nebo `Nothing` . Kompilátor považuje tyto předdefinované hodnoty za odpovídající vnitřní typ.  
  
## <a name="see-also"></a>Viz také

- [Konstanty a výčty](../constants-and-enumerations.md)
- [Datové typy](../../programming-guide/language-features/data-types/index.md)
- [Datové typy](../data-types/index.md)
