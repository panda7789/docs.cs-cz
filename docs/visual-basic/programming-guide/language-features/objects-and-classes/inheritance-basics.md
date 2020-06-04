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
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="650cd-102">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="650cd-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="650cd-103">`Inherits`Příkaz se používá k deklaraci nové třídy označované jako *odvozená třída*založená na stávající třídě, která se označuje jako *základní třída*.</span><span class="sxs-lookup"><span data-stu-id="650cd-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="650cd-104">Odvozené třídy dědí a mohou roztáhnout, vlastnosti, metody, události, pole a konstanty definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="650cd-105">V následující části jsou popsána některá pravidla dědičnosti a modifikátory, které lze použít ke změně způsobu dědění nebo dědění tříd:</span><span class="sxs-lookup"><span data-stu-id="650cd-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="650cd-106">Ve výchozím nastavení jsou všechny třídy děděny, pokud nejsou označeny `NotInheritable` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="650cd-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="650cd-107">Třídy mohou dědit z jiných tříd v projektu nebo ze tříd v jiných sestaveních, na která projekt odkazuje.</span><span class="sxs-lookup"><span data-stu-id="650cd-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="650cd-108">Na rozdíl od jazyků, které umožňují vícenásobnou dědění, Visual Basic povoluje pouze jedinou dědičnost v třídách; To znamená, že odvozené třídy mohou mít pouze jednu základní třídu.</span><span class="sxs-lookup"><span data-stu-id="650cd-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="650cd-109">I když v třídách není povolena vícenásobná dědičnost, třídy mohou implementovat více rozhraní, což může efektivně plnit stejné konce.</span><span class="sxs-lookup"><span data-stu-id="650cd-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="650cd-110">Aby nedocházelo k vystavení omezených položek v základní třídě, musí být typ přístupu odvozené třídy roven nebo větší omezující hodnotě než její základní třída.</span><span class="sxs-lookup"><span data-stu-id="650cd-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="650cd-111">`Public`Třída například nemůže dědit třídu nebo a třída `Friend` `Private` `Friend` nemůže dědit `Private` třídu.</span><span class="sxs-lookup"><span data-stu-id="650cd-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="650cd-112">Modifikátory dědičnosti</span><span class="sxs-lookup"><span data-stu-id="650cd-112">Inheritance Modifiers</span></span>

