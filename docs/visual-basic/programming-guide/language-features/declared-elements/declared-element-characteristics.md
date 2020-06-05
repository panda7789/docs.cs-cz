---
title: Deklarované charakteristiky elementu
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 9d1e327c25689bed1405ea9a627da6232abb707b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392945"
---
# <a name="declared-element-characteristics-visual-basic"></a>Deklarované charakteristiky elementu (Visual Basic)
*Charakteristika* deklarovaného elementu je aspekt tohoto prvku, který ovlivňuje, jak s ním může pracovat kód. Každý deklarovaný element má k sobě přidruženou jednu nebo více následujících vlastností:  
  
- *Datový typ* – hodnoty, které element může uchovávat, a způsob, jakým tyto hodnoty uloží. Další informace najdete v tématu [datové typy](../../../language-reference/data-types/index.md).  
  
- *Doba života* – doba spuštění, během které je prvek k dispozici pro použití. Další informace najdete v tématu [Doba života v Visual Basic](lifetime.md).  
  
- *Scope* – sada všech kódů, které mohou odkazovat na prvek bez kvalifikovaného názvu. Další informace naleznete v tématu [How to: Control a Scope of a proměnná](how-to-control-the-scope-of-a-variable.md).  
  
- *Úroveň přístupu* – oprávnění pro kód pro použití prvku. Další informace najdete v tématu [Postupy: řízení dostupnosti proměnné](how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Charakteristiky prvků  
 V následující tabulce jsou uvedeny deklarované prvky a vlastnosti, které platí pro každý z nich.  
  
|Prvek|Typ dat|Doba platnosti|Rozsah <sup>1</sup>|Úroveň přístupu|  
|-------------|---------------|--------------|------------------------|------------------|  
|Proměnná|Ano|Ano|Ano|Ano|  
|Trvalé|Ano|No|Ano|Ano|  
|Výčet|Ano|No|Ano|Ano|  
|Struktura|Ne|Ne|Ano|Ano|  
|Vlastnost|Ano|Ano|Ano|Ano|  
|Metoda|No|Ano|Ano|Ano|  
|Procedura ( `Sub` nebo `Function` )|No|Ano|Ano|Ano|  
|Parametr procedury|Ano|Ano|Ano|Ne|  
|Vrácení funkce|Ano|Ano|Ano|Ne|  
|Operátor|Ano|No|Ano|Ano|  
|Rozhraní|Ne|Ne|Ano|Ano|  
|Třída|Ne|Ne|Ano|Ano|  
|Událost|Ne|Ne|Ano|Ano|  
|Delegát|Ne|Ne|Ano|Ano|  
  
 <sup>1</sup> obor se někdy označuje jako *viditelnost*.  
  
## <a name="see-also"></a>Viz také

- [Deklarované elementy](index.md)
- [Deklarované názvy elementů](declared-element-names.md)
- [Odkazy na deklarované elementy](references-to-declared-elements.md)
- [Doba platnosti v jazyce Visual Basic](lifetime.md)
- [Rozsah v jazyce Visual Basic](scope.md)
- [Úrovně přístupu v Visual Basic](access-levels.md)
- [Datové typy](../data-types/index.md)
- [Deklarace proměnné](../variables/variable-declaration.md)
