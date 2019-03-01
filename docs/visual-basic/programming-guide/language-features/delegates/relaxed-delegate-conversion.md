---
title: Volný převod delegáta (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 96941754f17326893437cdcf83c588880e010cc0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979503"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Volný převod delegáta (Visual Basic)
Volný převod delegáta umožňuje přiřadit typu Sub a funkce na delegáty nebo obslužné rutiny i v případě, že jejich podpisy nejsou identické. Proto vazbu na delegáty stane konzistentní s vazbou již povolena pro volání metod.  
  
## <a name="parameters-and-return-type"></a>Parametry a návratový typ  
 Místo podpis přesnou shodu volný převod vyžaduje splnění následujících podmínek při `Option Strict` je nastavena na `On`:  
  
-   Rozšiřující převod musí existovat od datového typu každý parametr delegáta na datový typ odpovídající parametr přiřazené funkce nebo `Sub`. V následujícím příkladu, delegát `Del1` má jeden parametr, `Integer`. Parametr `m` v přiřazené lambda výrazy musí mít datový typ, pro kterou je rozšiřující převod z `Integer`, jako například `Long` nebo `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Zužující převody jsou povolené jenom v případě `Option Strict` je nastavena na `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
-   Rozšiřující převod musí existovat v opačném směru z návratového typu funkce přiřazené nebo `Sub` na návratový typ delegáta. V následujících příkladech text každého přiřazené lambda výraz se musí vyhodnotit na datový typ, který rozšiřuje na `Integer` protože návratový typ `del1` je `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Pokud `Option Strict` je nastavena na `Off`, rozšiřující omezení se už v obou směrech.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Vynechání specifikace parametru  
 Uvolněné delegáty lze také kompletně vynechat specifikace parametru v metodě přiřazené:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Mějte na paměti, že nelze zadat některé parametry a ostatní vynechat.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Umožňuje vynechat je užitečné v situaci, například definování obslužné rutiny události, kde se podílejí několik složité parametry. Nejsou použity argumenty, které mají některé obslužné rutiny události. Místo toho obslužnou rutinu přímý přístup k stavu ovládacího prvku, na kterém je zaregistrován události a ignoruje argumenty. Uvolněné delegáty umožňují vynechejte argumenty v těchto prohlášení, pokud žádný výsledek nejednoznačnosti. V následujícím příkladu, plně zadanou metodu `OnClick` může být přepsán ve formátu `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Příklady AddressOf  
 Výrazy lambda se používají v předchozích příkladech k usnadnění vztahům typů zobrazíte. Ale stejné zmírnění jsou povolené pro přiřazení delegáta, které používají `AddressOf`, `Handles`, nebo `AddHandler`.  
  
 V následujícím příkladu se funkce `f1`, `f2`, `f3`, a `f4` je všechny možné přiřadit k `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Následující příklad je platný jenom v případě `Option Strict` je nastavena na `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Přetažení funkce vrátí  
 Volný převod delegáta umožňuje přiřadit funkce, která se `Sub` delegáta, efektivní systém ignoroval návratovou hodnotu funkce. Však nelze přiřadit `Sub` delegáta funkce. V následujícím příkladu, adresu funkce `doubler` přiřazen `Sub` delegovat `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Viz také:
- [Výrazy lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
