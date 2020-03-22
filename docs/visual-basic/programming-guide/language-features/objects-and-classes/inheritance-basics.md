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
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="3b87c-102">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b87c-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="3b87c-103">Příkaz `Inherits` se používá k deklarování nové třídy, nazývané *odvozené třídy*, založené na existující třídě, známé jako *základní třída*.</span><span class="sxs-lookup"><span data-stu-id="3b87c-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="3b87c-104">Odvozené třídy dědí a mohou rozšířit vlastnosti, metody, události, pole a konstanty definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="3b87c-105">Následující část popisuje některá pravidla dědičnosti a modifikátory, které můžete použít ke změně způsobu, jakým třídy dědí nebo jsou zděděny:</span><span class="sxs-lookup"><span data-stu-id="3b87c-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="3b87c-106">Ve výchozím nastavení jsou všechny třídy `NotInheritable` dědičné, pokud nejsou označeny klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="3b87c-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="3b87c-107">Třídy mohou dědit z jiných tříd v projektu nebo z tříd v jiných sestaveních, na které projekt odkazuje.</span><span class="sxs-lookup"><span data-stu-id="3b87c-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="3b87c-108">Na rozdíl od jazyků, které umožňují více násobné dědičnosti, visual basic umožňuje pouze jednu dědičnost ve třídách; to znamená, že odvozené třídy mohou mít pouze jednu základní třídu.</span><span class="sxs-lookup"><span data-stu-id="3b87c-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="3b87c-109">Přestože více dědičnosti není povoleno ve třídách, třídy můžete implementovat více rozhraní, které mohou účinně dosáhnout stejné konce.</span><span class="sxs-lookup"><span data-stu-id="3b87c-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="3b87c-110">Chcete-li zabránit vystavení položek s omezeným přístupem v základní třídě, musí být typ přístupu odvozené třídy stejný nebo více omezující než její základní třída.</span><span class="sxs-lookup"><span data-stu-id="3b87c-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="3b87c-111">Například `Public` třída nemůže `Friend` dědit `Private` nebo třídu `Friend` a třída `Private` nemůže dědit třídu.</span><span class="sxs-lookup"><span data-stu-id="3b87c-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="3b87c-112">Modifikátory dědičnosti</span><span class="sxs-lookup"><span data-stu-id="3b87c-112">Inheritance Modifiers</span></span>

