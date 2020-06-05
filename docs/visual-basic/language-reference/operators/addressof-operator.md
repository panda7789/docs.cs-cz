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
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372061"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf – operátor (Visual Basic)
Vytvoří instanci delegáta, která odkazuje na konkrétní proceduru.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Součásti  
 `procedurename`  
 Povinná hodnota. Určuje proceduru, na kterou má nově vytvořený delegát odkazovat.  
  
## <a name="remarks"></a>Poznámky  
 `AddressOf`Operátor vytvoří delegáta, který odkazuje na proceduru nebo funkci určenou parametrem `procedurename` . Pokud je zadaná procedura metodou instance, pak delegát odkazuje na instanci i na metodu. Poté, když je vyvolán delegát, je volána zadaná metoda zadané instance.  
  
 `AddressOf`Operátor lze použít jako operand konstruktoru delegáta nebo jej lze použít v kontextu, ve kterém lze určit typ delegáta kompilátorem.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `AddressOf` operátor k určení delegáta pro zpracování `Click` události tlačítka.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `AddressOf` operátor k určení spouštěcí funkce pro vlákno.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také

- [Declare – příkaz](../statements/declare-statement.md)
- [Function – příkaz](../statements/function-statement.md)
- [Sub – příkaz](../statements/sub-statement.md)
- [Delegáti](../../programming-guide/language-features/delegates/index.md)
