---
title: Volný převod delegáta (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: c4a41bf74716a6ea7d3c1139651834acccf27657
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Volný převod delegáta (Visual Basic)
Volný převod delegáta umožňuje přiřadit předplatných a funkce na delegáty nebo obslužné rutiny i v případě, že jejich podpisy nejsou identické. Vazba na delegáty tedy stane konzistentní s vazbou již povolena pro volání metod.  
  
## <a name="parameters-and-return-type"></a>Parametry a návratový typ  
 Místo podpis přesnou shodu, volný převod vyžaduje splnění následujících podmínek při `Option Strict` je nastaven na `On`:  
  
-   Rozšiřující převod musí existovat od datového typu parametru každý delegáta na datový typ parametru odpovídající funkce přiřazené nebo `Sub`. V následujícím příkladu, delegát `Del1` má jeden parametr `Integer`. Parametr `m` v přiřazené lambda výrazy musí mít datový typ, pro kterou je rozšiřující převod z `Integer`, jako například `Long` nebo `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Zužující převody jsou povoleny pouze tehdy, když `Option Strict` je nastaven na `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Rozšiřující převod musí existovat v opačném směru z návratový typ funkce přiřazené nebo `Sub` návratový typ delegáta. V následujících příkladech se musí text každého výrazu lambda přiřazené vyhodnotit datový typ, který rozšiřuje na `Integer` protože návratový typ `del1` je `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Pokud `Option Strict` je nastaven na `Off`, v obou směrech rozšiřující omezení je odebrána.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>Vynechání parametru specifikace  
 Volný delegáti taky umožňují zcela vynechejte parametr specifikace v metodě přiřazené:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Všimněte si, nelze zadat některé parametry a ostatní vynechejte.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 Umožňuje vynechat parametry je užitečné v situaci, jako je například definování obslužné rutiny události, které se podílejí několika komplexní parametry. Argumenty, které mají některé obslužné rutiny událostí se nepoužívají. Místo toho obslužná rutina přímý přístup k stavu ovládacího prvku, na kterém je zaregistrován události a ignoruje argumenty. Volný Delegáti umožňují vynechejte argumentů taková deklarace, pokud žádný výsledek nejednoznačnosti. V následujícím příkladu plně zadanou metodu `OnClick` může být přepsán jako `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf příklady  
 Lambda – výrazy se používají v předchozích příkladech snadno zjistit, aby typ relace. Však stejné zmírnění jsou povoleny pro přiřazení delegáta, které používají `AddressOf`, `Handles`, nebo `AddHandler`.  
  
 V následujícím příkladu funkce `f1`, `f2`, `f3`, a `f4` lze všechny přiřadit k `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 Následující příklad je platný jenom v případě `Option Strict` je nastaven na `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>Vrátí vyřazování – funkce  
 Volný převod delegáta umožňuje přiřadit funkce, která se `Sub` delegáta, efektivně ignoruje návratovou hodnotu funkce. Však nelze přiřadit `Sub` k delegáta funkce. V následujícím příkladu, adresy funkce `doubler` je přiřazena k `Sub` delegovat `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Postupy: předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
