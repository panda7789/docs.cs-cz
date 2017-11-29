---
title: "Vlastnosti a metody přetečení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a872540716941ccd0dbb8b058508b89ce26a988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Vlastnosti a metody přetečení (Visual Basic)
Přetížení je vytvoření více procedur, konstruktoru instance nebo vlastnost v třídě se stejným názvem, ale s typy argumentů jiný.  
  
## <a name="overloading-usage"></a>Přetížení využití  
 Přetížení je obzvláště užitečné, když objektový model stanoví, že nepoužijete identické názvy postupy, které působí na různé datové typy. Například může mít třídy, která může zobrazit několik různých datových typů `Display` postupy, které vypadají takto:  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 Bez přetížení, museli byste vytvořit jedinečné názvy pro každý postup, i když udělají samé, jak ukazuje následující:  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 Přetížení usnadňuje použít vlastností nebo metod, protože poskytuje výběru datových typů, které lze použít. Například přetížené `Display` popsané dříve nelze volat metodu s žádným z následujících řádků kódu:  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 V době běhu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] volání správný postup na základě datové typy parametrů můžete zadat.  
  
## <a name="overloading-rules"></a>Přetížení pravidla  
 Vytvoříte člena přetížená pro třídu přidáním dva nebo více vlastností nebo metod se stejným názvem. S výjimkou přetížené odvozené členy každý přetížené člen musí mít jiný parametr seznamy a následující položky nelze použít jako rozdílné funkce v případě přetížení vlastnosti nebo postup:  
  
-   Modifikátory, jako například `ByVal` nebo `ByRef`, která platí pro člen, nebo parametry člena.  
  
-   Názvy parametrů  
  
-   Návratové typy procedury  
  
 `Overloads` – Klíčové slovo je nepovinný, pokud přetížení, ale pokud existují přetížený člen používá `Overloads` – klíčové slovo, pak všechny ostatní přetěžované členy se stejným názvem musíte zadat také toto klíčové slovo.  
  
 Odvozené třídy mohou přetížení zděděné členy se členy, kteří mají stejné parametry a typy parametrů, tento proces se označuje jako *stínový provoz podle názvu a podpis*. Pokud `Overloads` – klíčové slovo se používá, když stínováním podle názvu a podpis, implementaci odvozené třídě člena použije místo implementace v základní třídě a dalšími přetíženími pro tento člen bude k dispozici pro instance odvozené třídy.  
  
 Pokud `Overloads` – klíčové slovo je vynechán, při přetížení zděděného členu s člena, který má stejné parametry a typy parametrů a potom přetížení se nazývá *stínový provoz podle názvu*. Stínový provoz podle názvu nahrazuje zděděné implementace členem, a dalšími přetíženími umožňuje pro instance odvozené třídě a jeho decedents není dostupná.  
  
 `Overloads` a `Shadows` Modifikátory nelze kombinovat s stejné vlastnosti nebo metody.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří přetížené metody, které přijímají buď `String` nebo `Decimal` reprezentace dolaru velikost a vrátí řetězec obsahující DPH.  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Chcete-li použít tento příklad k vytvoření přetížené metody  
  
1.  Otevřete nový projekt a přidejte třídu s názvem `TaxClass`.  
  
2.  Přidejte následující kód, který `TaxClass` třídy.  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  Přidejte do svého formuláře následující postup.  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  Přidání tlačítka do formuláře a volání `ShowTax` procedury `Button1_Click` události tlačítka.  
  
5.  Spusťte projekt a klikněte na tlačítko ve formuláři pro testování přetížené `ShowTax` postupu.  
  
 V době běhu zvolí kompilátoru příslušné přetížené funkce, která odpovídá parametry používá. Když kliknete na tlačítko, přetížené metoda je volána nejprve s `Price` parametr, který je řetězec a zobrazí zpráva "cena je řetězec. Daň je $5.12" se zobrazí. `TaxAmount`je volána s `Decimal` hodnotu druhém a zpráva, "cena je datový typ Decimal. Daň je $5.12" se zobrazí.  
  
## <a name="see-also"></a>Viz také  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Stínů](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [Přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Stínů](../../../../visual-basic/language-reference/modifiers/shadows.md)
