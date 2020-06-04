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
ms.openlocfilehash: 9ae1a307e8c886166d516140b7f100a411cedcfa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410371"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="59adb-102">Přiřazení proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59adb-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="59adb-103">Použijete normální příkaz přiřazení k přiřazení objektu proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="59adb-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="59adb-104">Můžete přiřadit výraz objektu nebo klíčové slovo [Nothing](../../../language-reference/nothing.md) , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="59adb-104">You can assign an object expression or the [Nothing](../../../language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="59adb-105">`Nothing`znamená, že k proměnné není aktuálně přiřazen žádný objekt.</span><span class="sxs-lookup"><span data-stu-id="59adb-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="59adb-106">Inicializace</span><span class="sxs-lookup"><span data-stu-id="59adb-106">Initialization</span></span>

<span data-ttu-id="59adb-107">Když váš kód začíná běžet, vaše proměnné objektu jsou inicializovány na `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="59adb-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="59adb-108">Ty, jejichž deklarace zahrnují inicializaci, jsou znovu inicializovány na hodnoty, které zadáte při spuštění příkazů deklarace.</span><span class="sxs-lookup"><span data-stu-id="59adb-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="59adb-109">Do své deklarace můžete přidat inicializaci pomocí klíčového slova [New](../../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="59adb-109">You can include initialization in your declaration by using the [New](../../../language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="59adb-110">Následující příkazy deklarace deklaruje objektové proměnné `testUri` a `ver` přiřadí jim konkrétní objekty.</span><span class="sxs-lookup"><span data-stu-id="59adb-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="59adb-111">Každý používá jeden z přetížených konstruktorů příslušné třídy pro inicializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="59adb-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="59adb-112">Zrušení přidružení</span><span class="sxs-lookup"><span data-stu-id="59adb-112">Disassociation</span></span>

<span data-ttu-id="59adb-113">Nastavení proměnné objektu pro `Nothing` přerušit přidružení proměnné k jakémukoli konkrétnímu objektu.</span><span class="sxs-lookup"><span data-stu-id="59adb-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="59adb-114">Tím zabráníte nechtěné změně objektu změnou proměnné.</span><span class="sxs-lookup"><span data-stu-id="59adb-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="59adb-115">Také umožňuje otestovat, zda proměnná objektu odkazuje na platný objekt, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="59adb-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="59adb-116">Pokud objekt, na který proměnná odkazuje, je v jiné aplikaci, nemůže tento test určit, zda byla daná aplikace ukončena nebo zda právě neověřovala objekt.</span><span class="sxs-lookup"><span data-stu-id="59adb-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="59adb-117">Objektová proměnná s hodnotou `Nothing` je také označována jako *odkaz s hodnotou null*.</span><span class="sxs-lookup"><span data-stu-id="59adb-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="59adb-118">Aktuální instance</span><span class="sxs-lookup"><span data-stu-id="59adb-118">Current Instance</span></span>

<span data-ttu-id="59adb-119">*Aktuální instance* objektu je ten, ve kterém je aktuálně spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="59adb-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="59adb-120">Vzhledem k tomu, že veškerý kód provede v rámci procedury, aktuální instance je ta, ve které byl procedura vyvolána.</span><span class="sxs-lookup"><span data-stu-id="59adb-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="59adb-121">`Me`Klíčové slovo funguje jako proměnná objektu odkazující na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="59adb-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="59adb-122">Pokud procedura není [sdílená](../../../language-reference/modifiers/shared.md), může pomocí `Me` klíčového slova získat ukazatel na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="59adb-122">If a procedure is not [Shared](../../../language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="59adb-123">Sdílené procedury nelze přidružit ke konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="59adb-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="59adb-124">Použití `Me` je zvláště užitečné pro předání aktuální instance do procedury v jiném modulu.</span><span class="sxs-lookup"><span data-stu-id="59adb-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="59adb-125">Předpokládejme například, že máte několik dokumentů XML a chcete do nich přidat nějaký standardní text.</span><span class="sxs-lookup"><span data-stu-id="59adb-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="59adb-126">Následující příklad definuje proceduru, která to provede.</span><span class="sxs-lookup"><span data-stu-id="59adb-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="59adb-127">Každý objekt dokumentu XML pak může zavolat proceduru a předat aktuální instanci jako argument.</span><span class="sxs-lookup"><span data-stu-id="59adb-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="59adb-128">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="59adb-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="59adb-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="59adb-129">See also</span></span>

- [<span data-ttu-id="59adb-130">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="59adb-130">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="59adb-131">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="59adb-131">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="59adb-132">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="59adb-132">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="59adb-133">Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59adb-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="59adb-134">Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci.</span><span class="sxs-lookup"><span data-stu-id="59adb-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="59adb-135">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="59adb-135">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
