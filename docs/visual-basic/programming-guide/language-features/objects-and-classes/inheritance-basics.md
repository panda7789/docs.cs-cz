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
ms.openlocfilehash: 3d772fb81eb13b9454f44ff8ae4256bdb4144caa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970295"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="fcc0b-102">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcc0b-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="fcc0b-103">`Inherits` Prohlášení se používá k deklaraci nové třídy, nazvané *odvozené třídy*založená na stávající třídě, označované jako *základní třída*.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="fcc0b-104">Odvozené třídy dědit a můžete rozšířit, vlastnosti, metody, události, polí a konstanty definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="fcc0b-105">Následující část popisuje některé z pravidel pro dědičnost a modifikátory, které vám umožní změnit způsob, jak třídy dědit nebo jsou zděděny:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="fcc0b-106">Ve výchozím nastavení, všechny třídy lze dědit, pokud označené `NotInheritable` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="fcc0b-107">Třídy mohou dědit z jiné třídy v projektu nebo z třídy v jiných sestavení, na které odkazuje váš projekt.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="fcc0b-108">Na rozdíl od jazyky, které umožňují vícenásobná dědičnost Visual Basic umožňuje pouze jedna dědičnost tříd; To znamená, že odvozené třídy mohou mít pouze jednu základní třídu.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="fcc0b-109">I když vícenásobná dědičnost není povolený ve třídách, třídy můžou implementovat více rozhraní, které můžete efektivně provádět stejné elementy end.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="fcc0b-110">Pokud chcete zabránit zveřejnění položky s omezeným přístupem v základní třídě, musí být typ přístupu odvozené třídy rovná nebo je více omezující než její základní třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="fcc0b-111">Například `Public` třída nemůže dědit `Friend` nebo `Private` třídy a `Friend` třída nemůže dědit `Private` třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="fcc0b-112">Modifikátory dědičnosti</span><span class="sxs-lookup"><span data-stu-id="fcc0b-112">Inheritance Modifiers</span></span>  
 <span data-ttu-id="fcc0b-113">Visual Basic představuje následující příkazy na úrovni třídy a modifikátory pro podporu dědičnosti:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="fcc0b-114">`Inherits` příkaz – určuje základní třídu.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="fcc0b-115">`NotInheritable` Modifikátor – zbavuje programátory horizontálních oddílů pomocí třídy jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="fcc0b-116">`MustInherit` Modifikátor – Určuje, že třída je určena pro použití jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="fcc0b-117">Instance `MustInherit` třídy nelze vytvořit přímo, mohou být vytvořeny pouze jako základní třída instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="fcc0b-118">(Jiných programovacích jazycích, jako je například C++ a C#, použijte termín *abstraktní třídu* k popisu takové třídy.)</span><span class="sxs-lookup"><span data-stu-id="fcc0b-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="fcc0b-119">Přepsání vlastností a metod v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="fcc0b-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="fcc0b-120">Ve výchozím nastavení dědí odvozená třída vlastnosti a metody ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="fcc0b-121">Pokud zděděnou vlastnost nebo metoda mají chovat jinak než v odvozené třídě může být *přepsat*.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="fcc0b-122">To znamená můžete definovat novou implementaci metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="fcc0b-123">Následující modifikátory umožňují určit, jak přepsat vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="fcc0b-124">`Overridable` – Povoluje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="fcc0b-125">`Overrides` – Přepíše `Overridable` vlastnosti nebo metody definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="fcc0b-126">`NotOverridable` – Brání vlastnosti nebo metody v přepsání v dědičné třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="fcc0b-127">Ve výchozím nastavení `Public` metody jsou `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="fcc0b-128">`MustOverride` – Vyžaduje, aby odvozená třída přepsat vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="fcc0b-129">Když `MustOverride` klíčové slovo se používá, se skládá z definice metody jenom `Sub`, `Function`, nebo `Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="fcc0b-130">Jsou povoleny žádné jiné příkazy a konkrétně neexistuje žádné `End Sub` nebo `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="fcc0b-131">`MustOverride` metody musí být deklarována v `MustInherit` třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="fcc0b-132">Předpokládejme, že chcete definovat třídy pro zpracování mezd.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="fcc0b-133">Můžete například definovat obecnou `Payroll` třídu, která obsahuje `RunPayroll` metodu, která vypočítá mezd typické týden.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="fcc0b-134">Můžete pak použít `Payroll` jako základní třída pro více specializované `BonusPayroll` třídy, který může být použit při distribuci bonusy zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="fcc0b-135">`BonusPayroll` Třída může dědit a přepsat, `PayEmployee` metodu definovanou v základní třídě `Payroll` třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="fcc0b-136">Následující příklad definuje základní třídu, `Payroll,` a odvozené třídy `BonusPayroll`, která přepíše metodu zděděné `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="fcc0b-137">Proceduře `RunPayroll`, vytvoří a pak předá `Payroll` objektu a `BonusPayroll` objekt funkce, `Pay`, který se spustí `PayEmployee` metoda oba objekty.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="fcc0b-138">MyBase – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="fcc0b-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="fcc0b-139">`MyBase` – Klíčové slovo se chová jako proměnné objektu, který odkazuje na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="fcc0b-140">`MyBase` často se používá pro přístup ke členům základní třídy, přepsat nebo Stínovaný v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="fcc0b-141">Zejména `MyBase.New` se používá explicitně volat konstruktor základní třídy v konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="fcc0b-142">Předpokládejme například, že při návrhu odvozenou třídu, která přepíše metodu zděděné ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="fcc0b-143">Přepsané metody lze volat metodu v základní třídě a vrácenou hodnotu změnit, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 <span data-ttu-id="fcc0b-144">Následující seznam popisuje omezení pro používání `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="fcc0b-145">`MyBase` odkazuje na přímé základní třídy a jejích zděděných členů.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="fcc0b-146">Nedá se použít pro přístup k `Private` členy třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-146">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="fcc0b-147">`MyBase` je klíčové slovo, nikoli skutečný objekt.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="fcc0b-148">`MyBase` nelze přiřadit k proměnné, předány do procedury nebo použít v `Is` porovnání.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="fcc0b-149">Metoda, která `MyBase` kvalifikuje nemusí být definován v přímé základní třídy je místo toho mohou být definovány v nepřímo zděděné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="fcc0b-150">Aby odkaz kvalifikována `MyBase` pro správnou kompilaci některé základní třída musí obsahovat odpovídající název a typy parametrů, které se zobrazí při volání metody.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="fcc0b-151">Nemůžete použít `MyBase` volat `MustOverride` základní metody třídy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="fcc0b-152">`MyBase` nelze použít k vyfiltrování samotný.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="fcc0b-153">Následující kód proto není platná:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="fcc0b-154">`MyBase` nelze použít v modulech.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-154">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="fcc0b-155">`MyBase` nelze použít pro přístup k členům základní třídy, které jsou označeny jako `Friend` Pokud základní třída je v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="fcc0b-156">Další informace a další příklad naleznete v tématu [jak: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="fcc0b-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="fcc0b-157">MyClass – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="fcc0b-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="fcc0b-158">`MyClass` – Klíčové slovo se chová jako proměnné objektu, který odkazuje na aktuální instanci třídy, jak byly původně implementované.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="fcc0b-159">`MyClass` se podobá `Me`, ale každé metody a vlastnosti volat na `MyClass` je zacházeno, jako kdyby byly metody nebo vlastnosti [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="fcc0b-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="fcc0b-160">Proto že metoda nebo vlastnost nemá vliv přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="fcc0b-161">`MyClass` je klíčové slovo, nikoli skutečný objekt.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="fcc0b-162">`MyClass` nelze přiřadit k proměnné, předány do procedury nebo použít v `Is` porovnání.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="fcc0b-163">`MyClass` odkazuje na třídu obsahující a jejích zděděných členů.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="fcc0b-164">`MyClass` lze použít jako kvalifikátory pro `Shared` členy.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="fcc0b-165">`MyClass` nelze použít uvnitř `Shared` metody, ale můžou se používat pro přístup ke sdílenému členu třídy uvnitř metody instance.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="fcc0b-166">`MyClass` nelze použít standardní moduly.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-166">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="fcc0b-167">`MyClass` lze použít k vyfiltrování metodu, která je definována v základní třídě a, který nemá žádnou implementaci metody, které jsou k dispozici v dané třídě.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="fcc0b-168">Takový odkaz má stejný význam jako `MyBase.` *metoda*.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="fcc0b-169">Následující příklad porovnává `Me` a `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-169">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="fcc0b-170">I když `derivedClass` přepíše `testMethod`, `MyClass` – klíčové slovo v `useMyClass` nichž účinky přepsání a odstraňuje kompilátoru volání základní třídy verzi `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="fcc0b-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc0b-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcc0b-171">See also</span></span>
- [<span data-ttu-id="fcc0b-172">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="fcc0b-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="fcc0b-173">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="fcc0b-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
