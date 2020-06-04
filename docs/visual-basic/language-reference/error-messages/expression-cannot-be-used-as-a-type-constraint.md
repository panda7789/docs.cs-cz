---
title: Výrazu '<expression>' nelze použít jako omezení typu.
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: e2ba411a5f0db21539a9cf99c7645b8c9309caab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409553"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a>Výrazu '\<expression>' nelze použít jako omezení typu.
Seznam omezení obsahuje výraz, který nepředstavuje platné omezení parametru typu.  
  
 Seznam omezení ukládá požadavky na argument typu předaný parametru typu. V libovolné kombinaci můžete zadat následující požadavky:  
  
- Argument typu musí implementovat jedno nebo víc rozhraní.  
  
- Argument typu musí dědit od maximálně jedné třídy.  
  
- Argument typu musí vystavit konstruktor bez parametrů, ke kterému může vytvořit kód (zahrnuje `New` omezení).  
  
 Pokud v seznamu omezení nezahrnete žádnou konkrétní třídu nebo rozhraní, můžete stanovit obecnější požadavek zadáním jednoho z následujících způsobů:  
  
- Argument typu musí být typ hodnoty (zahrnuje `Structure` omezení).  
  
- Argument typu musí být odkazový typ (zahrnuje `Class` omezení).  
  
 Nemůžete zadat obojí `Structure` a `Class` pro stejný parametr typu a nemůžete zadat žádné z nich více než jednou.  
  
 **ID chyby:** BC32061  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ověřte, zda je výraz a jeho prvky zadány správně.  
  
- Pokud výraz nesplňuje podmínky pro předchozí seznam požadavků, odeberte ho ze seznamu omezení.  
  
- Pokud výraz odkazuje na rozhraní nebo třídu, ověřte, zda má kompilátor přístup k tomuto rozhraní nebo třídě. Je možné, že budete muset kvalifikovat jeho název a může být nutné přidat odkaz na projekt. Další informace naleznete v části "odkazy na projekty" v tématu [odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Viz také

- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Typy hodnot a typy odkazu](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
