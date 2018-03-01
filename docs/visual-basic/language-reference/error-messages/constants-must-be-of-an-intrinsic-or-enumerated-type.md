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
