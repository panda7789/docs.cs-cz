---
title: 'Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 9ca9a0ccdac3ac13429928233a0c09d58427ce74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665764"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic
A *výchozí vlastnost* je vlastnost třídy nebo struktury, který váš kód může přistupovat bez zadání ho. Při volání metody kódu názvy třídy nebo struktury, ale není vlastnost a kontext umožňuje přístup k vlastnosti, Visual Basic přeloží přístup k dané třídy nebo struktury výchozí vlastnost pokud existuje.  
  
 Třídy nebo struktury může mít maximálně jeden výchozí vlastnost. Můžete však přetížení výchozí vlastností a mají více než jednu verzi.  
  
 Další informace najdete v tématu [výchozí](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Chcete-li deklarovat výchozí vlastnosti  
  
1. Deklarujte vlastnost běžným způsobem. Nezadávejte `Shared` nebo `Private` – klíčové slovo.  
  
2. Zahrnout `Default` – klíčové slovo v deklaraci vlastnosti.  
  
3. Zadejte nejméně jeden parametr pro vlastnost. Nelze definovat výchozí vlastnost, která nevyužívá aspoň jeden argument.  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>K volání výchozí vlastnosti  
  
1. Deklarujte proměnnou obsahující typ třídy nebo struktury.  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. Použijte název proměnné pouze ve výrazu, kde by obvykle zahrnují název vlastnosti.  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. Použijte název proměnné se seznamem argumentů v závorkách. Výchozí vlastnost musí přebírat aspoň jeden argument.  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. Načíst výchozí hodnota vlastnosti, použijte název proměnné, se seznamem argumentů, ve výrazu nebo rovno (`=`) Přihlaste se příkazu přiřazení.  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. Pokud chcete nastavit výchozí hodnotu vlastnosti, použijte název proměnné, se seznamem argumentů, na levé straně příkazu přiřazení.  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. Výchozí název vlastnosti spolu s názvem proměnné, můžete zadat vždy, stejně jako by tomu pro přístup k žádné jiné vlastnosti.  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje výchozí vlastnost třídy.  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob volání výchozí vlastnosti `myProperty` ve třídě `class1`. Tři přiřazovací příkazy ukládání hodnot v `myProperty`a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání načte hodnoty.  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 Se nejčastěji používá výchozí vlastnost <xref:Microsoft.VisualBasic.Collection.Item%2A> vlastnost na různé třídy kolekcí.  
  
## <a name="robust-programming"></a>Robustní programování  
 Výchozí vlastnosti může vést k malé snížení zdrojového kódu – znaků, ale váš kód mohl provést obtížněji čitelný. Pokud volající kód není znáte třídy nebo struktury, když se vytváří odkaz na název třídy nebo struktury nemůže být určité Určuje, zda přistupuje k této referenční třídy nebo struktury samotné nebo výchozí vlastnost. To může vést k chybám kompilátoru nebo běhové logiky drobné chyby.  
  
 Můžete poněkud snížit pravděpodobnost vzniku chyby výchozí vlastnost vždy používat [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavení kompilátoru kontroly typů pro `On`.  
  
 Pokud máte v úmyslu použít předdefinované třídy nebo struktury v kódu, musíte určit, zda má výchozí vlastnosti a pokud ano, co její název je.  
  
 Z důvodu tyto nevýhody měli byste zvážit, není definování výchozí vlastnosti. Pro lepší čitelnost kódu byste také vzít v úvahu vždy odkazuje na všechny vlastnosti explicitně, dokonce i výchozí vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Default](../../../../visual-basic/language-reference/modifiers/default.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
