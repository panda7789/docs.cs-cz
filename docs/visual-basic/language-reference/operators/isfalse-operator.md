---
title: IsFalse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917146"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse – operátor (Visual Basic)
Určuje, zda je `False`výraz.  
  
 Nemůžete `IsFalse` volat explicitně v kódu, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `AndAlso` klauzulí. Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v `AndAlso` klauzuli, je nutné definovat `IsFalse` v této třídě nebo struktuře.  
  
 Kompilátor považuje `IsFalse` operátory a `IsTrue` za *spárované páry*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.  
  
> [!NOTE]
> Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury. `IsFalse` Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys struktury, která obsahuje definice pro `IsFalse` operátory a. `IsTrue`  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
