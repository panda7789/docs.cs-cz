---
title: "Základní informace o dědičnosti (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76813bb36c0bcf75791932a0fec081f0fc1958e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="63b7d-102">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b7d-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="63b7d-103">`Inherits` Příkaz se používá k deklaraci novou třídu, s názvem *odvozené třídy*na stávající třídě, označuje jako základě *základní třída*.</span><span class="sxs-lookup"><span data-stu-id="63b7d-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="63b7d-104">Odvozené třídy dědí a můžete rozšířit, vlastnosti, metody, události, pole a konstanty definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="63b7d-105">Následující část popisuje některé z pravidel pro dědičnosti a modifikátory, které můžete změnit způsob třídy dědí nebo jsou děděné:</span><span class="sxs-lookup"><span data-stu-id="63b7d-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
-   <span data-ttu-id="63b7d-106">Ve výchozím nastavení, všechny třídy lze dědit, pokud označené jako `NotInheritable` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="63b7d-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="63b7d-107">Třídy lze dědit z jiné třídy v projektu nebo z třídy v ostatních sestavení, které váš projekt odkazuje.</span><span class="sxs-lookup"><span data-stu-id="63b7d-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
-   <span data-ttu-id="63b7d-108">Na rozdíl od jazyky, které umožňují vícenásobná dědičnost [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umožňuje pouze jedna dědičnost v třídách; to znamená, odvozené třídy mohou mít pouze jeden základní třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-108">Unlike languages that allow multiple inheritance, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="63b7d-109">I když vícenásobná dědičnost není povolena v třídách, můžete implementovat třídy více rozhraní, které můžete efektivně provádět stejné elementy end.</span><span class="sxs-lookup"><span data-stu-id="63b7d-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
-   <span data-ttu-id="63b7d-110">Pokud chcete zabránit vystavení s omezeným přístupem položky v základní třídě, musí být typ přístupu odvozené třídy rovna nebo více omezující než její základní třída.</span><span class="sxs-lookup"><span data-stu-id="63b7d-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="63b7d-111">Například `Public` třída nemůže Zdědit `Friend` nebo `Private` třída a `Friend` třída nemůže Zdědit `Private` – třída.</span><span class="sxs-lookup"><span data-stu-id="63b7d-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="63b7d-112">Modifikátory dědičnosti</span><span class="sxs-lookup"><span data-stu-id="63b7d-112">Inheritance Modifiers</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="63b7d-113">zavádí následující příkazy úrovni třídy a modifikátory pro podporu dědičnosti:</span><span class="sxs-lookup"><span data-stu-id="63b7d-113"> introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
-   <span data-ttu-id="63b7d-114">`Inherits`příkaz – určuje základní třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-114">`Inherits` statement — Specifies the base class.</span></span>  
  
-   <span data-ttu-id="63b7d-115">`NotInheritable`Modifikátor – programátory bránit v použití třídy jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="63b7d-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
-   <span data-ttu-id="63b7d-116">`MustInherit`Modifikátor – Určuje, že třída je určena pro použití jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="63b7d-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="63b7d-117">Instance `MustInherit` třídy nelze vytvořit přímo; jejich lze vytvořit pouze jako základní instancí třídy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="63b7d-118">(Jinými programovací jazyky, jako je například C++ a C#, použijte termín *abstraktní třída* k popisu taková třída.)</span><span class="sxs-lookup"><span data-stu-id="63b7d-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="63b7d-119">Přepsání vlastností a metod v odvozených třídách</span><span class="sxs-lookup"><span data-stu-id="63b7d-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="63b7d-120">Ve výchozím nastavení odvozené třídy dědí vlastnosti a metody ze své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="63b7d-121">Pokud zděděnou vlastnost nebo metoda obsahuje chovat jinak v odvozené třídě může být *přepsat*.</span><span class="sxs-lookup"><span data-stu-id="63b7d-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="63b7d-122">To znamená můžete definovat nové implementace metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="63b7d-123">Následující modifikátory je možné určit, jak jsou přepsaná vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="63b7d-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
-   <span data-ttu-id="63b7d-124">`Overridable`– Umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
-   <span data-ttu-id="63b7d-125">`Overrides`– Přepsání `Overridable` vlastnosti nebo metody definované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
-   <span data-ttu-id="63b7d-126">`NotOverridable`– Brání vlastnosti nebo metody přepsání dědičných třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="63b7d-127">Ve výchozím nastavení `Public` metody jsou `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="63b7d-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
-   <span data-ttu-id="63b7d-128">`MustOverride`– Vyžaduje, aby odvozené třídě přepsat vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="63b7d-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="63b7d-129">Když `MustOverride` – klíčové slovo se používá, definici metody se skládá z jenom na `Sub`, `Function`, nebo `Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="63b7d-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="63b7d-130">Jsou povoleny žádné jiné příkazy a konkrétně neexistuje žádné `End Sub` nebo `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="63b7d-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="63b7d-131">`MustOverride`metody musí být deklarován v `MustInherit` třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="63b7d-132">Předpokládejme, že chcete definovat pro zpracování mzdy třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="63b7d-133">Můžete třeba definovat obecný `Payroll` třídu, která obsahuje `RunPayroll` metoda, která by vypočítala mzdy typické týden.</span><span class="sxs-lookup"><span data-stu-id="63b7d-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="63b7d-134">Poté můžete použít `Payroll` jako základní třída pro více specializované `BonusPayroll` třídy, který může být použit při distribuci bonusy zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="63b7d-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="63b7d-135">`BonusPayroll` Třída může dědit a přepsat, `PayEmployee` metoda definované v základní `Payroll` třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="63b7d-136">V následujícím příkladu definuje základní třídu, `Payroll,` a odvozené třídy `BonusPayroll`, který přepíše metodu zděděné `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="63b7d-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="63b7d-137">A postup `RunPayroll`, vytvoří a pak předá `Payroll` objektu a `BonusPayroll` objekt, který má funkci, `Pay`, který provede `PayEmployee` metoda oba objekty.</span><span class="sxs-lookup"><span data-stu-id="63b7d-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="63b7d-138">MyBase – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="63b7d-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="63b7d-139">`MyBase` – Klíčové slovo chová jako objektová proměnná, která odkazuje na základní třídu aktuální instance třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="63b7d-140">`MyBase`často se používá pro přístup k členy základní třídy, které jsou přepsat nebo Stínovaný v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="63b7d-141">Konkrétně `MyBase.New` se používá k explicitně volání konstruktoru základní třídy z konstruktoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="63b7d-142">Předpokládejme například, že navrhujete odvozené třídy, který přepíše metodu zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="63b7d-143">Přepsaná metoda můžete volat metodu v základní třídě a jak je znázorněno v následující fragment kódu upravit návratovou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="63b7d-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 <span data-ttu-id="63b7d-144">Následující seznam popisuje omezení týkající se použití `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="63b7d-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
-   <span data-ttu-id="63b7d-145">`MyBase`odkazuje na přímé základní třídy a její zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="63b7d-146">Nelze použít pro přístup k `Private` členy ve třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-146">It cannot be used to access `Private` members in the class.</span></span>  
  
-   <span data-ttu-id="63b7d-147">`MyBase`je klíčové slovo, nikoli skutečné objektu.</span><span class="sxs-lookup"><span data-stu-id="63b7d-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="63b7d-148">`MyBase`nelze přiřazený k proměnné, předaný postupy nebo používány `Is` porovnání.</span><span class="sxs-lookup"><span data-stu-id="63b7d-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="63b7d-149">Metoda, `MyBase` vyfiltrování nemá být definován ve třídě okamžitou základní; se místo toho mohou být definovány v nepřímo zděděné základní třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="63b7d-150">Aby odkaz kvalifikovaný `MyBase` pro správnou kompilaci některé základní třída musí obsahovat odpovídající název a typy parametrů, které se zobrazují v volání metody.</span><span class="sxs-lookup"><span data-stu-id="63b7d-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
-   <span data-ttu-id="63b7d-151">Nemůžete použít `MyBase` volat `MustOverride` základní metody třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
-   <span data-ttu-id="63b7d-152">`MyBase`nelze použít k vyfiltrování sám sebe.</span><span class="sxs-lookup"><span data-stu-id="63b7d-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="63b7d-153">Následující kód, proto není platný:</span><span class="sxs-lookup"><span data-stu-id="63b7d-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   <span data-ttu-id="63b7d-154">`MyBase`nelze použít v modulech.</span><span class="sxs-lookup"><span data-stu-id="63b7d-154">`MyBase` cannot be used in modules.</span></span>  
  
-   <span data-ttu-id="63b7d-155">`MyBase`nelze použít pro přístup k členy základní třídy, které jsou označeny jako `Friend` Pokud základní třída je v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="63b7d-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="63b7d-156">Další informace a další příklad najdete v tématu [postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="63b7d-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="63b7d-157">MyClass – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="63b7d-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="63b7d-158">`MyClass` – Klíčové slovo chová jako objektová proměnná, která odkazuje na aktuální instanci třídy v původním implementována.</span><span class="sxs-lookup"><span data-stu-id="63b7d-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="63b7d-159">`MyClass`podobá `Me`, ale každý metod a vlastností volání na `MyClass` je zpracováván jako by byly metody nebo vlastnosti [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="63b7d-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="63b7d-160">Proto metody nebo vlastnosti nemá vliv přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
-   <span data-ttu-id="63b7d-161">`MyClass`je klíčové slovo, nikoli skutečné objektu.</span><span class="sxs-lookup"><span data-stu-id="63b7d-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="63b7d-162">`MyClass`nelze přiřazený k proměnné, předaný postupy nebo používány `Is` porovnání.</span><span class="sxs-lookup"><span data-stu-id="63b7d-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
-   <span data-ttu-id="63b7d-163">`MyClass`odkazuje na třídu obsahující a jeho zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
-   <span data-ttu-id="63b7d-164">`MyClass`lze použít jako kvalifikátory pro `Shared` členy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
-   <span data-ttu-id="63b7d-165">`MyClass`nelze použít uvnitř `Shared` metoda, ale dá se použít uvnitř metody instance přístup sdíleného člena třídy.</span><span class="sxs-lookup"><span data-stu-id="63b7d-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
-   <span data-ttu-id="63b7d-166">`MyClass`nelze použít v standardní moduly.</span><span class="sxs-lookup"><span data-stu-id="63b7d-166">`MyClass` cannot be used in standard modules.</span></span>  
  
-   <span data-ttu-id="63b7d-167">`MyClass`lze použít k vyfiltrování metoda, která je definovaná v základní třídě a která nemá žádnou implementaci metody uvedené v této třídě.</span><span class="sxs-lookup"><span data-stu-id="63b7d-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="63b7d-168">Takový odkaz má stejný význam jako `MyBase.` *metoda*.</span><span class="sxs-lookup"><span data-stu-id="63b7d-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="63b7d-169">Následující příklad porovnává `Me` a `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="63b7d-169">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="63b7d-170">I když `derivedClass` přepsání `testMethod`, `MyClass` – klíčové slovo v `useMyClass` nichž účinnost přepsání a překládá kompilátoru volání základní třída verzi `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="63b7d-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b7d-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="63b7d-171">See Also</span></span>  
 [<span data-ttu-id="63b7d-172">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="63b7d-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="63b7d-173">ME, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="63b7d-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
