---
title: "Přiřazení proměnné objektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb6b53bebddc1c9cf1b9088e96ded36a5e1c5242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="8ef1a-102">Přiřazení proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ef1a-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="8ef1a-103">Příkaz normální přiřazení můžete použít k přiřazení objektu k proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="8ef1a-104">Můžete přiřadit výraz objekt nebo [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo, jako následující příklad znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="8ef1a-105">`Nothing`znamená, že žádný objekt aktuálně přiřazená k proměnné.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="8ef1a-106">Inicializace</span><span class="sxs-lookup"><span data-stu-id="8ef1a-106">Initialization</span></span>  
 <span data-ttu-id="8ef1a-107">Pokud váš kód zahájí spuštění, proměnné se inicializují k objektu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="8ef1a-108">Ty, jejichž deklarace zahrnují inicializace jsou opětovně inicializovány na hodnoty, které určíte při provedení deklarační příkazy.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="8ef1a-109">Inicializace můžete zahrnout do vaší deklarace pomocí [nový](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="8ef1a-110">Následující příkazy deklarace deklarace objektové proměnné `testUri` a `ver` a k nim přiřadíte konkrétní objekty.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="8ef1a-111">Každá používá jednu z přetížené konstruktory příslušné třídy k inicializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="8ef1a-112">Zrušení přidružení</span><span class="sxs-lookup"><span data-stu-id="8ef1a-112">Disassociation</span></span>  
 <span data-ttu-id="8ef1a-113">Nastavení proměnné objektu `Nothing` ze přidružení konkrétního objektu proměnné.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="8ef1a-114">To brání omylem Změna objektu změnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="8ef1a-115">Také umožňuje otestovat, zda proměnná objektu odkazuje na platný objekt, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="8ef1a-116">Pokud objekt, který vaše proměnná odkazuje v jiné aplikaci, tento test nelze určit, zda má aplikace ukončeno, nebo jenom zrušena objekt.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="8ef1a-117">Proměnné objektu s hodnotou `Nothing` se označuje taky jako *odkaz s hodnotou null*.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="8ef1a-118">Aktuální Instance</span><span class="sxs-lookup"><span data-stu-id="8ef1a-118">Current Instance</span></span>  
 <span data-ttu-id="8ef1a-119">*Aktuální instance* objektu je ten, ve kterém je aktuálně provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="8ef1a-120">Vzhledem k tomu, že veškerý kód provede uvnitř procedury, aktuální instance je ten, ve kterém byl vyvolán postupu.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="8ef1a-121">`Me` – Klíčové slovo funguje jako proměnná objektu odkazuje na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="8ef1a-122">Pokud není procedury [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md), můžete použít `Me` – klíčové slovo k získání ukazatele na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="8ef1a-123">Sdílené procedury nelze přidružit k určité instance třídy.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="8ef1a-124">Pomocí `Me` je obzvláště užitečné pro předávání aktuální instance proceduře v jiném modulu.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="8ef1a-125">Předpokládejme například, máte několik dokumentů XML a chcete přidat některé standardní text pro všechny z nich.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="8ef1a-126">V následujícím příkladu definuje postup zajímá.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="8ef1a-127">Každý objekt dokumentu XML může pak voláním procedury a předat jako argument jeho aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="8ef1a-128">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="8ef1a-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ef1a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef1a-129">See Also</span></span>  
 [<span data-ttu-id="8ef1a-130">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="8ef1a-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="8ef1a-131">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="8ef1a-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="8ef1a-132">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="8ef1a-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="8ef1a-133">Postupy: deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ef1a-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="8ef1a-134">Postupy: nastavení proměnné objektu neodkazovala na žádnou instanci</span><span class="sxs-lookup"><span data-stu-id="8ef1a-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [<span data-ttu-id="8ef1a-135">ME, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="8ef1a-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
