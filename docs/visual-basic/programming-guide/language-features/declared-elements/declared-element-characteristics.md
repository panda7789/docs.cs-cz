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
ms.openlocfilehash: 4e03cd28fed5e0ae109337739251c11a0ff3424a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331630"
---
# <a name="declared-element-characteristics-visual-basic"></a>Deklarované charakteristiky elementu (Visual Basic)
*Charakteristika* deklarovaného elementu je aspekt tohoto prvku, který ovlivňuje, jak s ním může pracovat kód. Každý deklarovaný element má k sobě přidruženou jednu nebo více následujících vlastností:  
  
- *Datový typ* – hodnoty, které element může uchovávat, a způsob, jakým tyto hodnoty uloží. Další informace najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
- *Doba života* – doba spuštění, během které je prvek k dispozici pro použití. Další informace najdete v tématu [Doba života v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- *Scope* – sada všech kódů, které mohou odkazovat na prvek bez kvalifikovaného názvu. Další informace naleznete v tématu [How to: Control a Scope of a proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
- *Úroveň přístupu* – oprávnění pro kód pro použití prvku. Další informace najdete v tématu [Postupy: řízení dostupnosti proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Charakteristiky prvků  
 V následující tabulce jsou uvedeny deklarované prvky a vlastnosti, které platí pro každý z nich.  
  
|Prvek|Typ dat|Životnost|Rozsah <sup>1</sup>|Úroveň přístupu|  
|-------------|---------------|--------------|------------------------|------------------|  
|Proměnná|Ano|Ano|Ano|Ano|  
|Konstanta|Ano|Ne|Ano|Ano|  
|Výčet|Ano|Ne|Ano|Ano|  
|Struktura|Ne|Ne|Ano|Ano|  
|Vlastnost|Ano|Ano|Ano|Ano|  
|Metoda|Ne|Ano|Ano|Ano|  
|Procedura (`Sub` nebo `Function`)|Ne|Ano|Ano|Ano|  
|Parametr procedury|Ano|Ano|Ano|Ne|  
|Vrácení funkce|Ano|Ano|Ano|Ne|  
|Operátor|Ano|Ne|Ano|Ano|  
|Rozhraní|Ne|Ne|Ano|Ano|  
|Třída|Ne|Ne|Ano|Ano|  
|Událost|Ne|Ne|Ano|Ano|  
|Delegát|Ne|Ne|Ano|Ano|  
  
 <sup>1</sup> obor se někdy označuje jako *viditelnost*.  
  
## <a name="see-also"></a>Viz také:

- [Deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Doba života v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
