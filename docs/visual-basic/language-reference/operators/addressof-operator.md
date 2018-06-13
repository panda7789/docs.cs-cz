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
ms.openlocfilehash: 7c229c32a3b295b4dbfe50ca2abc60d4ad5f2145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597784"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf – operátor (Visual Basic)
Vytvoří instanci postup delegáta, který odkazuje na zvláštní postup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Součásti  
 `procedurename`  
 Požadováno. Určuje postup pro nově vytvořený postup delegát odkazovat.  
  
## <a name="remarks"></a>Poznámky  
 `AddressOf` Operátor vytvoří delegáta funkce, která odkazuje na funkci určeného `procedurename`. Když zadanou proceduru je že metodu instance pak delegáta funkce odkazuje na instanci a metoda. Potom při vyvolání delegáta funkce se nazývá zadanou metodu určené instance.  
  
 `AddressOf` Operátor lze použít jako operand konstruktor delegáta nebo ji lze použít v kontextu, ve kterém se dá určit typ delegát kompilátorem.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `AddressOf` operátor k určení delegáta pro zpracování `Click` událost tlačítka.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `AddressOf` operátor a určit funkce spuštění vlákna.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
