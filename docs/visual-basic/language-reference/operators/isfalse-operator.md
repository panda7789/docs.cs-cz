---
title: IsFalse – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349520"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse – operátor (Visual Basic)
Určuje, zda je výraz `False`.  
  
 Ve svém kódu nemůžete volat `IsFalse` explicitně, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `AndAlso` klauzulí. Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v klauzuli `AndAlso`, je nutné definovat `IsFalse` v této třídě nebo struktuře.  
  
 Kompilátor považuje operátory `IsFalse` a `IsTrue` za *spárovaný pár*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.  
  
> [!NOTE]
> Operátor `IsFalse` může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má jeho operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys struktury, která obsahuje definice pro operátory `IsFalse` a `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
