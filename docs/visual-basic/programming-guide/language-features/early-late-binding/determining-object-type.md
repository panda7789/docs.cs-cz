---
title: Určení typu objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 4014bef2e0c27a0f6a684bc1ed95019f392062a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050516"
---
# <a name="determining-object-type-visual-basic"></a>Určení typu objektu (Visual Basic)
Generický objekt proměnné (tedy proměnné můžete deklarovat jako `Object`) může obsahovat objekty z jiné třídy. Při použití proměnné typu `Object`, možná budete muset provést různé akce na základě třídy objektu; například nemusí podporovat některé objekty určité vlastnosti nebo metody. Visual Basic poskytuje dva prostředky určující, jaký typ objektu je uložen v proměnné objektu: `TypeName` funkce a `TypeOf...Is` operátor.  
  
## <a name="typename-and-typeofis"></a>Vlastnosti TypeName a TypeOf... Je  
 `TypeName` Funkce vrátí řetězec a je nejlepší volbou, pokud potřebujete uložit nebo zobrazit název třídy objektu, jak je znázorněno v následujícím fragmentu kódu:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is` Operátor je nejlepší volbou pro testování typ objektu, protože je mnohem rychlejší než porovnání odpovídající řetězec pomocí `TypeName`. Následující fragment kódu používá `TypeOf...Is` v rámci `If...Then...Else` – příkaz:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Tady je termín slovo upozornění. `TypeOf...Is` Operátor vrátí `True` Pokud objekt je určitého typu nebo je odvozen z určitého typu. Téměř vše, co dělat s jazykem Visual Basic zahrnuje objekty, které obsahují některé prvky, které nejsou běžně považují za objekty, jako jsou řetězce a celá čísla. Tyto objekty jsou odvozeny z a dědí z metody <xref:System.Object>. Po uplynutí `Integer` a vyhodnocené s `Object`, `TypeOf...Is` operátor vrátí `True`. Následující příklad uvádí, že parametr `InParam` je oba směry `Object` a `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 Následující příklad používá obě `TypeOf...Is` a `TypeName` k určení typu objektu do ní předán v `Ctrl` argument. `TestObject` Volání procedur `ShowType` s tři různé typy ovládacích prvků.  
  
#### <a name="to-run-the-example"></a>Chcete-li spustit příklad  
  
1. Vytvořte nový projekt aplikace Windows a přidejte <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Windows.Forms.CheckBox> ovládacího prvku a <xref:System.Windows.Forms.RadioButton> ovládacího prvku na formuláři.  
  
2. Pomocí tlačítka na formuláři, zavolejte `TestObject` postup.  
  
3. Přidejte následující kód do svého formuláře:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Volání vlastnosti nebo metody pomocí názvu řetězce](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz If...Then...Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Datový typ Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
