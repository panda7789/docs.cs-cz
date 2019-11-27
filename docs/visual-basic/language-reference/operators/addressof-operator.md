---
title: AddressOf – operátor
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350273"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf – operátor (Visual Basic)
Vytvoří instanci delegáta, která odkazuje na konkrétní proceduru.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Součásti  
 `procedurename`  
 Požadováno. Určuje proceduru, na kterou má nově vytvořený delegát odkazovat.  
  
## <a name="remarks"></a>Poznámky  
 Operátor `AddressOf` vytvoří delegáta, který odkazuje na sub nebo funkci určenou parametrem `procedurename`. Pokud je zadaná procedura metodou instance, pak delegát odkazuje na instanci i na metodu. Poté, když je vyvolán delegát, je volána zadaná metoda zadané instance.  
  
 Operátor `AddressOf` lze použít jako operand konstruktoru delegáta nebo jej lze použít v kontextu, ve kterém lze určit typ delegáta kompilátorem.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá operátor `AddressOf` k určení delegáta pro zpracování události `Click` tlačítka.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `AddressOf` k určení spouštěcí funkce pro vlákno.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
