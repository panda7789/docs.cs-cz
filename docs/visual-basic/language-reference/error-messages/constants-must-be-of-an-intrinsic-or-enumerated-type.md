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
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Konstanty musí být vnitřního nebo výčtového typu, nikoli třída, struktura, parametr typu nebo typ pole.
Pokusili jste se deklarace konstanty jako třída, struktura nebo typ pole, nebo jako parametr typu definované obsahující obecného typu.  
  
 Konstanty musí být vnitřního typu (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, nebo `UShort`), nebo `Enum` typu na základě jedné z integrální typy.  
  
 **ID chyby:** BC30424  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Deklarace konstanty jako vnitřní nebo `Enum` typu.  
  
2.  Konstanta může být také speciální hodnotu, jako `True`, `False`, nebo `Nothing`. Kompilátor zvažuje tyto předem definovaných hodnot jako vnitřní příslušného typu.  
  
## <a name="see-also"></a>Viz také  
 [Konstanty a výčty](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Datové typy](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)
