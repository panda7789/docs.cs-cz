---
title: Operandem 'AddressOf' musí být název metody (bez závorek).
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751628"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>Operandem 'AddressOf' musí být název metody (bez závorek).
`AddressOf` Operátor vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup. Syntaxe je následující.  
  
 `AddressOf``procedurename`  
  
 Vložení závorek okolo následující argument `AddressOf`, ve kterém není potřeba.  
  
 **ID chyby:** BC30577  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Odebrat závorky kolem následující argument `AddressOf`.  
  
2. Ujistěte se, že argument je název metody.  
  
## <a name="see-also"></a>Viz také:

- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
