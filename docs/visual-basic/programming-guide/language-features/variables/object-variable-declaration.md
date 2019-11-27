---
title: Deklarace proměnné objektu
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351806"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="be7da-102">Deklarace proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be7da-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="be7da-103">Použijete normální příkaz deklarace k deklaraci objektové proměnné.</span><span class="sxs-lookup"><span data-stu-id="be7da-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="be7da-104">Pro datový typ zadáte buď `Object` (tj. [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md)), nebo konkrétnější třídu, ze které má být objekt vytvořen.</span><span class="sxs-lookup"><span data-stu-id="be7da-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="be7da-105">Deklarace proměnné jako `Object` je stejná jako deklarace jako <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be7da-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="be7da-106">Pokud deklarujete proměnnou s konkrétní objektovou třídou, může získat přístup ke všem metodám a vlastnostem vystaveným touto třídou a třídám, ze kterých dědí.</span><span class="sxs-lookup"><span data-stu-id="be7da-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="be7da-107">Pokud deklarujete proměnnou s <xref:System.Object>, může přistupovat pouze k členům třídy <xref:System.Object>, pokud nezapnete `Option Strict Off` povolit pozdní vazby.</span><span class="sxs-lookup"><span data-stu-id="be7da-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="be7da-108">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="be7da-108">Declaration Syntax</span></span>  
 <span data-ttu-id="be7da-109">K deklaraci objektové proměnné použijte následující syntax:</span><span class="sxs-lookup"><span data-stu-id="be7da-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="be7da-110">V deklaraci můžete také zadat [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)nebo [static](../../../../visual-basic/language-reference/modifiers/static.md) .</span><span class="sxs-lookup"><span data-stu-id="be7da-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="be7da-111">Následující příklady deklarací jsou platné:</span><span class="sxs-lookup"><span data-stu-id="be7da-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="be7da-112">Pozdní vazba a počáteční vazba</span><span class="sxs-lookup"><span data-stu-id="be7da-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="be7da-113">Někdy je konkrétní třída neznámá, dokud se váš kód nespustí.</span><span class="sxs-lookup"><span data-stu-id="be7da-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="be7da-114">V takovém případě je nutné deklarovat objektovou proměnnou s datovým typem `Object`.</span><span class="sxs-lookup"><span data-stu-id="be7da-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="be7da-115">Tím se vytvoří obecný odkaz na jakýkoli typ objektu a specifická třída je přiřazena za běhu.</span><span class="sxs-lookup"><span data-stu-id="be7da-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="be7da-116">Tato metoda se nazývá *pozdní vazba*.</span><span class="sxs-lookup"><span data-stu-id="be7da-116">This is called *late binding*.</span></span> <span data-ttu-id="be7da-117">Pozdní vazba vyžaduje další čas spuštění.</span><span class="sxs-lookup"><span data-stu-id="be7da-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="be7da-118">Také omezuje váš kód na metody a vlastnosti třídy, kterou jste nedávno přiřadili.</span><span class="sxs-lookup"><span data-stu-id="be7da-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="be7da-119">To může způsobit chyby v době běhu, pokud se váš kód pokusí o přístup k členům jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="be7da-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="be7da-120">Pokud znáte konkrétní třídu v době kompilace, měli byste deklarovat objektovou proměnnou, která má být danou třídou.</span><span class="sxs-lookup"><span data-stu-id="be7da-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="be7da-121">Tato metoda se nazývá *časná vazba*.</span><span class="sxs-lookup"><span data-stu-id="be7da-121">This is called *early binding*.</span></span> <span data-ttu-id="be7da-122">Předčasné vázání zvyšuje výkon a zaručuje přístup kódu ke všem metodám a vlastnostem konkrétní třídy.</span><span class="sxs-lookup"><span data-stu-id="be7da-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="be7da-123">V předchozím příkladu deklarace, pokud proměnná `objA` používá pouze objekty <xref:System.Windows.Forms.Label?displayProperty=nameWithType>třídy, měli byste zadat `As System.Windows.Forms.Label` ve své deklaraci.</span><span class="sxs-lookup"><span data-stu-id="be7da-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="be7da-124">Výhody prvotní vazby</span><span class="sxs-lookup"><span data-stu-id="be7da-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="be7da-125">Deklarování proměnné objektu jako konkrétní třídy poskytuje několik výhod:</span><span class="sxs-lookup"><span data-stu-id="be7da-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="be7da-126">Automatická kontrola typu</span><span class="sxs-lookup"><span data-stu-id="be7da-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="be7da-127">Zaručit přístup ke všem členům konkrétní třídy</span><span class="sxs-lookup"><span data-stu-id="be7da-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="be7da-128">Podpora technologie Microsoft IntelliSense v editoru kódu</span><span class="sxs-lookup"><span data-stu-id="be7da-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="be7da-129">Zlepšení čitelnosti kódu</span><span class="sxs-lookup"><span data-stu-id="be7da-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="be7da-130">Méně chyb v kódu</span><span class="sxs-lookup"><span data-stu-id="be7da-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="be7da-131">Chyby zachycené v době kompilace namísto běhu</span><span class="sxs-lookup"><span data-stu-id="be7da-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="be7da-132">Rychlejší provádění kódu</span><span class="sxs-lookup"><span data-stu-id="be7da-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="be7da-133">Přístup k členům proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="be7da-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="be7da-134">Když je `Option Strict` `On`, proměnná objektu může přistupovat pouze k metodám a vlastnostem třídy, se kterou deklarujete.</span><span class="sxs-lookup"><span data-stu-id="be7da-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="be7da-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="be7da-135">The following example illustrates this.</span></span>  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 <span data-ttu-id="be7da-136">V tomto příkladu může `p` použít pouze členy <xref:System.Object> třídy, které neobsahují vlastnost `Left`.</span><span class="sxs-lookup"><span data-stu-id="be7da-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="be7da-137">Na druhé straně `q` byla deklarována jako typu <xref:System.Windows.Forms.Label>, takže může použít všechny metody a vlastnosti třídy <xref:System.Windows.Forms.Label> v oboru názvů <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="be7da-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="be7da-138">Flexibilita objektových proměnných</span><span class="sxs-lookup"><span data-stu-id="be7da-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="be7da-139">Při práci s objekty v hierarchii dědičnosti máte možnost výběru třídy, která se má použít pro deklaraci proměnných objektu.</span><span class="sxs-lookup"><span data-stu-id="be7da-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="be7da-140">Při výběru této možnosti je nutné rovnováhu mezi přiřazením objektu a přístupem ke členům třídy.</span><span class="sxs-lookup"><span data-stu-id="be7da-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="be7da-141">Zvažte například hierarchii dědičnosti, která vede na třídu <xref:System.Windows.Forms.Form?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="be7da-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="be7da-142">Předpokládejme, že vaše aplikace definuje třídu formuláře nazvanou `specialForm`, která dědí z třídy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="be7da-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="be7da-143">Můžete deklarovat objektovou proměnnou, která odkazuje konkrétně na `specialForm`, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="be7da-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="be7da-144">Deklarace v předchozím příkladu omezuje proměnnou `nextForm` na objekty třídy `specialForm`, ale také zpřístupňuje všechny metody a vlastnosti `specialForm` k dispozici pro `nextForm`a také všechny členy všech tříd, ze kterých `specialForm` dědí.</span><span class="sxs-lookup"><span data-stu-id="be7da-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="be7da-145">Objekt, který je obecnější, lze vytvořit tak, že deklarujete, že je typu <xref:System.Windows.Forms.Form>, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="be7da-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="be7da-146">Deklarace v předchozím příkladu umožňuje přiřadit libovolný formulář v aplikaci k `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="be7da-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="be7da-147">I když ale `anyForm` mají přístup ke všem členům třídy <xref:System.Windows.Forms.Form>, nemůže použít žádnou z dalších metod nebo vlastností definovaných pro konkrétní formuláře, jako je například `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="be7da-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="be7da-148">Všichni členové základní třídy jsou k dispozici pro odvozené třídy, ale další členy odvozené třídy nejsou pro základní třídu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="be7da-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7da-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be7da-149">See also</span></span>

- [<span data-ttu-id="be7da-150">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="be7da-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="be7da-151">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="be7da-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="be7da-152">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="be7da-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="be7da-153">Postupy: deklarace objektové proměnné a přiřazení objektu k němu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be7da-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="be7da-154">Postupy: Přístup ke členům v objektu</span><span class="sxs-lookup"><span data-stu-id="be7da-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="be7da-155">Operátor New</span><span class="sxs-lookup"><span data-stu-id="be7da-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="be7da-156">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="be7da-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="be7da-157">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="be7da-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
