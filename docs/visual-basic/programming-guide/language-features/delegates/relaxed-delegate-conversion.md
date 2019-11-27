---
title: Volný převod delegáta
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345220"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Volný převod delegáta (Visual Basic)
Odlehčený převod delegáta umožňuje přiřadit vlastníky a funkce delegátům nebo obslužným rutinám, i když jejich signatury nejsou identické. Proto vazba na delegáty se bude shodovat s vazbou, která je již povolena pro vyvolání metod.  
  
## <a name="parameters-and-return-type"></a>Parametry a návratový typ  
 V případě shody přes přesný podpis vyžaduje odlehčený převod, aby při `Option Strict` nastavené na `On`byly splněné následující podmínky:  
  
- Rozšiřující převod musí existovat z datového typu každého parametru delegáta na datový typ odpovídajícího parametru přiřazené funkce nebo `Sub`. V následujícím příkladu má delegát `Del1` jeden parametr, `Integer`. Parametr `m` v přiřazených výrazech lambda musí mít datový typ, pro který existuje rozšiřující převod z `Integer`, jako je například `Long` nebo `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Zužující převody jsou povoleny pouze v případě, že je `Option Strict` nastaveno na hodnotu `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Rozšiřující převod musí existovat v opačném směru od návratového typu přiřazené funkce nebo `Sub` k návratový typ delegáta. V následujících příkladech se tělo každého přiřazeného výrazu lambda musí vyhodnotit na datový typ, který se rozšíří na `Integer`, protože návratový typ `del1` je `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Pokud je `Option Strict` nastavené na `Off`, rozšiřující omezení se odebere v obou směrech.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Vynechávání specifikací parametrů  
 Odlehčení Delegáti vám také umožní zcela vynechat specifikace parametrů v přiřazené metodě:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Všimněte si, že nemůžete zadat některé parametry a vynechat jiné.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Možnost vynechat parametry je užitečná v situaci, jako je například definování obslužné rutiny události, kde je zapojeno několik složitých parametrů. Argumenty pro některé obslužné rutiny událostí se nepoužívají. Místo toho obslužná rutina přímo přistupuje ke stavu ovládacího prvku, na kterém je událost zaregistrována, a ignoruje argumenty. Odlehčení Delegáti umožňují vynechat argumenty v těchto prohlášeních, pokud výsledek nejednoznačnosti. V následujícím příkladu lze jako `RelaxedOnClick`přepsat úplnou zadanou metodu `OnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf – příklady  
 Výrazy lambda se používají v předchozích příkladech k usnadnění zobrazení vztahů typů. U přiřazení delegátů, které používají `AddressOf`, `Handles`nebo `AddHandler`je však povoleno stejné zmírnit.  
  
 V následujícím příkladu funkce `f1`, `f2`, `f3`a `f4`, mohou být přiřazeny `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Následující příklad je platný, pouze pokud je `Option Strict` nastaveno na `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Vyhození funkcí vrátí  
 Odlehčený převod delegáta umožňuje přiřadit funkci delegátovi `Sub` a efektivně tak ignorovat vrácenou hodnotu funkce. Nemůžete však přiřadit `Sub` delegátovi funkce. V následujícím příkladu je adresa funkce `doubler` přiřazená `Sub` delegátům `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Postupy: Předání procedur jinému postupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
