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
ms.openlocfilehash: 26c9ec247a0b848d46df063bc7b85ceec30d81c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650891"
---
# <a name="declared-element-characteristics-visual-basic"></a>Deklarované charakteristiky elementu (Visual Basic)
A *vlastnosti* deklarované elementu je aspekt daný element, který má vliv jak kód mohou komunikovat s ním. Každý element, deklarované má jeden nebo více z následujících vlastností s ním spojená:  
  
-   *Datový typ* – hodnoty mohou být uloženy elementu a jak ho uloží tyto hodnoty. Další informace najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
-   *Doba platnosti* – doba provádění, během které je k dispozici pro použití elementu. Další informace najdete v tématu [doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Obor* – sadu všechen kód, který mohou odkazovat na prvek bez určení názvu. Další informace najdete v tématu [postupy: řízení rozsahu proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Úroveň přístupu* – oprávnění pro kód, aby pomocí elementu. Další informace najdete v tématu [postupy: řízení dostupnosti proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## <a name="characteristics-of-the-elements"></a>Vlastnosti elementů  
 V následující tabulce jsou uvedeny deklarované elementy a vlastnosti, které platí pro každé z nich.  
  
|Prvek|Datový typ|Doba platnosti|Obor <sup>1</sup>|Úroveň přístupu|  
|-------------|---------------|--------------|------------------------|------------------|  
|Proměnná|Ano|Ano|Ano|Ano|  
|Konstanta|Ano|Ne|Ano|Ano|  
|Výčet|Ano|Ne|Ano|Ano|  
|Struktura|Ne|Ne|Ano|Ano|  
|Vlastnost|Ano|Ano|Ano|Ano|  
|Metoda|Ne|Ano|Ano|Ano|  
|Postup (`Sub` nebo `Function`)|Ne|Ano|Ano|Ano|  
|Parametr postupu|Ano|Ano|Ano|Ne|  
|Return – funkce|Ano|Ano|Ano|Ne|  
|Operátor|Ano|Ne|Ano|Ano|  
|Rozhraní|Ne|Ne|Ano|Ano|  
|Třída|Ne|Ne|Ano|Ano|  
|Událost|Ne|Ne|Ano|Ano|  
|Delegát|Ne|Ne|Ano|Ano|  
  
 <sup>1</sup> oboru se někdy označuje jako *viditelnost*.  
  
## <a name="see-also"></a>Viz také  
 [Deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
