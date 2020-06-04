---
title: Určení typu objektu
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 3b1c4ad0ab4fd8d2897aff6ad9097cdc81272455
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410641"
---
# <a name="determining-object-type-visual-basic"></a>Určení typu objektu (Visual Basic)
Proměnné obecného objektu (to znamená, že proměnné, jako `Object` ), mohou uchovávat objekty z libovolné třídy. Při použití proměnných typu `Object` může být nutné provést různé akce na základě třídy objektu; například některé objekty nemusí podporovat určitou vlastnost nebo metodu. Visual Basic poskytuje dva způsoby určení, který typ objektu je uložen v proměnné objektu: `TypeName` funkce a `TypeOf...Is` operátor.  
  
## <a name="typename-and-typeofis"></a>TypeName a TypeOf... Dojde  
 `TypeName`Funkce vrátí řetězec a je nejvhodnější volbou, pokud potřebujete uložit nebo zobrazit název třídy objektu, jak je znázorněno v následujícím fragmentu kódu:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`Operátor je nejlepší volbou pro testování typu objektu, protože je mnohem rychlejší než ekvivalentní porovnávání řetězců pomocí `TypeName` . Následující fragment kódu používá `TypeOf...Is` v rámci `If...Then...Else` příkazu:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Zde je uvedeno slovo s upozorněním. `TypeOf...Is`Operátor vrátí `True` , zda je objekt určitého typu nebo je odvozen z konkrétního typu. Téměř všechno, co děláte s Visual Basic zahrnuje objekty, které obsahují některé prvky, které nejsou obvykle považovány za objekty, jako jsou například řetězce a celá čísla. Tyto objekty jsou odvozeny z a dědí metody z <xref:System.Object> . Při předání `Integer` a vyhodnocení pomocí `Object` `TypeOf...Is` operátoru vrátí operátor `True` . Následující příklad hlásí, že parametr `InParam` je `Object` a `Integer` :  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 Následující příklad používá jak `TypeOf...Is` a `TypeName` k určení typu objektu předaného do něj v `Ctrl` argumentu. `TestObject`Procedura volá `ShowType` tři různé druhy ovládacích prvků.  
  
#### <a name="to-run-the-example"></a>Chcete-li spustit příklad  
  
1. Vytvořte nový projekt aplikace pro Windows a přidejte ovládací <xref:System.Windows.Forms.Button> prvek, <xref:System.Windows.Forms.CheckBox> ovládací prvek a ovládací prvek <xref:System.Windows.Forms.RadioButton> do formuláře.  
  
2. Z tlačítka na formuláři zavolejte `TestObject` proceduru.  
  
3. Do formuláře přidejte následující kód:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Volání vlastnosti nebo metody pomocí názvu řetězce](calling-a-property-or-method-using-a-string-name.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
- [If...Then...Else – příkaz](../../../language-reference/statements/if-then-else-statement.md)
- [Datový typ String](../../../language-reference/data-types/string-data-type.md)
- [Integer – datový typ](../../../language-reference/data-types/integer-data-type.md)
