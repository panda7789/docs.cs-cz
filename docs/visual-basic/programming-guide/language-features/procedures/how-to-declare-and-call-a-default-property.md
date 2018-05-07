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
ms.openlocfilehash: 7805ee4dcd4bad0d0624c97ccc25232e9bc31ba4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic
A *výchozí vlastnost* je vlastnost třídu nebo strukturu, která může kód přistupovat bez zadání ho. Při volání metody kód názvy třídu nebo strukturu, ale není vlastnost a kontext umožňuje přístup k vlastnosti, Visual Basic přeloží přístup třídy nebo struktury je výchozí vlastnost, pokud existuje.  
  
 Třídu nebo strukturu může mít maximálně jeden výchozí vlastnost. Můžete však přetížení výchozí vlastnost a mít více než jednu verzi.  
  
 Další informace najdete v tématu [výchozí](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Deklarace výchozí vlastnosti  
  
1.  Deklarujte vlastnost běžným způsobem. Nezadávejte `Shared` nebo `Private` – klíčové slovo.  
  
2.  Zahrnout `Default` – klíčové slovo v deklarace vlastnosti.  
  
3.  Zadejte jeden nebo více parametrů pro vlastnost. Nelze definovat výchozí vlastnost, která nevyužívá alespoň jeden argument.  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>K volání výchozí vlastnosti  
  
1.  Deklarace proměnné obsahující třídu nebo strukturu typu.  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Použijte název proměnné samostatně ve výrazu, kde bude obvykle zahrnovat název vlastnosti.  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Postupujte podle názvu proměnné s seznam argumentů v závorkách. Výchozí vlastnost vyžaduje alespoň jeden argument.  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Načíst výchozí hodnotu vlastnosti, použijte název proměnné, s seznam argumentů, ve výrazu, nebo rovno (`=`) přihlásit příkazu přiřazení.  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Pokud chcete nastavit výchozí hodnotu vlastnosti, použijte název proměnné, s seznam argumentů, na levé straně příkazu přiřazení.  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Vždy můžete výchozí název vlastnosti společně s názvem proměnné, stejně, jako byste to udělali pro přístup k libovolné jiné vlastnosti.  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí výchozí vlastnost třídy.  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak volat výchozí vlastnost `myProperty` na třídě `class1`. Příkazy tři přiřazení ukládání hodnot v `myProperty`a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání čte hodnoty.  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 Se nejčastěji používá výchozí vlastnosti <xref:Microsoft.VisualBasic.Collection.Item%2A> vlastnost na různé třídy kolekce.  
  
## <a name="robust-programming"></a>Robustní programování  
 Výchozí vlastnosti může vést ke snížení malé znaky zdrojový kód, ale jejich byl váš kód obtížněji čitelný. Pokud volání kód není obeznámeni s třídě nebo struktuře, když má odkaz na název třídy nebo struktura nemůže být určité jestli přistupuje k tento odkaz, třídu nebo strukturu sám sebe nebo výchozí vlastnost. To může vést k chybám kompilátoru nebo jemně běhu logické chyby.  
  
 Poněkud může snížit pravděpodobnost chyby výchozí vlastnost vždy pomocí [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavte typ kompilátoru kontrole `On`.  
  
 Pokud máte v úmyslu použít předdefinované třídu nebo strukturu ve vašem kódu, je třeba určit, jestli má výchozí vlastnost a pokud ano, jaké jeho název je.  
  
 Z důvodu tyto nevýhody měli byste zvážit není definování výchozí vlastnosti. Kód čitelnější měli také zvážit vždy odkazující na všechny vlastnosti explicitně, i výchozí vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Procedury vlastnosti](./property-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Default](../../../../visual-basic/language-reference/modifiers/default.md)  
 [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)  
 [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)  
 [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)  
 [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)  
 [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
