---
title: "'<typename>' je typ delegátu."
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4278ea0fc6a8dc2c6a90b720d2da70b1c26f2a17
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283449"
---
# <a name="typename-is-a-delegate-type"></a>"\<typename >' je typ delegátu
"\<typename >' je typ delegátu. Konstrukce delegáta povoluje pouze jeden výraz AddressOf jako seznam argumentů. Výraz AddressOf často lze použít místo vytváření delegátů.  
  
 A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegate.  
  
 Můžete zadat pouze jeden `AddressOf` výraz při vytváření nové instance delegáta.  
  
 K této chybě může dojít, pokud nepředáte žádné argumenty konstruktoru delegáta, Pokud předáváte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výrazu.  
  
 **ID chyby:** BC32008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pomocí jediné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzuli.  
  
## <a name="see-also"></a>Viz také:
- [Operátor New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Postupy: Volání metody delegáta](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
