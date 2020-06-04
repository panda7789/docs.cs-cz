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
ms.openlocfilehash: 3bf1847f618a642d26df4aa1c5247a4ba2bd3b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411776"
---
# <a name="inheritance-basics-visual-basic"></a>Základní informace o dědičnosti (Visual Basic)

`Inherits`Příkaz se používá k deklaraci nové třídy označované jako *odvozená třída*založená na stávající třídě, která se označuje jako *základní třída*. Odvozené třídy dědí a mohou roztáhnout, vlastnosti, metody, události, pole a konstanty definované v základní třídě. V následující části jsou popsána některá pravidla dědičnosti a modifikátory, které lze použít ke změně způsobu dědění nebo dědění tříd:

- Ve výchozím nastavení jsou všechny třídy děděny, pokud nejsou označeny `NotInheritable` klíčovým slovem. Třídy mohou dědit z jiných tříd v projektu nebo ze tříd v jiných sestaveních, na která projekt odkazuje.

- Na rozdíl od jazyků, které umožňují vícenásobnou dědění, Visual Basic povoluje pouze jedinou dědičnost v třídách; To znamená, že odvozené třídy mohou mít pouze jednu základní třídu. I když v třídách není povolena vícenásobná dědičnost, třídy mohou implementovat více rozhraní, což může efektivně plnit stejné konce.

- Aby nedocházelo k vystavení omezených položek v základní třídě, musí být typ přístupu odvozené třídy roven nebo větší omezující hodnotě než její základní třída. `Public`Třída například nemůže dědit třídu nebo a třída `Friend` `Private` `Friend` nemůže dědit `Private` třídu.

## <a name="inheritance-modifiers"></a>Modifikátory dědičnosti

Visual Basic zavádí následující příkazy na úrovni třídy a modifikátory pro podporu dědičnosti:

- `Inherits`příkaz – určuje základní třídu.

- `NotInheritable`Modifikátor – zabraňuje programátorům v používání třídy jako základní třídy.

