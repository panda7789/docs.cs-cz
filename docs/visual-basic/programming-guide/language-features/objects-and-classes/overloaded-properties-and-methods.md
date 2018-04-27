---
title: Přetížené vlastnosti a metody (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
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
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96d5ef2462f5312baa5269865977596035a254d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Přetížené vlastnosti a metody (Visual Basic)

Přetížení je vytvoření více procedur, konstruktoru instance nebo vlastnost v třídě se stejným názvem, ale s typy argumentů jiný.  
  
## <a name="overloading-usage"></a>Přetížení využití

 Přetížení je obzvláště užitečné, když objektový model stanoví, že nepoužijete identické názvy postupy, které působí na různé datové typy. Například může mít třídy, která může zobrazit několik různých datových typů `Display` postupy, které vypadají takto:  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 Bez přetížení, museli byste vytvořit jedinečné názvy pro každý postup, i když udělají samé, jak ukazuje následující:  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 Přetížení usnadňuje použít vlastností nebo metod, protože poskytuje výběru datových typů, které lze použít. Například přetížené `Display` popsané dříve nelze volat metodu s žádným z následujících řádků kódu:  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 Za běhu jazyka Visual Basic volá správný postup podle datové typy parametrů, které zadáte.  
  
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
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Chcete-li použít tento příklad k vytvoření přetížené metody
  
1.  Otevřete nový projekt a přidejte třídu s názvem `TaxClass`.  
  
2.  Přidejte následující kód, který `TaxClass` třídy.  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  Přidejte do svého formuláře následující postup.  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  Přidání tlačítka do formuláře a volání `ShowTax` procedury `Button1_Click` události tlačítka.  
  
5.  Spusťte projekt a klikněte na tlačítko ve formuláři pro testování přetížené `ShowTax` postupu.  
  
 V době běhu zvolí kompilátoru příslušné přetížené funkce, která odpovídá parametry používá. Když kliknete na tlačítko, přetížené metoda je volána nejprve s `Price` parametr, který je řetězec a zobrazí zpráva "cena je řetězec. Daň je $5.12" se zobrazí. `TaxAmount` je volána s `Decimal` hodnotu druhém a zpráva, "cena je datový typ Decimal. Daň je $5.12" se zobrazí.  
  
## <a name="see-also"></a>Viz také

 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
