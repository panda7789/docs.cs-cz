---
title: "AddressOf – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
