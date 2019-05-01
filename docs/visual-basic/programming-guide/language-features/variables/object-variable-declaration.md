---
title: Deklarace proměnné objektu (Visual Basic)
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
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959975"
---
# <a name="object-variable-declaration-visual-basic"></a><span data-ttu-id="f3f0d-102">Deklarace proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3f0d-102">Object Variable Declaration (Visual Basic)</span></span>
<span data-ttu-id="f3f0d-103">Pomocí příkazu normální deklarace můžete deklarovat proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-103">You use a normal declaration statement to declare an object variable.</span></span> <span data-ttu-id="f3f0d-104">Pro datový typ, můžete zadat buď `Object` (to znamená, [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md)) nebo konkrétnější třídy, ze kterého má být vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-104">For the data type, you specify either `Object` (that is, the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) or a more specific class from which the object is to be created.</span></span>  
  
 <span data-ttu-id="f3f0d-105">Deklarace proměnné jako `Object` je stejné jako deklarování jako <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-105">Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f3f0d-106">Pokud deklarujete proměnnou s konkrétní objekt třídy, má přístup k všechny metody a vlastnosti, které jsou vystavené třídy a třídy, ze které dědí.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-106">When you declare a variable with a specific object class, it can access all the methods and properties exposed by that class and the classes from which it inherits.</span></span> <span data-ttu-id="f3f0d-107">Pokud deklarujete proměnnou <xref:System.Object>, má přístup pouze členové <xref:System.Object> třídy, pokud posunete `Option Strict Off` umožňující pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-107">If you declare the variable with <xref:System.Object>, it can access only the members of the <xref:System.Object> class, unless you turn `Option Strict Off` to allow late binding.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="f3f0d-108">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="f3f0d-108">Declaration Syntax</span></span>  
 <span data-ttu-id="f3f0d-109">Použijte následující syntaxi pro deklaraci proměnné objektu:</span><span class="sxs-lookup"><span data-stu-id="f3f0d-109">Use the following syntax to declare an object variable:</span></span>  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 <span data-ttu-id="f3f0d-110">Můžete také určit [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), nebo [statické](../../../../visual-basic/language-reference/modifiers/static.md) v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-110">You can also specify [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), or [Static](../../../../visual-basic/language-reference/modifiers/static.md) in the declaration.</span></span> <span data-ttu-id="f3f0d-111">Následující příklad deklarace jsou platné:</span><span class="sxs-lookup"><span data-stu-id="f3f0d-111">The following example declarations are valid:</span></span>  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a><span data-ttu-id="f3f0d-112">Časné vazby a pozdní vazby</span><span class="sxs-lookup"><span data-stu-id="f3f0d-112">Late Binding and Early Binding</span></span>  
 <span data-ttu-id="f3f0d-113">Někdy Neznámý určité třídy, dokud váš kód běží.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-113">Sometimes the specific class is unknown until your code runs.</span></span> <span data-ttu-id="f3f0d-114">V takovém případě je třeba deklarovat proměnnou objektu s `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-114">In this case, you must declare the object variable with the `Object` data type.</span></span> <span data-ttu-id="f3f0d-115">Tím se vytvoří Obecné referenční informace pro libovolný typ objektu a v době běhu je přiřazena určité třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-115">This creates a general reference to any type of object, and the specific class is assigned at run time.</span></span> <span data-ttu-id="f3f0d-116">Tento postup se nazývá *pozdní vazby*.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-116">This is called *late binding*.</span></span> <span data-ttu-id="f3f0d-117">Pozdní vazba vyžaduje další čas spuštění.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-117">Late binding requires additional execution time.</span></span> <span data-ttu-id="f3f0d-118">Také omezuje kód do metody a vlastnosti třídy, které jste přiřadili naposledy k němu.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-118">It also limits your code to the methods and properties of the class you have most recently assigned to it.</span></span> <span data-ttu-id="f3f0d-119">To může způsobit chyby za běhu, pokud váš kód se pokusí o přístup ke členům jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-119">This can cause run-time errors if your code attempts to access members of a different class.</span></span>  
  
 <span data-ttu-id="f3f0d-120">Pokud znáte konkrétní třídu v době kompilace, by měla deklarovat proměnnou objekt této třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-120">When you know the specific class at compile time, you should declare the object variable to be of that class.</span></span> <span data-ttu-id="f3f0d-121">Tento postup se nazývá *časné vazby*.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-121">This is called *early binding*.</span></span> <span data-ttu-id="f3f0d-122">Časná vazba zlepšuje výkon a garantuje váš kód přístup k metodám a vlastnostem konkrétní třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-122">Early binding improves performance and guarantees your code access to all the methods and properties of the specific class.</span></span> <span data-ttu-id="f3f0d-123">V předchozím příkladu deklarace, pokud proměnné `objA` používá jenom objekty třídy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, měli byste zadat `As System.Windows.Forms.Label` v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-123">In the preceding example declarations, if variable `objA` uses only objects of class <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, you should specify `As System.Windows.Forms.Label` in its declaration.</span></span>  
  
