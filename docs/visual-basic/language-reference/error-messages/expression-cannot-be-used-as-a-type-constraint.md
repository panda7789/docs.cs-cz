---
title: '&#39;&lt;výraz&gt; &#39; nelze použít jako omezení typu.'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8e9aad2ec65e037b15e19ca2e624fdc8f28bc94e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588171"
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39;&lt;výraz&gt; &#39; nelze použít jako omezení typu.
Seznam omezení obsahuje výraz, který nepředstavuje platný parametr typu omezení.  
  
 Seznam omezení ukládá požadavky na typ argument předaný parametr typu. V libovolné kombinace můžete určit následující požadavky:  
  
-   Argument typu musí implementovat jednu nebo více rozhraní  
  
-   Argument typu musí dědit z maximálně jednu třídu  
  
-   Argument typu musí vystavit konstruktor bez parametrů, kterým může přistupovat vytváření kódu (zahrnout `New` omezení)  
  
 Pokud neuvedete žádné konkrétní třídy nebo rozhraní v seznamu omezení, můžete použít obecnější požadavek zadáním jednoho z následujících akcí:  
  
-   Argument typu musí být typu hodnoty (zahrnout `Structure` omezení)  
  
-   Argument typu musí být typu odkazu (zahrnout `Class` omezení)  
  
 Nelze zadat současně `Structure` a `Class` pro stejný typ parametru a nelze zadat buď jednu více než jednou.  
  
 **ID chyby:** BC32061  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ověřte, jestli jsou správně zadané ve výrazu a jejích elementů.  
  
-   Výraz není způsobilá pro předchozí seznam požadavků, odeberte ji ze seznamu omezení.  
  
-   Pokud výraz odkazuje na rozhraní nebo třídy, ověřte, zda kompilátor má přístup k tomuto rozhraní nebo třídy. Možná budete muset kvalifikovat jeho název a možná budete muset přidat odkaz na projekt. Další informace najdete v tématu "Odkazy na projekty" v [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
