---
title: Základní informace o dědičnosti (Visual Basic)
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
ms.openlocfilehash: 8a75b75ef9acb4c89f4c7d05f1410d4ca70e680b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582751"
---
# <a name="inheritance-basics-visual-basic"></a>Základní informace o dědičnosti (Visual Basic)

Příkaz `Inherits` slouží k deklaraci nové třídy, která se nazývá *odvozená třída*, na základě existující třídy, označované jako *základní třída*. Odvozené třídy dědí a mohou roztáhnout, vlastnosti, metody, události, pole a konstanty definované v základní třídě. V následující části jsou popsána některá pravidla dědičnosti a modifikátory, které lze použít ke změně způsobu dědění nebo dědění tříd:

- Ve výchozím nastavení jsou všechny třídy děděny, pokud nejsou označeny klíčovým slovem `NotInheritable`. Třídy mohou dědit z jiných tříd v projektu nebo ze tříd v jiných sestaveních, na která projekt odkazuje.

- Na rozdíl od jazyků, které umožňují vícenásobnou dědění, Visual Basic povoluje pouze jedinou dědičnost v třídách; To znamená, že odvozené třídy mohou mít pouze jednu základní třídu. I když v třídách není povolena vícenásobná dědičnost, třídy mohou implementovat více rozhraní, což může efektivně plnit stejné konce.

- Aby nedocházelo k vystavení omezených položek v základní třídě, musí být typ přístupu odvozené třídy roven nebo větší omezující hodnotě než její základní třída. Například třída `Public` nemůže dědit třídu `Friend` nebo `Private` a třída `Friend` nemůže dědit třídu `Private`.

## <a name="inheritance-modifiers"></a>Modifikátory dědičnosti

Visual Basic zavádí následující příkazy na úrovni třídy a modifikátory pro podporu dědičnosti:

- příkaz `Inherits` – určuje základní třídu.

- Modifikátor `NotInheritable` – zabraňuje programátorům v používání třídy jako základní třídy.

- Modifikátor `MustInherit` – určuje, že třída je určena pouze pro použití jako základní třída. Instance `MustInherit` třídy nelze vytvořit přímo; lze je vytvořit pouze jako instance základní třídy odvozené třídy. (Jiné programovací jazyky, jako jsou C++ a C#, použijte pojem *abstraktní třída* k popsání takové třídy.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Přepsání vlastností a metod v odvozených třídách

Ve výchozím nastavení dědí odvozená třída vlastnosti a metody ze své základní třídy. Pokud se zděděná vlastnost nebo metoda musí chovat jinak v odvozené třídě, může být *přepsána*. To znamená, že můžete definovat novou implementaci metody v odvozené třídě. Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:

- `Overridable` – umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě.

- `Overrides` – Přepisuje vlastnost `Overridable` nebo metodu definovanou v základní třídě.

- `NotOverridable` – zabrání přepsání vlastnosti nebo metody v dědičné třídě. Ve výchozím nastavení jsou `Public` metody `NotOverridable`.

- `MustOverride` – vyžaduje, aby odvozená třída přepsala vlastnost nebo metodu. Při použití klíčového slova `MustOverride` se definice metody skládá pouze z příkazu `Sub`, `Function` nebo `Property`. Nejsou povoleny žádné jiné příkazy a konkrétně není k dispozici žádný `End Sub` ani `End Function` příkaz. metody `MustOverride` musí být deklarované v `MustInherit`ch třídách.

Předpokládejme, že chcete definovat třídy pro zpracování mezd. Můžete definovat obecnou třídu `Payroll`, která obsahuje metodu `RunPayroll`, která vypočítá mzdový kód pro typický týden. Pak můžete použít `Payroll` jako základní třídu pro užitečnější `BonusPayroll` třídu, která se dá použít při distribuci bonusů zaměstnanců.

Třída `BonusPayroll` může dědit a přepsat metodu `PayEmployee` definovanou v základní třídě `Payroll`.

Následující příklad definuje základní třídu, `Payroll,` a odvozenou třídu, `BonusPayroll`, která přepíše zděděnou metodu `PayEmployee`. Procedura, `RunPayroll`, vytvoří a poté předá objekt `Payroll` a objekt `BonusPayroll` do funkce, `Pay`, která provádí `PayEmployee` metoda obou objektů.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Klíčové slovo MyBase

Klíčové slovo `MyBase` se chová jako proměnná objektu, která odkazuje na základní třídu aktuální instance třídy. `MyBase` se často používá pro přístup ke členům základních tříd, které jsou přepsány nebo vrženy v odvozené třídě. Konkrétně `MyBase.New` slouží k explicitnímu volání konstruktoru základní třídy z konstruktoru odvozené třídy.

Předpokládejme například, že navrhujete odvozenou třídu, která přepisuje metodu zděděnou ze základní třídy. Přepsaná metoda může volat metodu v základní třídě a upravit návratovou hodnotu, jak je znázorněno v následujícím fragmentu kódu:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Následující seznam popisuje omezení používání `MyBase`:

- `MyBase` odkazuje na bezprostřední základní třídu a její zděděné členy. Nedá se použít pro přístup k `Private` členům třídy.

- `MyBase` je klíčové slovo, nikoli skutečný objekt. `MyBase` nelze přiřadit proměnné, předat do procedur nebo použít v porovnání `Is`.

- Metoda, kterou `MyBase` kvalifikátory, nemusí být definována v bezprostřední základní třídě; místo toho je možné jej definovat v nepřímo zděděné základní třídě. Aby byl odkaz kvalifikován `MyBase` pro správné kompilování, musí některá základní třída obsahovat metodu, která odpovídá názvu a typům parametrů, které se zobrazí ve volání.

- Nelze použít `MyBase` pro volání metod `MustOverride` základní třídy.

- `MyBase` nelze použít k zařazení do sebe samé. Proto následující kód není platný:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase` nelze použít v modulech.

- `MyBase` nelze použít pro přístup ke členům základní třídy, které jsou označeny jako `Friend`, pokud je základní třída v jiném sestavení.

Další informace a další příklad naleznete v tématu [How to: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Klíčové slovo MyClass

Klíčové slovo `MyClass` se chová jako proměnná objektu, která odkazuje na aktuální instanci třídy, jak je původně implementována. `MyClass` se podobá `Me`, ale každá metoda a volání vlastnosti v `MyClass` se považují za, jako kdyby byla metoda nebo vlastnost [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Proto metoda nebo vlastnost není ovlivněna přepsáním v odvozené třídě.

- `MyClass` je klíčové slovo, nikoli skutečný objekt. `MyClass` nelze přiřadit proměnné, předat do procedur nebo použít v porovnání `Is`.

- `MyClass` odkazuje na obsahující třídu a její zděděné členy.

- `MyClass` lze použít jako kvalifikátor pro `Shared` členy.

- `MyClass` nelze použít uvnitř metody `Shared`, ale lze ji použít uvnitř metody instance pro přístup ke sdílenému členu třídy.

- `MyClass` nelze použít ve standardních modulech.

- `MyClass` lze použít k kvalifikování metody, která je definována v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě. Takový odkaz má stejný význam jako `MyBase.`*Metoda*.

Následující příklad porovnává `Me` a `MyClass`.

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

I když `derivedClass` Přepisuje `testMethod`, klíčové slovo `MyClass` v `useMyClass` NULLIFIES účinek přepsání a kompilátor vyřeší volání verze třídy `testMethod` základní třídy.

## <a name="see-also"></a>Viz také:

- [Příkaz Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
