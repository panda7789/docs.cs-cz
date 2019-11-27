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
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345190"
---
# <a name="determining-object-type-visual-basic"></a>Určení typu objektu (Visual Basic)
Proměnné obecného objektu (to znamená, proměnné, které deklarujete jako `Object`) mohou uchovávat objekty z libovolné třídy. Při použití proměnných typu `Object`může být nutné provést různé akce na základě třídy objektu; Některé objekty například nemusí podporovat určitou vlastnost nebo metodu. Visual Basic poskytuje dva způsoby určení, který typ objektu je uložen v proměnné objektu: funkce `TypeName` a operátor `TypeOf...Is`.  
  
## <a name="typename-and-typeofis"></a>TypeName a TypeOf... Dojde  
 Funkce `TypeName` vrací řetězec a je nejvhodnější volbou, pokud potřebujete uložit nebo zobrazit název třídy objektu, jak je znázorněno v následujícím fragmentu kódu:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 Operátor `TypeOf...Is` je nejlepší volbou pro testování typu objektu, protože je mnohem rychlejší než ekvivalentní porovnávání řetězců pomocí `TypeName`. Následující fragment kódu používá `TypeOf...Is` v rámci příkazu `If...Then...Else`:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Zde je uvedeno slovo s upozorněním. Operátor `TypeOf...Is` vrátí `True`, pokud je objekt určitého typu nebo je odvozen z konkrétního typu. Téměř všechno, co děláte s Visual Basic zahrnuje objekty, které obsahují některé prvky, které nejsou obvykle považovány za objekty, jako jsou například řetězce a celá čísla. Tyto objekty jsou odvozeny z a dědí metody z <xref:System.Object>. Při předání `Integer` a vyhodnocování pomocí `Object`vrací operátor `TypeOf...Is` `True`. Následující příklad hlásí, že parametr `InParam` je `Object` a `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 Následující příklad používá `TypeOf...Is` a `TypeName` k určení typu objektu, který je předaný do něj v argumentu `Ctrl`. Procedura `TestObject` volá `ShowType` se třemi různými druhy ovládacích prvků.  
  
#### <a name="to-run-the-example"></a>Chcete-li spustit příklad  
  
1. Vytvořte nový projekt aplikace pro Windows a do formuláře přidejte ovládací prvek <xref:System.Windows.Forms.Button>, ovládací prvek <xref:System.Windows.Forms.CheckBox> a ovládací prvek <xref:System.Windows.Forms.RadioButton>.  
  
2. Z tlačítka na formuláři zavolejte proceduru `TestObject`.  
  
3. Do formuláře přidejte následující kód:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Volání vlastnosti nebo metody pomocí názvu řetězce](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Příkaz If...Then...Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Datový typ Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
