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
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591659"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf – operátor (Visual Basic)
Vytvoří instanci delegáta, která odkazuje na konkrétní proceduru.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Součásti  
 `procedurename`  
 Povinný parametr. Určuje proceduru, na kterou má nově vytvořený delegát odkazovat.  
  
## <a name="remarks"></a>Poznámky  
 Operátor `AddressOf` vytvoří delegáta, který odkazuje na sub nebo funkci určenou parametrem `procedurename`. Pokud je zadaná procedura metodou instance, pak delegát odkazuje na instanci i na metodu. Poté, když je vyvolán delegát, je volána zadaná metoda zadané instance.  
  
 Operátor `AddressOf` lze použít jako operand konstruktoru delegáta nebo jej lze použít v kontextu, ve kterém může být typ delegáta určen kompilátorem.  
  
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