- `MustInherit`Modifikátor – určuje, že třída je určena pouze pro použití jako základní třída. Instance `MustInherit` tříd nelze vytvořit přímo; lze je vytvořit pouze jako instance základní třídy odvozené třídy. (Jiné programovací jazyky, například C++ a C#, používají pojem *abstraktní třída* k popsání takové třídy.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Přepsání vlastností a metod v odvozených třídách

Ve výchozím nastavení dědí odvozená třída vlastnosti a metody ze své základní třídy. Pokud se zděděná vlastnost nebo metoda musí chovat jinak v odvozené třídě, může být *přepsána*. To znamená, že můžete definovat novou implementaci metody v odvozené třídě. Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:

- `Overridable`– Umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě.

- `Overrides`– Přepisuje `Overridable` vlastnost nebo metodu definovanou v základní třídě.

- `NotOverridable`– Zabraňuje přepsání vlastnosti nebo metody v dědičné třídě. Ve výchozím nastavení `Public` jsou metody `NotOverridable` .

- `MustOverride`– Vyžaduje, aby odvozená třída přepsala vlastnost nebo metodu. Při `MustOverride` použití klíčového slova se definice metody skládá pouze z `Sub` `Function` příkazu, nebo `Property` . Nejsou povoleny žádné jiné příkazy a konkrétně neexistuje žádný `End Sub` `End Function` příkaz. `MustOverride`metody musí být deklarovány ve `MustInherit` třídách.

Předpokládejme, že chcete definovat třídy pro zpracování mezd. Můžete definovat obecnou `Payroll` třídu, která obsahuje `RunPayroll` metodu, která vypočítá mzdový kód pro typický týden. Pak můžete použít `Payroll` jako základní třídu pro konkrétnější `BonusPayroll` třídu, která se dá použít při distribuci prémií zaměstnanců.

`BonusPayroll`Třída může dědit a přepsat `PayEmployee` metodu definovanou v základní `Payroll` třídě.

Následující příklad definuje základní třídu `Payroll,` a odvozenou třídu, `BonusPayroll` která přepisuje zděděnou metodu, `PayEmployee` . Procedura, `RunPayroll` , vytvoří a poté předá `Payroll` objekt a `BonusPayroll` objekt do funkce,, `Pay` která provede `PayEmployee` metodu obou objektů.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>Klíčové slovo MyBase

`MyBase`Klíčové slovo se chová jako proměnná objektu, která odkazuje na základní třídu aktuální instance třídy. `MyBase`se často používá pro přístup ke členům základních tříd, které jsou přepsány nebo vrženy v odvozené třídě. Konkrétně `MyBase.New` se používá k explicitnímu volání konstruktoru základní třídy z konstruktoru odvozené třídy.

Předpokládejme například, že navrhujete odvozenou třídu, která přepisuje metodu zděděnou ze základní třídy. Přepsaná metoda může volat metodu v základní třídě a upravit návratovou hodnotu, jak je znázorněno v následujícím fragmentu kódu:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Následující seznam popisuje omezení používání `MyBase` :

- `MyBase`odkazuje na bezprostřední základní třídu a její zděděné členy. Nedá se použít pro přístup ke `Private` členům ve třídě.

- `MyBase`je klíčové slovo, nikoli skutečný objekt. `MyBase`nelze přiřadit proměnné, předávat do procedur ani použít v `Is` porovnání.

- Metoda, kterou je třeba použít, `MyBase` nemusí být definována v bezprostřední základní třídě; je možné ji definovat v nepřímo zděděné základní třídě. Aby byl odkaz kvalifikován pro `MyBase` správné kompilování, musí některá základní třída obsahovat metodu, která odpovídá názvu a typům parametrů, které se zobrazí ve volání.

- Nemůžete použít `MyBase` k volání `MustOverride` metod základní třídy.

- `MyBase`nejde použít k zařazení sebe sama. Proto následující kód není platný:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`nelze použít v modulech.

- `MyBase`nelze použít pro přístup ke členům základní třídy, které jsou označeny jako, `Friend` Pokud je základní třída v jiném sestavení.

Další informace a další příklad naleznete v tématu [How to: přístup k proměnné skryté odvozenou třídou](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>Klíčové slovo MyClass

`MyClass`Klíčové slovo se chová jako proměnná objektu, která odkazuje na aktuální instanci třídy, jak je původně implementována. `MyClass`se podobá `Me` , ale všechny metody a volání vlastností `MyClass` se považují za, pokud byla metoda nebo vlastnost [NotOverridable](../../../language-reference/modifiers/notoverridable.md). Proto metoda nebo vlastnost není ovlivněna přepsáním v odvozené třídě.

- `MyClass`je klíčové slovo, nikoli skutečný objekt. `MyClass`nelze přiřadit proměnné, předávat do procedur ani použít v `Is` porovnání.

- `MyClass`odkazuje na obsahující třídu a její zděděné členy.

- `MyClass`dá se použít jako kvalifikátor pro `Shared` členy.

- `MyClass`nelze použít uvnitř `Shared` metody, ale lze ji použít uvnitř metody instance pro přístup ke sdílenému členu třídy.

- `MyClass`nelze použít ve standardních modulech.

- `MyClass`lze použít k kvalifikování metody, která je definována v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě. Takový odkaz má stejný význam jako `MyBase.` *Metoda*.

Následující příklad porovnává `Me` a `MyClass` .

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

I když `derivedClass` přepsání `testMethod` , `MyClass` klíčové slovo v `useMyClass` NULLIFIES účinek přepsání a kompilátor překládá volání na verzi základní třídy `testMethod` .

## <a name="see-also"></a>Viz také

- [Inherits – příkaz](../../../language-reference/statements/inherits-statement.md)
- [Me, My, MyBase a MyClass](../../program-structure/me-my-mybase-and-myclass.md)
