---
title: IsTrue – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370645"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue – operátor (Visual Basic)
Určuje, zda je výraz `True` .  
  
 Nemůžete volat `IsTrue` explicitně v kódu, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `OrElse` klauzulí. Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v `OrElse` klauzuli, je nutné definovat `IsTrue` v této třídě nebo struktuře.  
  
 Kompilátor považuje `IsTrue` operátory a `IsFalse` za *spárované páry*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.  
  
## <a name="compiler-use-of-istrue"></a>Použití kompilátoru true  
 Pokud jste definovali třídu nebo strukturu, můžete použít proměnnou daného typu v `For` `If` příkazu,, `Else If` nebo `While` nebo v `When` klauzuli. Pokud to uděláte, kompilátor vyžaduje operátor, který převede typ na hodnotu, aby mohl `Boolean` otestovat podmínku. Vyhledá vhodný operátor v následujícím pořadí:  
  
1. Rozšiřující operátor převodu z vaší třídy nebo struktury na `Boolean` .  
  
2. Rozšiřující operátor převodu z vaší třídy nebo struktury na `Boolean?` .  
  
3. `IsTrue`Operátor pro třídu nebo strukturu.  
  
4. Zužující převod na `Boolean?` , který nezahrnuje převod z `Boolean` na `Boolean?` .  
  
5. Zúžený operátor převodu z vaší třídy nebo struktury na `Boolean` .  
  
 Pokud jste nedefinovali převod na `Boolean` `IsTrue` operátor nebo, kompilátor signalizuje chybu.  
  
> [!NOTE]
> `IsTrue`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys struktury, která obsahuje definice pro `IsFalse` `IsTrue` operátory a.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také

- [IsFalse – operátor](isfalse-operator.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse – operátor](orelse-operator.md)
