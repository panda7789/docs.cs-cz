---
title: 'Postupy: deklarace a volání výchozí vlastnosti'
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
ms.openlocfilehash: b01188ed8a9ff4da95a6975dcac3509625fdffb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349686"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic
*Výchozí vlastnost* je vlastnost třídy nebo struktury, ke které má váš kód přístup bez zadání. Při volání názvů kódu třída nebo struktura, ale ne vlastnost, a kontext umožňuje přístup k vlastnosti, Visual Basic přeloží přístup k výchozí vlastnosti této třídy nebo struktury, pokud existuje.  
  
 Třída nebo struktura může mít nejvýše jednu výchozí vlastnost. Můžete však přetížit výchozí vlastnost a mít více než jednu verzi.  
  
 Další informace najdete v tématu [výchozí](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Deklarace výchozí vlastnosti  
  
1. Deklarujte vlastnost normálním způsobem. Nezadávejte klíčové slovo `Shared` ani `Private`.  
  
2. Zahrňte klíčové slovo `Default` v deklaraci vlastnosti.  
  
3. Zadejte alespoň jeden parametr pro vlastnost. Nelze definovat výchozí vlastnost, která nepřijímá alespoň jeden argument.  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>Volání výchozí vlastnosti  
  
1. Deklaruje proměnnou obsahujícího typu třídy nebo struktury.  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. Použijte název proměnné samotný ve výrazu, kde byste normálně zahrnuli název vlastnosti.  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. Použijte název proměnné se seznamem argumentů v závorkách. Výchozí vlastnost musí mít alespoň jeden argument.  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. Chcete-li načíst výchozí hodnotu vlastnosti, použijte název proměnné se seznamem argumentů ve výrazu nebo za znaménkem EQUAL (`=`) v příkazu přiřazení.  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. Chcete-li nastavit výchozí hodnotu vlastnosti, použijte název proměnné s seznamem argumentů na levé straně příkazu přiřazení.  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. Název výchozí vlastnosti můžete vždy zadat společně s názvem proměnné, stejně jako při přístupu k libovolné jiné vlastnosti.  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje výchozí vlastnost třídy.  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat výchozí vlastnost `myProperty` ve třídě `class1`. Tři příkazy přiřazení ukládají hodnoty do `myProperty`a volání <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> přečte hodnoty.  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 Nejběžnějším použitím výchozí vlastnosti je vlastnost <xref:Microsoft.VisualBasic.Collection.Item%2A> v různých třídách kolekcí.  
  
## <a name="robust-programming"></a>Robustní programování  
 Výchozí vlastnosti můžou mít za následek malé snížení počtu znaků zdrojového kódu, ale můžou ztížit čtení kódu. Pokud volající kód není obeznámen s vaší třídou nebo strukturou, při odkazování na název třídy nebo struktury nemůže být jisté, zda tento odkaz přistupuje k třídě nebo struktuře samotné nebo výchozí vlastnosti. To může vést k chybám kompilátoru nebo k drobným chybám logiky run-time.  
  
 Můžete trochu snížit šanci na chyby výchozích vlastností – vždy pomocí [příkazu Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavit kontrolu typu kompilátoru na `On`.  
  
 Pokud plánujete použít předdefinovanou třídu nebo strukturu v kódu, je nutné určit, zda má výchozí vlastnost, a pokud ano, jaký je její název.  
  
 Z důvodu těchto nevýhody byste měli zvážit, že nedefinujete výchozí vlastnosti. V případě čitelnosti kódu byste měli také zvážit možnost vždy odkazovat na všechny vlastnosti, a to i na výchozí vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Default](../../../../visual-basic/language-reference/modifiers/default.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