### <a name="advantages-of-early-binding"></a><span data-ttu-id="f3f0d-124">Výhody časná vazba</span><span class="sxs-lookup"><span data-stu-id="f3f0d-124">Advantages of Early Binding</span></span>  
 <span data-ttu-id="f3f0d-125">Deklarace proměnné objektu jako konkrétní třídy přináší řadu výhod:</span><span class="sxs-lookup"><span data-stu-id="f3f0d-125">Declaring an object variable as a specific class gives you several advantages:</span></span>  
  
- <span data-ttu-id="f3f0d-126">Kontrola automatické typu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-126">Automatic type checking</span></span>  
  
- <span data-ttu-id="f3f0d-127">Zaručeno, že přístup všech členů určité třídy</span><span class="sxs-lookup"><span data-stu-id="f3f0d-127">Guaranteed access to all members of the specific class</span></span>  
  
- <span data-ttu-id="f3f0d-128">Podpora Microsoft IntelliSense v editoru kódu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-128">Microsoft IntelliSense support in the Code Editor</span></span>  
  
- <span data-ttu-id="f3f0d-129">Lepší čitelnost kódu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-129">Improved readability of your code</span></span>  
  
- <span data-ttu-id="f3f0d-130">Méně chyb v kódu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-130">Fewer errors in your code</span></span>  
  
- <span data-ttu-id="f3f0d-131">Chyby zachycena v době kompilace spíše než čas spuštění</span><span class="sxs-lookup"><span data-stu-id="f3f0d-131">Errors caught at compile time rather than run time</span></span>  
  
- <span data-ttu-id="f3f0d-132">Rychlejší provádění kódu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-132">Faster code execution</span></span>  
  
## <a name="access-to-object-variable-members"></a><span data-ttu-id="f3f0d-133">Přístup k proměnné členů objektu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-133">Access to Object Variable Members</span></span>  
 <span data-ttu-id="f3f0d-134">Když `Option Strict` zapnuté `On`, proměnné objektu přístupné pouze metody a vlastnosti třídy, se kterým se deklaruje.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-134">When `Option Strict` is turned `On`, an object variable can access only the methods and properties of the class with which you declare it.</span></span> <span data-ttu-id="f3f0d-135">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-135">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="f3f0d-136">V tomto příkladu `p` lze použít pouze členové <xref:System.Object> třídu, která nejsou zahrnuté `Left` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-136">In this example, `p` can use only the members of the <xref:System.Object> class itself, which do not include the `Left` property.</span></span> <span data-ttu-id="f3f0d-137">Na druhé straně `q` byl deklarován jako typ <xref:System.Windows.Forms.Label>, takže ho můžete použít všechny metody a vlastnosti <xref:System.Windows.Forms.Label> třídy v <xref:System.Windows.Forms> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-137">On the other hand, `q` was declared to be of type <xref:System.Windows.Forms.Label>, so it can use all the methods and properties of the <xref:System.Windows.Forms.Label> class in the <xref:System.Windows.Forms> namespace.</span></span>  
  