<span data-ttu-id="3b87c-113">Visual Basic zavádí následující příkazy a modifikátory na úrovni třídy pro podporu dědičnosti:</span><span class="sxs-lookup"><span data-stu-id="3b87c-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="3b87c-114">`Inherits`příkaz — Určuje základní třídu.</span><span class="sxs-lookup"><span data-stu-id="3b87c-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="3b87c-115">`NotInheritable`modifikátor – Zabrání programátorům používat třídu jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="3b87c-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="3b87c-116">`MustInherit`modifikátor – Určuje, že třída je určena pouze pro použití jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="3b87c-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="3b87c-117">Instance `MustInherit` tříd nelze vytvořit přímo; mohou být vytvořeny pouze jako instance základní třídy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="3b87c-118">(Jiné programovací jazyky, například C++ a C#, používají termín *abstraktní třída* k popisu takové třídy.)</span><span class="sxs-lookup"><span data-stu-id="3b87c-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="3b87c-119">Přepsání vlastností a metod v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="3b87c-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="3b87c-120">Ve výchozím nastavení odvozená třída dědí vlastnosti a metody ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="3b87c-121">Pokud zděděné vlastnost nebo metoda musí chovat odlišně v odvozené třídě může být *přepsána*.</span><span class="sxs-lookup"><span data-stu-id="3b87c-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="3b87c-122">To znamená, že můžete definovat novou implementaci metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="3b87c-123">Následující modifikátory se používají k řízení, jak jsou přepsány vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="3b87c-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="3b87c-124">`Overridable`– Umožňuje přepsání vlastnosti nebo metody ve třídě v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="3b87c-125">`Overrides`— Přepíše `Overridable` vlastnost nebo metodu definovanou v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="3b87c-126">`NotOverridable`– Zabrání přepsání vlastnosti nebo metody v dědící třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="3b87c-127">Ve výchozím `Public` nastavení `NotOverridable`jsou metody .</span><span class="sxs-lookup"><span data-stu-id="3b87c-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="3b87c-128">`MustOverride`– Vyžaduje, aby odvozená třída přepsat vlastnost nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="3b87c-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="3b87c-129">Při `MustOverride` použití klíčového slova se definice metody `Sub` `Function`skládá `Property` pouze z příkazu , nebo příkazu.</span><span class="sxs-lookup"><span data-stu-id="3b87c-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="3b87c-130">Žádné jiné příkazy jsou povoleny, a konkrétně není žádné `End Sub` nebo `End Function` prohlášení.</span><span class="sxs-lookup"><span data-stu-id="3b87c-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="3b87c-131">`MustOverride`metody musí být `MustInherit` deklarovány ve třídách.</span><span class="sxs-lookup"><span data-stu-id="3b87c-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="3b87c-132">Předpokládejme, že chcete definovat třídy pro zpracování mezd.</span><span class="sxs-lookup"><span data-stu-id="3b87c-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="3b87c-133">Můžete definovat obecnou `Payroll` třídu, `RunPayroll` která obsahuje metodu, která vypočítá mzdy pro typický týden.</span><span class="sxs-lookup"><span data-stu-id="3b87c-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="3b87c-134">Pak můžete `Payroll` použít jako základní třídu `BonusPayroll` pro specializovanější třídu, která by mohla být použita při distribuci bonusů zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="3b87c-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="3b87c-135">Třída `BonusPayroll` může dědit a přepsat `PayEmployee` metodu definovanou v základní `Payroll` třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="3b87c-136">Následující příklad definuje základní třídu `Payroll,` a odvozenou `BonusPayroll`třídu , která přepíše zděděnou metodu `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="3b87c-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="3b87c-137">Procedura `RunPayroll`, vytvoří a `Payroll` potom předá objekt `BonusPayroll` a `Pay`objekt funkci `PayEmployee` , která provede metodu obou objektů.</span><span class="sxs-lookup"><span data-stu-id="3b87c-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="3b87c-138">Klíčové slovo MyBase</span><span class="sxs-lookup"><span data-stu-id="3b87c-138">The MyBase Keyword</span></span>

<span data-ttu-id="3b87c-139">Klíčové `MyBase` slovo se chová jako proměnná objektu, která odkazuje na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="3b87c-140">`MyBase`se často používá pro přístup k členům základní třídy, které jsou přepsány nebo stínovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="3b87c-141">Zejména `MyBase.New` se používá k explicitnívolání konstruktoru základní třídy z konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="3b87c-142">Předpokládejme například, že navrhujete odvozenou třídu, která přepíše metodu zděděnou ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="3b87c-143">Potlačená metoda může volat metodu v základní třídě a upravit vrácenou hodnotu, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="3b87c-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="3b87c-144">Následující seznam popisuje omezení `MyBase`používání :</span><span class="sxs-lookup"><span data-stu-id="3b87c-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="3b87c-145">`MyBase`odkazuje na okamžitou základní třídu a její zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="3b87c-146">Nelze jej použít `Private` pro přístup k členům ve třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="3b87c-147">`MyBase`je klíčové slovo, nikoli skutečný objekt.</span><span class="sxs-lookup"><span data-stu-id="3b87c-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="3b87c-148">`MyBase`nelze přiřadit proměnné, předat procedurám nebo použít `Is` při porovnání.</span><span class="sxs-lookup"><span data-stu-id="3b87c-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="3b87c-149">Metoda, `MyBase` která se kvalifikuje, nemusí být definována v okamžité základní třídě; místo toho může být definována v nepřímo zděděné základní třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="3b87c-150">Aby odkaz kvalifikovaný podle `MyBase` správně zkompilovat některé základní třídy musí obsahovat metodu odpovídající název a typy parametrů, které se zobrazí ve volání.</span><span class="sxs-lookup"><span data-stu-id="3b87c-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="3b87c-151">Nelze použít `MyBase` k `MustOverride` volání metod základní třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="3b87c-152">`MyBase`nelze použít k tomu, aby se kvalifikovala sama.</span><span class="sxs-lookup"><span data-stu-id="3b87c-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="3b87c-153">Proto následující kód není platný:</span><span class="sxs-lookup"><span data-stu-id="3b87c-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="3b87c-154">`MyBase`nelze použít v modulech.</span><span class="sxs-lookup"><span data-stu-id="3b87c-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="3b87c-155">`MyBase`nelze použít pro přístup k členům `Friend` základní třídy, které jsou označeny jako základní třída v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b87c-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="3b87c-156">Další informace a další příklad naleznete v [tématu How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="3b87c-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="3b87c-157">Klíčové slovo MyClass</span><span class="sxs-lookup"><span data-stu-id="3b87c-157">The MyClass Keyword</span></span>

<span data-ttu-id="3b87c-158">Klíčové `MyClass` slovo se chová jako proměnná objektu, která odkazuje na aktuální instanci třídy jako původně implementované.</span><span class="sxs-lookup"><span data-stu-id="3b87c-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="3b87c-159">`MyClass`podobá `Me`se , ale každá `MyClass` metoda a volání vlastností je považována za metodu nebo vlastnost [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="3b87c-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="3b87c-160">Proto metoda nebo vlastnost není ovlivněna přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="3b87c-161">`MyClass`je klíčové slovo, nikoli skutečný objekt.</span><span class="sxs-lookup"><span data-stu-id="3b87c-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="3b87c-162">`MyClass`nelze přiřadit proměnné, předat procedurám nebo použít `Is` při porovnání.</span><span class="sxs-lookup"><span data-stu-id="3b87c-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="3b87c-163">`MyClass`odkazuje na obsahující třídu a její zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="3b87c-164">`MyClass`lze použít jako kvalifikátor pro `Shared` členy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="3b87c-165">`MyClass`nelze použít uvnitř `Shared` metody, ale lze použít uvnitř metody instance pro přístup ke sdílenému členu třídy.</span><span class="sxs-lookup"><span data-stu-id="3b87c-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="3b87c-166">`MyClass`nelze použít ve standardních modulech.</span><span class="sxs-lookup"><span data-stu-id="3b87c-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="3b87c-167">`MyClass`lze použít ke kvalifikaci metody, která je definována v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě.</span><span class="sxs-lookup"><span data-stu-id="3b87c-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="3b87c-168">Takový odkaz má stejný `MyBase.`význam jako *metoda*.</span><span class="sxs-lookup"><span data-stu-id="3b87c-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="3b87c-169">Následující příklad porovnává `Me` `MyClass`a .</span><span class="sxs-lookup"><span data-stu-id="3b87c-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="3b87c-170">I `derivedClass` když `testMethod`přepíše `MyClass` , `useMyClass` klíčové slovo v nullefekty přepsání a kompilátor překládá `testMethod`volání verze základní třídy .</span><span class="sxs-lookup"><span data-stu-id="3b87c-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b87c-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b87c-171">See also</span></span>

- [<span data-ttu-id="3b87c-172">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="3b87c-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="3b87c-173">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="3b87c-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
