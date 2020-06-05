---
title: IsFalse – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 7c5ad5fa0b72370eeb19fbaced88807570467552
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370671"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse – operátor (Visual Basic)
Určuje, zda je výraz `False` .  
  
 Nemůžete volat `IsFalse` explicitně v kódu, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `AndAlso` klauzulí. Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v `AndAlso` klauzuli, je nutné definovat `IsFalse` v této třídě nebo struktuře.  
  
 Kompilátor považuje `IsFalse` operátory a `IsTrue` za *spárované páry*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.  
  
> [!NOTE]
> `IsFalse`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys struktury, která obsahuje definice pro `IsFalse` `IsTrue` operátory a.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také

- [IsTrue – operátor](istrue-operator.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso – operátor](andalso-operator.md)