## <a name="flexibility-of-object-variables"></a><span data-ttu-id="f3f0d-138">Flexibilita objektových proměnných</span><span class="sxs-lookup"><span data-stu-id="f3f0d-138">Flexibility of Object Variables</span></span>  
 <span data-ttu-id="f3f0d-139">Při práci s objekty v hierarchii dědičnosti, máte možnost volby z třídy pro deklarace objektových proměnných.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-139">When working with objects in an inheritance hierarchy, you have a choice of which class to use for declaring your object variables.</span></span> <span data-ttu-id="f3f0d-140">Při vytváření tohoto výběru, musí zajistit rovnováhu mezi flexibilitu přiřazení objektu pro přístup k členům třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-140">In making this choice, you must balance flexibility of object assignment against access to members of a class.</span></span> <span data-ttu-id="f3f0d-141">Představte si třeba, který vede k hierarchii dědičnosti <xref:System.Windows.Forms.Form?displayProperty=nameWithType> třídy:</span><span class="sxs-lookup"><span data-stu-id="f3f0d-141">For example, consider the inheritance hierarchy that leads to the <xref:System.Windows.Forms.Form?displayProperty=nameWithType> class:</span></span>  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 <span data-ttu-id="f3f0d-142">Předpokládejme, že vaše aplikace definuje třídu formulář s názvem `specialForm`, který dědí z třídy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-142">Suppose your application defines a form class called `specialForm`, which inherits from class <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="f3f0d-143">Můžete deklarovat proměnné objektu, který se vztahuje konkrétně pro `specialForm`, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-143">You can declare an object variable that refers specifically to `specialForm`, as the following example shows.</span></span>  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 <span data-ttu-id="f3f0d-144">Deklarace v předchozím příkladu omezuje proměnnou `nextForm` pro objekty třídy `specialForm`, ale také umožní všechny metody a vlastnosti `specialForm` k dispozici `nextForm`, stejně jako všechny členy všechny třídy, ze kterého `specialForm` dědí.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-144">The declaration in the preceding example limits the variable `nextForm` to objects of class `specialForm`, but it also makes all the methods and properties of `specialForm` available to `nextForm`, as well as all the members of all the classes from which `specialForm` inherits.</span></span>  
  
 <span data-ttu-id="f3f0d-145">Provedete proměnné objektu obecnější deklarováním typu <xref:System.Windows.Forms.Form>, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-145">You can make an object variable more general by declaring it to be of type <xref:System.Windows.Forms.Form>, as the following example shows.</span></span>  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="f3f0d-146">Deklarace v předchozím příkladu umožňuje přiřadit libovolného formuláře v aplikaci k `anyForm`.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-146">The declaration in the preceding example lets you assign any form in your application to `anyForm`.</span></span> <span data-ttu-id="f3f0d-147">Nicméně i když `anyForm` můžete přístup ke všem členům třídy <xref:System.Windows.Forms.Form>, se nemůže používat žádné další metody nebo vlastnosti, které jsou definovány pro konkrétní formulářů, jako `specialForm`.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-147">However, although `anyForm` can access all the members of class <xref:System.Windows.Forms.Form>, it cannot use any of the additional methods or properties defined for specific forms such as `specialForm`.</span></span>  
  
 <span data-ttu-id="f3f0d-148">Všechny členy základní třídy jsou k dispozici k odvozeným třídám, ale další členy odvozené třídy nejsou k dispozici pro základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f3f0d-148">All the members of a base class are available to derived classes, but the additional members of a derived class are unavailable to the base class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f0d-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3f0d-149">See also</span></span>

- [<span data-ttu-id="f3f0d-150">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="f3f0d-150">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="f3f0d-151">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="f3f0d-151">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="f3f0d-152">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="f3f0d-152">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="f3f0d-153">Postupy: Deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3f0d-153">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="f3f0d-154">Postupy: Přístup k členům v objektu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-154">How to: Access Members of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [<span data-ttu-id="f3f0d-155">Operátor New</span><span class="sxs-lookup"><span data-stu-id="f3f0d-155">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="f3f0d-156">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="f3f0d-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f3f0d-157">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="f3f0d-157">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
