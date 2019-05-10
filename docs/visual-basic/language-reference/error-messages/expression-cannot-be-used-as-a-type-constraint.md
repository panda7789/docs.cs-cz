---
title: Výrazu '<expression>' nelze použít jako omezení typu.
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: ff51bb27847a92b07ce6275a8ddee4789e865f08
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642802"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>"\<výrazu >' nelze použít jako omezení typu
Seznam omezení obsahuje výraz, který nepředstavuje platné omezení pro parametr typu.  
  
 Seznam omezení žáků argument typu předaný do parametru typu. V jakékoli kombinace můžete určit následující požadavky:  
  
- Argument typu musí implementovat jedno nebo více rozhraní  
  
- Argument typu musí dědit z nejvýše jednu třídu  
  
- Argument typu musí vystavit konstruktor bez parametrů, s přístupem k vytváření kódu (patří `New` omezení)  
  
 Pokud jste neobsahují žádné konkrétní třídu nebo rozhraní v seznamu omezení, je možné nastavit obecnější požadavek zadáním jedné z následujících akcí:  
  
- Argument typu musí být typ hodnoty (patří `Structure` omezení)  
  
- Argument typu musí být typ odkazu (patří `Class` omezení)  
  
 Nelze zadat současně `Structure` a `Class` pro stejný typ parametru a nelze zadat jednu více než jednou.  
  
 **ID chyby:** BC32061  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ověřte, že výraz a jeho prvky jsou zadány správně.  
  
- Pokud výraz nesplňuje požadavky uvedené v předchozím seznamu, odeberte ji ze seznamu omezení.  
  
- Pokud výraz odkazuje na rozhraní nebo tříd, ověřte, že kompilátor má přístup k tomuto rozhraní nebo tříd. Možná budete muset kvalifikovat její název a může být nutné přidat odkaz na svůj projekt. Další informace najdete v tématu "Odkazy na projekty" [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Viz také:

- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy hodnot a odkazové typy](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
