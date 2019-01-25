---
title: Přetížená vlastnosti a metody (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 472cd0dbfc0544477d8e368b553a454b977d633c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498606"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Přetížená vlastnosti a metody (Visual Basic)

Přetěžování je vytvoření více procedur, konstruktor instance nebo vlastnost ve třídě se stejným názvem, ale typy různých argumentů.  
  
## <a name="overloading-usage"></a>Přetížení využití

 Přetěžování je zvlášť užitečné, když objektový model Určuje, že nepoužijete stejný název pro postupy, které pracují s různými datovými typy. Například může mít třídu, která se může zobrazit několik různých datových typů `Display` postupy, které vypadají takto:  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 Bez přetížení, je třeba vytvořit odlišné názvy pro každý postup i v případě, že to samé udělá, jak je ukázáno dále:  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 Přetížení je snazší vzhledem k tomu, že poskytuje možnost datové typy, které je možné použít vlastnosti nebo metody. Například přetížené `Display` probírali dříve nelze volat metodu s jakoukoli následující řádky kódu:  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 V době běhu jazyka Visual Basic volá správný postup založené na datové typy parametrů, které zadáte.  
  
## <a name="overloading-rules"></a>Přetížení pravidla

 Vytvořit přetíženého členu třídy přidáním dvou nebo více vlastností nebo metod se stejným názvem. S výjimkou přetěžované členy odvozené každý přetíženého členu musí mít seznam různých parametrů a tyto položky nelze použít jako odlišující funkce při přetížení se vlastnost nebo procedura:  
  
-   Modifikátory, jako například `ByVal` nebo `ByRef`, která platí pro člena nebo parametrů členu.  
  
-   Názvy parametrů  
  
-   Návratové typy postupů  
  
 `Overloads` – Klíčové slovo je volitelný při přetížení, ale pokud existuje přetížení člena používá `Overloads` – klíčové slovo, pak všechny ostatní přetěžované členy se stejným názvem musíte zadat také toto klíčové slovo.  
  
 Odvozené třídy mohou přetěžování zděděných členů s členy, které mají shodné parametry a typy parametrů, tento proces se označuje jako *stínováním podle názvu a podpisu*. Pokud `Overloads` – klíčové slovo se používá při stínováním podle názvu a podpisu implementace odvozené třídy člena se použijí místo implementace základní třídy a všechny další přetížení pro tento člen bude k dispozici pro instance odvozené třídy.  
  
 Pokud `Overloads` – klíčové slovo je tento parametr vynecháte při přetížení zděděného člena s člena, který má stejné parametry a typy parametrů a pak přetížení se nazývá *stínováním podle názvu*. Stínový provoz podle názvu nahrazuje zděděná implementace členu a je k dispozici k instancím typu odvozené třídy a jeho decedents dalšími přetíženími.  
  
 `Overloads` a `Shadows` Modifikátory nelze použít současně s stejné vlastnosti nebo metody.  
  
### <a name="example"></a>Příklad

 Následující příklad vytvoří přetížené metody, které přijímají buď `String` nebo `Decimal` reprezentace částku a vrátit řetězec obsahující DPH.  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Chcete-li použít tento příklad k vytvoření přetížené metody
  
1.  Otevřete nový projekt a přidejte třídu pojmenovanou `TaxClass`.  
  
2.  Přidejte následující kód, který `TaxClass` třídy.  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  Přidejte do svého formuláře následující postup.  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  Přidání tlačítka do formuláře a volání `ShowTax` procedury ze `Button1_Click` událost tlačítka.  
  
5.  Spusťte projekt a klikněte na tlačítko na formuláři pro testování přetížené `ShowTax` postup.  
  
 V době běhu kompilátor volí odpovídající Přetížená funkce, která odpovídá parametrů používaných. Když kliknete na tlačítko, přetížená metoda je volána nejdřív s `Price` parametr, který je řetězec a zpráva "cena je řetězec. Daň se $5.12" se zobrazí. `TaxAmount` je volána s `Decimal` hodnotu druhého klonování a zpráva, "cena je desetinné číslo. Daň se $5.12" se zobrazí.  
  
## <a name="see-also"></a>Viz také:

- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
