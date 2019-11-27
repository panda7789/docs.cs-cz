---
title: Přiřazení proměnné objektu
ms.date: 07/20/2015
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
ms.openlocfilehash: 93de17490935d6d5cad01000e9ee3e2fe55bd16c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351821"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="69937-102">Přiřazení proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69937-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="69937-103">Použijete normální příkaz přiřazení k přiřazení objektu proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="69937-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="69937-104">Můžete přiřadit výraz objektu nebo klíčové slovo [Nothing](../../../../visual-basic/language-reference/nothing.md) , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69937-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="69937-105">`Nothing` znamená, že k proměnné není aktuálně přiřazen žádný objekt.</span><span class="sxs-lookup"><span data-stu-id="69937-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="69937-106">Inicializace</span><span class="sxs-lookup"><span data-stu-id="69937-106">Initialization</span></span>

<span data-ttu-id="69937-107">Když váš kód začíná běžet, vaše proměnné objektu jsou inicializovány na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="69937-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="69937-108">Ty, jejichž deklarace zahrnují inicializaci, jsou znovu inicializovány na hodnoty, které zadáte při spuštění příkazů deklarace.</span><span class="sxs-lookup"><span data-stu-id="69937-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="69937-109">Do své deklarace můžete přidat inicializaci pomocí klíčového slova [New](../../../../visual-basic/language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="69937-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="69937-110">Následující příkazy deklarace deklaruje proměnné objektu `testUri` a `ver` a přiřadí jim konkrétní objekty.</span><span class="sxs-lookup"><span data-stu-id="69937-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="69937-111">Každý používá jeden z přetížených konstruktorů příslušné třídy pro inicializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="69937-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="69937-112">Zrušení přidružení</span><span class="sxs-lookup"><span data-stu-id="69937-112">Disassociation</span></span>

<span data-ttu-id="69937-113">Nastavení proměnné objektu pro `Nothing` přestane přidružení proměnné k jakémukoli konkrétnímu objektu.</span><span class="sxs-lookup"><span data-stu-id="69937-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="69937-114">Tím zabráníte nechtěné změně objektu změnou proměnné.</span><span class="sxs-lookup"><span data-stu-id="69937-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="69937-115">Také umožňuje otestovat, zda proměnná objektu odkazuje na platný objekt, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="69937-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="69937-116">Pokud objekt, na který proměnná odkazuje, je v jiné aplikaci, nemůže tento test určit, zda byla daná aplikace ukončena nebo zda právě neověřovala objekt.</span><span class="sxs-lookup"><span data-stu-id="69937-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="69937-117">Proměnná objektu s hodnotou `Nothing` se také označuje jako *odkaz s hodnotou null*.</span><span class="sxs-lookup"><span data-stu-id="69937-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="69937-118">Aktuální instance</span><span class="sxs-lookup"><span data-stu-id="69937-118">Current Instance</span></span>

<span data-ttu-id="69937-119">*Aktuální instance* objektu je ten, ve kterém je aktuálně spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="69937-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="69937-120">Vzhledem k tomu, že veškerý kód provede v rámci procedury, aktuální instance je ta, ve které byl procedura vyvolána.</span><span class="sxs-lookup"><span data-stu-id="69937-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="69937-121">Klíčové slovo `Me` funguje jako proměnná objektu odkazující na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="69937-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="69937-122">Pokud procedura není [sdílená](../../../../visual-basic/language-reference/modifiers/shared.md), může pomocí klíčového slova `Me` získat ukazatel na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="69937-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="69937-123">Sdílené procedury nelze přidružit ke konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="69937-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="69937-124">Použití `Me` je zvláště užitečné pro předání aktuální instance do procedury v jiném modulu.</span><span class="sxs-lookup"><span data-stu-id="69937-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="69937-125">Předpokládejme například, že máte několik dokumentů XML a chcete do nich přidat nějaký standardní text.</span><span class="sxs-lookup"><span data-stu-id="69937-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="69937-126">Následující příklad definuje proceduru, která to provede.</span><span class="sxs-lookup"><span data-stu-id="69937-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="69937-127">Každý objekt dokumentu XML pak může zavolat proceduru a předat aktuální instanci jako argument.</span><span class="sxs-lookup"><span data-stu-id="69937-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="69937-128">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="69937-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="69937-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69937-129">See also</span></span>

- [<span data-ttu-id="69937-130">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="69937-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="69937-131">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="69937-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="69937-132">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="69937-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="69937-133">Postupy: deklarace objektové proměnné a přiřazení objektu k němu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69937-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="69937-134">Postupy: Nastavení objektové proměnné tak, aby neodkazovala na žádnou instanci</span><span class="sxs-lookup"><span data-stu-id="69937-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="69937-135">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="69937-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
