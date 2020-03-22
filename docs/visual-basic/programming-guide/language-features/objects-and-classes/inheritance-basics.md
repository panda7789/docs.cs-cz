---
title: Základní informace o dědičnosti
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400881"
---
# <a name="inheritance-basics-visual-basic"></a>Základní informace o dědičnosti (Visual Basic)

Příkaz `Inherits` se používá k deklarování nové třídy, nazývané *odvozené třídy*, založené na existující třídě, známé jako *základní třída*. Odvozené třídy dědí a mohou rozšířit vlastnosti, metody, události, pole a konstanty definované v základní třídě. Následující část popisuje některá pravidla dědičnosti a modifikátory, které můžete použít ke změně způsobu, jakým třídy dědí nebo jsou zděděny:

- Ve výchozím nastavení jsou všechny třídy `NotInheritable` dědičné, pokud nejsou označeny klíčovým slovem. Třídy mohou dědit z jiných tříd v projektu nebo z tříd v jiných sestaveních, na které projekt odkazuje.

- Na rozdíl od jazyků, které umožňují více násobné dědičnosti, visual basic umožňuje pouze jednu dědičnost ve třídách; to znamená, že odvozené třídy mohou mít pouze jednu základní třídu. Přestože více dědičnosti není povoleno ve třídách, třídy můžete implementovat více rozhraní, které mohou účinně dosáhnout stejné konce.

- Chcete-li zabránit vystavení položek s omezeným přístupem v základní třídě, musí být typ přístupu odvozené třídy stejný nebo více omezující než její základní třída. Například `Public` třída nemůže `Friend` dědit `Private` nebo třídu `Friend` a třída `Private` nemůže dědit třídu.

## <a name="inheritance-modifiers"></a>Modifikátory dědičnosti

Visual Basic zavádí následující příkazy a modifikátory na úrovni třídy pro podporu dědičnosti:

- `Inherits`příkaz — Určuje základní třídu.

- `NotInheritable`modifikátor – Zabrání programátorům používat třídu jako základní třídu.

- `MustInherit`modifikátor – Určuje, že třída je určena pouze pro použití jako základní třída. Instance `MustInherit` tříd nelze vytvořit přímo; mohou být vytvořeny pouze jako instance základní třídy odvozené třídy. (Jiné programovací jazyky, například C++ a C#, používají termín *abstraktní třída* k popisu takové třídy.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Přepsání vlastností a metod v odvozených třídách

Ve výchozím nastavení odvozená třída dědí vlastnosti a metody ze své základní třídy. Pokud zděděné vlastnost nebo metoda musí chovat odlišně v odvozené třídě může být *přepsána*. To znamená, že můžete definovat novou implementaci metody v odvozené třídě. Následující modifikátory se používají k řízení, jak jsou přepsány vlastnosti a metody:

- `Overridable`– Umožňuje přepsání vlastnosti nebo metody ve třídě v odvozené třídě.

- `Overrides`— Přepíše `Overridable` vlastnost nebo metodu definovanou v základní třídě.

- `NotOverridable`– Zabrání přepsání vlastnosti nebo metody v dědící třídě. Ve výchozím `Public` nastavení `NotOverridable`jsou metody .

- `MustOverride`– Vyžaduje, aby odvozená třída přepsat vlastnost nebo metodu. Při `MustOverride` použití klíčového slova se definice metody `Sub` `Function`skládá `Property` pouze z příkazu , nebo příkazu. Žádné jiné příkazy jsou povoleny, a konkrétně není žádné `End Sub` nebo `End Function` prohlášení. `MustOverride`metody musí být `MustInherit` deklarovány ve třídách.

Předpokládejme, že chcete definovat třídy pro zpracování mezd. Můžete definovat obecnou `Payroll` třídu, `RunPayroll` která obsahuje metodu, která vypočítá mzdy pro typický týden. Pak můžete `Payroll` použít jako základní třídu `BonusPayroll` pro specializovanější třídu, která by mohla být použita při distribuci bonusů zaměstnanců.

Třída `BonusPayroll` může dědit a přepsat `PayEmployee` metodu definovanou v základní `Payroll` třídě.

Následující příklad definuje základní třídu `Payroll,` a odvozenou `BonusPayroll`třídu , která přepíše zděděnou metodu `PayEmployee`. Procedura `RunPayroll`, vytvoří a `Payroll` potom předá objekt `BonusPayroll` a `Pay`objekt funkci `PayEmployee` , která provede metodu obou objektů.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Klíčové slovo MyBase

Klíčové `MyBase` slovo se chová jako proměnná objektu, která odkazuje na základní třídu aktuální instance třídy. `MyBase`se často používá pro přístup k členům základní třídy, které jsou přepsány nebo stínovány v odvozené třídě. Zejména `MyBase.New` se používá k explicitnívolání konstruktoru základní třídy z konstruktoru odvozené třídy.

Předpokládejme například, že navrhujete odvozenou třídu, která přepíše metodu zděděnou ze základní třídy. Potlačená metoda může volat metodu v základní třídě a upravit vrácenou hodnotu, jak je znázorněno v následujícím fragmentu kódu:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Následující seznam popisuje omezení `MyBase`používání :

- `MyBase`odkazuje na okamžitou základní třídu a její zděděné členy. Nelze jej použít `Private` pro přístup k členům ve třídě.

- `MyBase`je klíčové slovo, nikoli skutečný objekt. `MyBase`nelze přiřadit proměnné, předat procedurám nebo použít `Is` při porovnání.

- Metoda, `MyBase` která se kvalifikuje, nemusí být definována v okamžité základní třídě; místo toho může být definována v nepřímo zděděné základní třídě. Aby odkaz kvalifikovaný podle `MyBase` správně zkompilovat některé základní třídy musí obsahovat metodu odpovídající název a typy parametrů, které se zobrazí ve volání.

- Nelze použít `MyBase` k `MustOverride` volání metod základní třídy.

- `MyBase`nelze použít k tomu, aby se kvalifikovala sama. Proto následující kód není platný:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`nelze použít v modulech.

- `MyBase`nelze použít pro přístup k členům `Friend` základní třídy, které jsou označeny jako základní třída v jiném sestavení.

Další informace a další příklad naleznete v [tématu How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Klíčové slovo MyClass

Klíčové `MyClass` slovo se chová jako proměnná objektu, která odkazuje na aktuální instanci třídy jako původně implementované. `MyClass`podobá `Me`se , ale každá `MyClass` metoda a volání vlastností je považována za metodu nebo vlastnost [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Proto metoda nebo vlastnost není ovlivněna přepsání v odvozené třídě.

- `MyClass`je klíčové slovo, nikoli skutečný objekt. `MyClass`nelze přiřadit proměnné, předat procedurám nebo použít `Is` při porovnání.

- `MyClass`odkazuje na obsahující třídu a její zděděné členy.

- `MyClass`lze použít jako kvalifikátor pro `Shared` členy.

- `MyClass`nelze použít uvnitř `Shared` metody, ale lze použít uvnitř metody instance pro přístup ke sdílenému členu třídy.

- `MyClass`nelze použít ve standardních modulech.

- `MyClass`lze použít ke kvalifikaci metody, která je definována v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě. Takový odkaz má stejný `MyBase.`význam jako *metoda*.

Následující příklad porovnává `Me` `MyClass`a .

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

I `derivedClass` když `testMethod`přepíše `MyClass` , `useMyClass` klíčové slovo v nullefekty přepsání a kompilátor překládá `testMethod`volání verze základní třídy .

## <a name="see-also"></a>Viz také

- [Příkaz Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
