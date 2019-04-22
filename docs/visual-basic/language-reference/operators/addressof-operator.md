---
title: AddressOf – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 9d8515b6d5b0caf3552ed05a7e0cd4a271efaf54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830341"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf – operátor (Visual Basic)
Vytvoří instanci procedury delegáta, který odkazuje na konkrétní postup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Součásti  
 `procedurename`  
 Povinný parametr. Určuje postup odkazovat pomocí nově vytvořeného procedury delegáta.  
  
## <a name="remarks"></a>Poznámky  
 `AddressOf` Operátor vytvoří delegáta funkce, která odkazuje na funkci určené `procedurename`. Když zadaná procedura je že metodu instance potom delegáta funkce odkazuje na instanci a metodu. Potom při vyvolání delegáta funkce se nazývá zadanou metodu určené instance.  
  
 `AddressOf` Operátor můžete použít jako operand konstruktor delegate, nebo je možné v kontextu, ve kterém můžete určit typ delegáta kompilátorem.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `AddressOf` operátor k určení delegáta pro zpracování `Click` událost tlačítka.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `AddressOf` operátor k určení funkce spuštění vlákna.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
