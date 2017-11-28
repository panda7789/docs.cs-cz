---
title: "TypeOf – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-operator-visual-basic"></a>TypeOf – operátor (Visual Basic)
Porovná proměnná odkaz objektu k datovému typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Vrátí. A `Boolean` hodnotu.  
  
 `objectexpression`  
 Požadováno. Jakýkoli výraz, jehož výsledkem odkazového typu.  
  
 `typename`  
 Požadováno. Všechna data, zadejte název.  
  
## <a name="remarks"></a>Poznámky  
 `TypeOf` Operátor určuje, zda běhu typ `objectexpression` je kompatibilní s `typename`. Kompatibility závisí na typu kategorii `typename`. Následující tabulka uvádí, jakým způsobem je určován kompatibility.  
  
|Typ kategorie`typename`|Kritérium kompatibility|  
|---------------------------------|-----------------------------|  
|Třída|`objectexpression`je typu `typename` nebo dědí z`typename`|  
|Struktura|`objectexpression`je typu`typename`|  
|Rozhraní|`objectexpression`implementuje `typename` nebo dědí z třídy, který implementuje`typename`|  
  
 Pokud běhu typ `objectexpression` splňuje kritéria kompatibility `result` je `True`. V opačném `result` je `False`.  Pokud `objectexpression` má hodnotu null, pak `TypeOf`... `Is` vrátí `False`, a... `IsNot` vrátí `True`.  
  
 `TypeOf`vždy používá s `Is` – klíčové slovo vytvořit `TypeOf`... `Is` výrazu, nebo pomocí `IsNot` – klíčové slovo vytvořit `TypeOf`... `IsNot` výraz.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `TypeOf`... `Is` výrazy pro testování kompatibility typu dva objektu referenční proměnné s různými datovými typy.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 Proměnná `refInteger` má typ spuštění `Integer`. Je kompatibilní s `Integer` , ale ne při `Double`. Proměnná `refForm` má typ spuštění <xref:System.Windows.Forms.Form>. Je kompatibilní s <xref:System.Windows.Forms.Form> je její typ se totiž <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.Windows.Forms.Control>a s <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, který implementuje <xref:System.ComponentModel.IComponent>. Ale `refForm` není kompatibilní s <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Viz také  
 [Is – operátor](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot – operátor](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
