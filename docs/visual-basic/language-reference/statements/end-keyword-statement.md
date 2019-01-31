---
title: End <keyword> – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 96dc8ce6b0d3b7545f5caeef43358936e426f566
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273527"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="a3653-102">End \<– klíčové slovo > – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3653-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="a3653-103">Pokud následuje další klíčové slovo, ukončí definici bloku příkazů zavedených v dané klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a3653-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3653-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3653-104">Syntax</span></span>

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="a3653-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a3653-105">Parts</span></span>

|<span data-ttu-id="a3653-106">Část</span><span class="sxs-lookup"><span data-stu-id="a3653-106">Part</span></span>|<span data-ttu-id="a3653-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a3653-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="a3653-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a3653-108">Required.</span></span> <span data-ttu-id="a3653-109">Ukončí definici programovací element.</span><span class="sxs-lookup"><span data-stu-id="a3653-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="a3653-110">Povinnost ukončit `AddHandler` přistupující objekt zahájené odpovídající `AddHandler` příkaz ve vlastním [Event – příkaz](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="a3653-111">Povinnost ukončit definici třídy zahájené odpovídající [Class – příkaz](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="a3653-112">Povinnost ukončit definice výčtu zahájené odpovídající [Enum – příkaz](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="a3653-113">Povinnost ukončit `Custom` definice události zahájené odpovídající [Event – příkaz](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="a3653-114">Povinnost ukončit `Function` definici procedury zahájené odpovídající [Function – příkaz](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="a3653-115">Pokud se zjistí spuštění `End Function` prohlášení, ovládací prvek vrátí volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="a3653-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="a3653-116">Povinnost ukončit `Property` definici procedury zahájené odpovídající [získat příkaz](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="a3653-117">Pokud se zjistí spuštění `End Get` prohlášení, ovládací prvek vrátí příkaz požaduje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3653-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="a3653-118">Povinnost ukončit `If`... `Then`... `Else` blokovat definice zahájené odpovídající `If` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3653-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="a3653-119">Zobrazit [Pokud... Potom... Else – příkaz](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="a3653-120">Povinnost ukončit definici rozhraní zahájené odpovídající [Interface – příkaz](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="a3653-121">Povinnost ukončit modulu definice zahájené odpovídající [Module – příkaz](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="a3653-122">Povinnost ukončit definice oboru názvů zahájené odpovídající [příkaz Namespace](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="a3653-123">Povinnost ukončit definici operátoru zahájené odpovídající [Operator – příkaz](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="a3653-124">Povinnost ukončit definici vlastnosti zahájené odpovídající [Property – příkaz](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="a3653-125">Povinnost ukončit `RaiseEvent` přistupující objekt zahájené odpovídající `RaiseEvent` příkaz ve vlastním [Event – příkaz](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="a3653-126">Povinnost ukončit `RemoveHandler` přistupující objekt zahájené odpovídající `RemoveHandler` příkaz ve vlastním [Event – příkaz](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="a3653-127">Povinnost ukončit `Select`... `Case` blokovat definice zahájené odpovídající `Select` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3653-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="a3653-128">Zobrazit [vyberte... Case – příkaz](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="a3653-129">Povinnost ukončit `Property` definici procedury zahájené odpovídající [nastavit příkaz](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="a3653-130">Pokud se zjistí spuštění `End Set` prohlášení, ovládací prvek vrátí příkaz pro nastavení vlastnosti na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a3653-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="a3653-131">Povinnost ukončit definici struktury zahájené odpovídající [Structure – příkaz](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="a3653-132">Povinnost ukončit `Sub` definici procedury zahájené odpovídající [příkaz Sub](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="a3653-133">Pokud se zjistí spuštění `End Sub` prohlášení, ovládací prvek vrátí volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="a3653-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="a3653-134">Povinnost ukončit `SyncLock` blokovat definice zahájené odpovídající `SyncLock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3653-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="a3653-135">Zobrazit [příkaz SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="a3653-136">Povinnost ukončit `Try`... `Catch`... `Finally` blokovat definice zahájené odpovídající `Try` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3653-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="a3653-137">Zobrazit [zkuste... Catch... Příkaz finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="a3653-138">Povinnost ukončit `While` smyčky definice zahájené odpovídající `While` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3653-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="a3653-139">Zobrazit [během... End While – příkaz](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="a3653-140">Povinnost ukončit `With` blokovat definice zahájené odpovídající `With` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a3653-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="a3653-141">Zobrazit [s... End With – příkaz](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="a3653-142">Direktivy</span><span class="sxs-lookup"><span data-stu-id="a3653-142">Directives</span></span>

<span data-ttu-id="a3653-143">Když uvozená znakem čísla (`#`), `End` – klíčové slovo ukončí blok předzpracování zavedených v direktivě odpovídající.</span><span class="sxs-lookup"><span data-stu-id="a3653-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="a3653-144">Část</span><span class="sxs-lookup"><span data-stu-id="a3653-144">Part</span></span>|<span data-ttu-id="a3653-145">Popis</span><span class="sxs-lookup"><span data-stu-id="a3653-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="a3653-146">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a3653-146">Required.</span></span> <span data-ttu-id="a3653-147">Ukončí definici bloku předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="a3653-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="a3653-148">Povinnost ukončit z externího zdroje bloku zahájené odpovídající [#ExternalSource – direktiva](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="a3653-149">Povinnost ukončit blok podmíněné kompilace zahájené odpovídající `#If` směrnice.</span><span class="sxs-lookup"><span data-stu-id="a3653-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="a3653-150">Zobrazit [#If... Then... #Else – direktivy](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="a3653-151">Povinnost ukončit blok zdrojové oblasti zahájené odpovídající [#Region – direktiva](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a3653-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="a3653-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3653-152">Remarks</span></span>

<span data-ttu-id="a3653-153">[End – příkaz](end-statement.md), bez dodatečné klíčové slovo ukončí provádění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="a3653-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="a3653-154">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="a3653-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="a3653-155">`End` Příkaz bez další klíčové slovo, není podporován.</span><span class="sxs-lookup"><span data-stu-id="a3653-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3653-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3653-156">See also</span></span>

- [<span data-ttu-id="a3653-157">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="a3653-157">End Statement</span></span>](end-statement.md)
