---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966925"
---
# <a name="isnot-operator-visual-basic"></a>IsNot – operátor (Visual Basic)
Porovná dvě proměnné odkazu na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. `Boolean` Hodnota.  
  
 `object1`  
 Povinný parametr. Jakákoli `Object` proměnná nebo výraz.  
  
 `object2`  
 Povinný parametr. Jakákoli `Object` proměnná nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 `IsNot` Operátor určuje, zda dva odkazy na objekt odkazují na různé objekty. Ale neprovádí porovnávání hodnot. Pokud `object1` a `False` `result` `result` `True`oba odkazují na přesnou stejnou instanci objektu, je; Pokud ne, je. `object2`  
  
 `IsNot`je opakem `Is` operátoru. Výhodou `IsNot` je, že se můžete vyhnout nevhodným `Not` syntaxem s a `Is`, což může být obtížné ho přečíst.  
  
 Operátory `Is` a`IsNot` můžete použít k otestování objektů s časnou vazbou i s pozdní vazbou.  
  
> [!NOTE]
> Operátor nelze použít pro porovnání výrazů vrácených `TypeOf` z operátoru. `IsNot` Místo toho je nutné použít `Not` operátory a. `Is`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Is` operátor `IsNot` i operátor k provedení stejného porovnání.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Postupy: Testovat, zda jsou dva objekty stejné](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
