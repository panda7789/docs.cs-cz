---
title: '&#39;AddressOf&#39; operand musí být název metody (bez závorek).'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 6f9827d885996ffab8bdab91d0f774a57073e4a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565147"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39; operand musí být název metody (bez závorek).
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
