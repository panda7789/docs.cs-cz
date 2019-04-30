---
title: Deklarované charakteristiky elementu (Visual Basic)
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
ms.openlocfilehash: 98f6a7738a462e9f36abdc0380cb1fe8d488fb9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61830164"
---
# <a name="declared-element-characteristics-visual-basic"></a>Deklarované charakteristiky elementu (Visual Basic)
A *charakteristiku* deklarované elementu je určitý aspekt tento prvek, který má vliv jak s ním mohli pracovat kódu. Každý element deklarovaný má jeden nebo více z následujících vlastností s ním spojená:  
  
- *Datový typ* – může obsahovat hodnoty elementu a způsobu, jakým ukládá tyto hodnoty. Další informace najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
- *Doba života* – doba provádění, během které je k dispozici pro použití elementu. Další informace najdete v tématu [životnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- *Obor* – sada veškerý kód, který může odkazovat na prvek bez kvalifikace názvu. Další informace najdete v tématu [jak: Řízení rozsahu proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
- *Úroveň přístupu* – oprávnění pro kód, který pomocí elementu. Další informace najdete v tématu [jak: Řízení dostupnosti proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Vlastnosti elementů  
 V následující tabulce jsou uvedeny deklarované elementy a vlastnosti, které se vztahují ke každému z nich.  
  
|Prvek|Datový typ|Životnost|Obor <sup>1</sup>|Úroveň přístupu|  
|-------------|---------------|--------------|------------------------|------------------|  
|Proměnná|Ano|Ano|Ano|Ano|  
|Konstanta|Ano|Ne|Ano|Ano|  
|Výčet|Ano|Ne|Ano|Ano|  
|Struktura|Ne|Ne|Ano|Ano|  
|Vlastnost|Ano|Ano|Ano|Ano|  
|Metoda|Ne|Ano|Ano|Ano|  
|Postup (`Sub` nebo `Function`)|Ne|Ano|Ano|Ano|  
|Parametr procedury|Ano|Ano|Ano|Ne|  
|Return – funkce|Ano|Ano|Ano|Ne|  
|Operátor|Ano|Ne|Ano|Ano|  
|Rozhraní|Ne|Ne|Ano|Ano|  
|Třída|Ne|Ne|Ano|Ano|  
|Událost|Ne|Ne|Ano|Ano|  
|Delegát|Ne|Ne|Ano|Ano|  
  
 <sup>1</sup> oboru se někdy označuje jako *viditelnost*.  
  
## <a name="see-also"></a>Viz také:

- [Deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
