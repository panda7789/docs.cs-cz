---
title: Is – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 3cc0ae5f04358fbe6b2aabc50498f39ca7225164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370801"
---
# <a name="is-operator-visual-basic"></a>Is – operátor (Visual Basic)
Porovná dvě proměnné odkazu na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Libovolná `Boolean` hodnota.  
  
 `object1`  
 Povinná hodnota. Libovolný `Object` název.  
  
 `object2`  
 Povinná hodnota. Libovolný `Object` název.  
  
## <a name="remarks"></a>Poznámky  
 `Is`Operátor určuje, zda dva odkazy na objekt odkazují na stejný objekt. Ale neprovádí porovnávání hodnot. Pokud `object1` a `object2` oba odkazují na přesnou stejnou instanci objektu, `result` je `True` ; Pokud ne, `result` je `False` .  
  
 `Is`lze také použít s `TypeOf` klíčovým slovem pro vytvoření `TypeOf` výrazu... `Is` , který testuje, zda je objektová proměnná kompatibilní s datovým typem.  
  
> [!NOTE]
> `Is`Klíčové slovo se používá také v rámci [výběru... Příkaz Case](../statements/select-case-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Is` operátor pro porovnání párů odkazů na objekty. Výsledky jsou přiřazeny k `Boolean` hodnotě, která představuje, zda jsou dva objekty identické.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak ukazuje předchozí příklad, lze použít `Is` operátor k otestování počátečních a pozdních vázaných objektů.  
  
## <a name="see-also"></a>Viz také

- [TypeOf – operátor](typeof-operator.md)
- [IsNot – operátor](isnot-operator.md)
- [Operátory porovnání v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