<span data-ttu-id="650cd-113">Visual Basic zavádí následující příkazy na úrovni třídy a modifikátory pro podporu dědičnosti:</span><span class="sxs-lookup"><span data-stu-id="650cd-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="650cd-114">`Inherits`příkaz – určuje základní třídu.</span><span class="sxs-lookup"><span data-stu-id="650cd-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="650cd-115">`NotInheritable`Modifikátor – zabraňuje programátorům v používání třídy jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="650cd-116">`MustInherit`Modifikátor – určuje, že třída je určena pouze pro použití jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="650cd-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="650cd-117">Instance `MustInherit` tříd nelze vytvořit přímo; lze je vytvořit pouze jako instance základní třídy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="650cd-118">(Jiné programovací jazyky, například C++ a C#, používají pojem *abstraktní třída* k popsání takové třídy.)</span><span class="sxs-lookup"><span data-stu-id="650cd-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="650cd-119">Přepsání vlastností a metod v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="650cd-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="650cd-120">Ve výchozím nastavení dědí odvozená třída vlastnosti a metody ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="650cd-121">Pokud se zděděná vlastnost nebo metoda musí chovat jinak v odvozené třídě, může být *přepsána*.</span><span class="sxs-lookup"><span data-stu-id="650cd-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="650cd-122">To znamená, že můžete definovat novou implementaci metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="650cd-123">Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:</span><span class="sxs-lookup"><span data-stu-id="650cd-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="650cd-124">`Overridable`– Umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="650cd-125">`Overrides`– Přepisuje `Overridable` vlastnost nebo metodu definovanou v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="650cd-126">`NotOverridable`– Zabraňuje přepsání vlastnosti nebo metody v dědičné třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="650cd-127">Ve výchozím nastavení `Public` jsou metody `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="650cd-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="650cd-128">`MustOverride`– Vyžaduje, aby odvozená třída přepsala vlastnost nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="650cd-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="650cd-129">Při `MustOverride` použití klíčového slova se definice metody skládá pouze z `Sub` `Function` příkazu, nebo `Property` .</span><span class="sxs-lookup"><span data-stu-id="650cd-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="650cd-130">Nejsou povoleny žádné jiné příkazy a konkrétně neexistuje žádný `End Sub` `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="650cd-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="650cd-131">`MustOverride`metody musí být deklarovány ve `MustInherit` třídách.</span><span class="sxs-lookup"><span data-stu-id="650cd-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="650cd-132">Předpokládejme, že chcete definovat třídy pro zpracování mezd.</span><span class="sxs-lookup"><span data-stu-id="650cd-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="650cd-133">Můžete definovat obecnou `Payroll` třídu, která obsahuje `RunPayroll` metodu, která vypočítá mzdový kód pro typický týden.</span><span class="sxs-lookup"><span data-stu-id="650cd-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="650cd-134">Pak můžete použít `Payroll` jako základní třídu pro konkrétnější `BonusPayroll` třídu, která se dá použít při distribuci prémií zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="650cd-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="650cd-135">`BonusPayroll`Třída může dědit a přepsat `PayEmployee` metodu definovanou v základní `Payroll` třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="650cd-136">Následující příklad definuje základní třídu `Payroll,` a odvozenou třídu, `BonusPayroll` která přepisuje zděděnou metodu, `PayEmployee` .</span><span class="sxs-lookup"><span data-stu-id="650cd-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="650cd-137">Procedura, `RunPayroll` , vytvoří a poté předá `Payroll` objekt a `BonusPayroll` objekt do funkce,, `Pay` která provede `PayEmployee` metodu obou objektů.</span><span class="sxs-lookup"><span data-stu-id="650cd-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="650cd-138">Klíčové slovo MyBase</span><span class="sxs-lookup"><span data-stu-id="650cd-138">The MyBase Keyword</span></span>

<span data-ttu-id="650cd-139">`MyBase`Klíčové slovo se chová jako proměnná objektu, která odkazuje na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="650cd-140">`MyBase`se často používá pro přístup ke členům základních tříd, které jsou přepsány nebo vrženy v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="650cd-141">Konkrétně `MyBase.New` se používá k explicitnímu volání konstruktoru základní třídy z konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="650cd-142">Předpokládejme například, že navrhujete odvozenou třídu, která přepisuje metodu zděděnou ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="650cd-143">Přepsaná metoda může volat metodu v základní třídě a upravit návratovou hodnotu, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="650cd-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="650cd-144">Následující seznam popisuje omezení používání `MyBase` :</span><span class="sxs-lookup"><span data-stu-id="650cd-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="650cd-145">`MyBase`odkazuje na bezprostřední základní třídu a její zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="650cd-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="650cd-146">Nedá se použít pro přístup ke `Private` členům ve třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="650cd-147">`MyBase`je klíčové slovo, nikoli skutečný objekt.</span><span class="sxs-lookup"><span data-stu-id="650cd-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="650cd-148">`MyBase`nelze přiřadit proměnné, předávat do procedur ani použít v `Is` porovnání.</span><span class="sxs-lookup"><span data-stu-id="650cd-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="650cd-149">Metoda, kterou je třeba použít, `MyBase` nemusí být definována v bezprostřední základní třídě; je možné ji definovat v nepřímo zděděné základní třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="650cd-150">Aby byl odkaz kvalifikován pro `MyBase` správné kompilování, musí některá základní třída obsahovat metodu, která odpovídá názvu a typům parametrů, které se zobrazí ve volání.</span><span class="sxs-lookup"><span data-stu-id="650cd-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="650cd-151">Nemůžete použít `MyBase` k volání `MustOverride` metod základní třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="650cd-152">`MyBase`nejde použít k zařazení sebe sama.</span><span class="sxs-lookup"><span data-stu-id="650cd-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="650cd-153">Proto následující kód není platný:</span><span class="sxs-lookup"><span data-stu-id="650cd-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="650cd-154">`MyBase`nelze použít v modulech.</span><span class="sxs-lookup"><span data-stu-id="650cd-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="650cd-155">`MyBase`nelze použít pro přístup ke členům základní třídy, které jsou označeny jako, `Friend` Pokud je základní třída v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="650cd-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="650cd-156">Další informace a další příklad naleznete v tématu [How to: přístup k proměnné skryté odvozenou třídou](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="650cd-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="650cd-157">Klíčové slovo MyClass</span><span class="sxs-lookup"><span data-stu-id="650cd-157">The MyClass Keyword</span></span>

<span data-ttu-id="650cd-158">`MyClass`Klíčové slovo se chová jako proměnná objektu, která odkazuje na aktuální instanci třídy, jak je původně implementována.</span><span class="sxs-lookup"><span data-stu-id="650cd-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="650cd-159">`MyClass`se podobá `Me` , ale všechny metody a volání vlastností `MyClass` se považují za, pokud byla metoda nebo vlastnost [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="650cd-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="650cd-160">Proto metoda nebo vlastnost není ovlivněna přepsáním v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="650cd-161">`MyClass`je klíčové slovo, nikoli skutečný objekt.</span><span class="sxs-lookup"><span data-stu-id="650cd-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="650cd-162">`MyClass`nelze přiřadit proměnné, předávat do procedur ani použít v `Is` porovnání.</span><span class="sxs-lookup"><span data-stu-id="650cd-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="650cd-163">`MyClass`odkazuje na obsahující třídu a její zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="650cd-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="650cd-164">`MyClass`dá se použít jako kvalifikátor pro `Shared` členy.</span><span class="sxs-lookup"><span data-stu-id="650cd-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="650cd-165">`MyClass`nelze použít uvnitř `Shared` metody, ale lze ji použít uvnitř metody instance pro přístup ke sdílenému členu třídy.</span><span class="sxs-lookup"><span data-stu-id="650cd-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="650cd-166">`MyClass`nelze použít ve standardních modulech.</span><span class="sxs-lookup"><span data-stu-id="650cd-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="650cd-167">`MyClass`lze použít k kvalifikování metody, která je definována v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě.</span><span class="sxs-lookup"><span data-stu-id="650cd-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="650cd-168">Takový odkaz má stejný význam jako `MyBase.` *Metoda*.</span><span class="sxs-lookup"><span data-stu-id="650cd-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="650cd-169">Následující příklad porovnává `Me` a `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="650cd-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="650cd-170">I když `derivedClass` přepsání `testMethod` , `MyClass` klíčové slovo v `useMyClass` NULLIFIES účinek přepsání a kompilátor překládá volání na verzi základní třídy `testMethod` .</span><span class="sxs-lookup"><span data-stu-id="650cd-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="650cd-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="650cd-171">See also</span></span>

- [<span data-ttu-id="650cd-172">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="650cd-172">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="650cd-173">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="650cd-173">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
