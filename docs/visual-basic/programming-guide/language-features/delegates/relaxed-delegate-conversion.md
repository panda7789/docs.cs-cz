---
title: Volný převod delegáta
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: a581ffae77c496908d2e4e38df53491a54ae2ab8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410667"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Volný převod delegáta (Visual Basic)
Odlehčený převod delegáta umožňuje přiřadit vlastníky a funkce delegátům nebo obslužným rutinám, i když jejich signatury nejsou identické. Proto vazba na delegáty se bude shodovat s vazbou, která je již povolena pro vyvolání metod.  
  
## <a name="parameters-and-return-type"></a>Parametry a návratový typ  
 Místo přesné shody signatury vyžaduje odlehčený převod, aby byly splněny následující podmínky, pokud `Option Strict` je nastavena na `On` :  
  
- Rozšiřující převod musí existovat z datového typu každého parametru delegáta na datový typ odpovídajícího parametru přiřazené funkce nebo `Sub` . V následujícím příkladu `Del1` má delegát jeden parametr, a `Integer` . Parametr `m` v přiřazených výrazech lambda musí mít datový typ, pro který existuje rozšiřující převod z `Integer` , například `Long` nebo `Double` .  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Zužující převody jsou povoleny pouze v případě `Option Strict` , že je nastavena na `Off` .  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Rozšiřující převod musí existovat v opačném směru od návratového typu přiřazené funkce nebo `Sub` na návratový typ delegáta. V následujících příkladech se tělo každého přiřazeného výrazu lambda musí vyhodnotit na datový typ, který se rozšíří, `Integer` protože návratový typ `del1` je `Integer` .  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Pokud `Option Strict` je nastavená na `Off` , rozšiřující omezení se odebere v obou směrech.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Vynechávání specifikací parametrů  
 Odlehčení Delegáti vám také umožní zcela vynechat specifikace parametrů v přiřazené metodě:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Všimněte si, že nemůžete zadat některé parametry a vynechat jiné.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Možnost vynechat parametry je užitečná v situaci, jako je například definování obslužné rutiny události, kde je zapojeno několik složitých parametrů. Argumenty pro některé obslužné rutiny událostí se nepoužívají. Místo toho obslužná rutina přímo přistupuje ke stavu ovládacího prvku, na kterém je událost zaregistrována, a ignoruje argumenty. Odlehčení Delegáti umožňují vynechat argumenty v těchto prohlášeních, pokud výsledek nejednoznačnosti. V následujícím příkladu lze úplnou zadanou metodu `OnClick` přepsat jako `RelaxedOnClick` .  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf – příklady  
 Výrazy lambda se používají v předchozích příkladech k usnadnění zobrazení vztahů typů. U přiřazení delegátů, které používají, nebo jsou však povolena stejná `AddressOf` zmírnění `Handles` `AddHandler` .  
  
 V následujícím příkladu funkce,, `f1` `f2` `f3` a `f4` mohou být přiřazeny k `Del1` .  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Následující příklad je platný pouze v případě `Option Strict` , že je nastavena na `Off` .  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Vyhození funkcí vrátí  
 Odlehčený převod delegáta umožňuje přiřadit funkci `Sub` delegátovi a efektivně tak ignorovat vrácenou hodnotu funkce. Nemůžete však přiřadit `Sub` delegáta funkce. V následujícím příkladu je adresa funkce `doubler` přiřazena `Sub` delegátovi `Del3` .  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Viz také

- [Výrazy lambda](../procedures/lambda-expressions.md)
- [Rozšíření a zúžení převodů](../data-types/widening-and-narrowing-conversions.md)
- [Delegáti](index.md)
- [Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](how-to-pass-procedures-to-another-procedure.md)
- [Odvození místního typu](../variables/local-type-inference.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
