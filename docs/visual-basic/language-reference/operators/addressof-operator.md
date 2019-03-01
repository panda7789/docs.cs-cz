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
ms.openlocfilehash: b68d93009d2d297f8b8867fb8e79b26173a45095
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964666"
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
