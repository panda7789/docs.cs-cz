---
title: Přetížené vlastnosti a metody
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346092"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Přetížené vlastnosti a metody (Visual Basic)

Přetížení je vytvoření více než jedné procedury, konstruktoru instance nebo vlastnosti ve třídě se stejným názvem, ale s různými typy argumentů.

## <a name="overloading-usage"></a>Přetížení využití

Přetížení je obzvláště užitečné, když objektový model určuje, že pro procedury, které pracují s různými datovými typy, využíváte stejné názvy. Například třída, která může zobrazit několik různých datových typů, by mohla mít `Display` postupy, které vypadají takto:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Bez přetížení byste museli pro každý postup vytvořit rozdílné názvy, a to i v případě, že mají stejnou věc, jak je uvedeno dále:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Přetížení usnadňuje používání vlastností nebo metod, protože poskytuje možnost volby datových typů, které lze použít. Například přetížená výše popsaná `Display` metoda může být volána s libovolným z následujících řádků kódu:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

V době běhu Visual Basic volá správný postup na základě datových typů zadaných parametrů.

## <a name="overloading-rules"></a>Pravidla přetížení

 Můžete vytvořit přetíženého člena pro třídu přidáním dvou nebo více vlastností nebo metod se stejným názvem. S výjimkou přetížených členů musí mít každý přetížený člen jiný seznam parametrů a následující položky nelze použít jako rozdílové funkce při přetížení vlastnosti nebo procedury:

- Modifikátory, například `ByVal` nebo `ByRef`, které se vztahují na člen nebo parametry člena.

- Názvy parametrů

- Návratové typy procedur

Klíčové slovo `Overloads` je při přetížení volitelné, ale pokud nějaký přetížený člen používá klíčové slovo `Overloads`, pak všechny ostatní přetížené členy, které mají stejný název, musí také zadat toto klíčové slovo.

Odvozené třídy mohou přetížit zděděné členy se členy, kteří mají stejné parametry a typy parametrů, což je proces známý jako *stínování podle názvu a podpisu*. Pokud je klíčové slovo `Overloads` použito při stínování podle názvu a signatury, použije se místo implementace v základní třídě implementace člena odvozené třídy a všechna ostatní přetížení tohoto člena budou k dispozici pro instance odvozené třídy.

Pokud je klíčové slovo `Overloads` vynecháno při přetížení zděděného člena se členem, který má stejné parametry a typy parametrů, pak přetížení se nazývá *stíning podle názvu*. Stínová kopie podle názvu nahradí zděděnou implementaci člena a zpřístupňuje všechna ostatní přetížení instancím odvozené třídy a její decedents.

Modifikátory `Overloads` a `Shadows` nelze současně použít se stejnou vlastností nebo metodou.

### <a name="example"></a>Příklad

Následující příklad vytvoří přetížené metody, které přijímají buď `String`, nebo `Decimal` reprezentaci částky dolaru a vrátí řetězec obsahující DPH.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Chcete-li použít tento příklad k vytvoření přetížené metody

1. Otevřete nový projekt a přidejte třídu s názvem `TaxClass`.

2. Do třídy `TaxClass` přidejte následující kód.

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Do formuláře přidejte následující proceduru.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Přidejte do formuláře tlačítko a zavolejte `ShowTax`ovou proceduru z události `Button1_Click` tlačítka.

5. Spusťte projekt a klikněte na tlačítko na formuláři pro otestování přetížené `ShowTax` postupu.

V době běhu kompilátor zvolí vhodnou přetíženou funkci, která odpovídá použitým parametrům. Po kliknutí na tlačítko je přetížená metoda nejprve volána s parametrem `Price`, který je řetězec a zpráva, "Price je řetězec. Zobrazí se daň $5,12. `TaxAmount` se volá s hodnotou `Decimal` podruhé a zprávou "cena je Desítková. Zobrazí se daň $5,12.

## <a name="see-also"></a>Viz také:

- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Stínování v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
