---
title: Operandem 'AddressOf' musí být název metody (bez závorek).
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 37b02ab76730458b757835fda37b8cb145ed93ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262111"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>Operandem 'AddressOf' musí být název metody (bez závorek).
`AddressOf` Operátor vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup. Syntaxe je následující.  
  
 `AddressOf``procedurename`  
  
 Vložení závorek okolo následující argument `AddressOf`, ve kterém není potřeba.  
  
 **ID chyby:** BC30577  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odebrat závorky kolem následující argument `AddressOf`.  
  
2.  Ujistěte se, že argument je název metody.  
  
## <a name="see-also"></a>Viz také:
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
