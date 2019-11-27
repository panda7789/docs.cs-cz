---
title: End <keyword> – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343737"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="29bae-102">End \<– klíčové slovo > příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29bae-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="29bae-103">Po následování klíčového slova další se ukončí definice bloku příkazu, který je představený tímto klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="29bae-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="29bae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29bae-104">Syntax</span></span>

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
  
## <a name="parts"></a><span data-ttu-id="29bae-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="29bae-105">Parts</span></span>

|<span data-ttu-id="29bae-106">Částí</span><span class="sxs-lookup"><span data-stu-id="29bae-106">Part</span></span>|<span data-ttu-id="29bae-107">Popis</span><span class="sxs-lookup"><span data-stu-id="29bae-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="29bae-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="29bae-108">Required.</span></span> <span data-ttu-id="29bae-109">Ukončí definici programovacího prvku.</span><span class="sxs-lookup"><span data-stu-id="29bae-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="29bae-110">Vyžadovaná k ukončení přístupového objektu `AddHandler` začal pomocí odpovídajícího příkazu `AddHandler` ve vlastním [příkazu události](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="29bae-111">Požadováno pro ukončení definice třídy zahájené párovým [příkazem třídy](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="29bae-112">Požadováno pro ukončení definice výčtu zahájené párovým [příkazem výčtu](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="29bae-113">Vyžadovaná pro ukončení definice události `Custom` zahájená párovým [příkazem události](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="29bae-114">Požadováno pro ukončení definice `Function` procedury zahájené párovým [příkazem funkce](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="29bae-115">Pokud spuštění narazí na příkaz `End Function`, ovládací prvek se vrátí volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="29bae-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="29bae-116">Vyžadovaná k ukončení definice `Property` procedury, kterou začaly párovým [příkazem Get](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="29bae-117">Pokud spuštění narazí na příkaz `End Get`, ovládací prvek se vrátí do příkazu, který požaduje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="29bae-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="29bae-118">Vyžadovaná k ukončení `If`...`Then`...`Else` definice bloku začala pomocí odpovídajícího `If`ho příkazu.</span><span class="sxs-lookup"><span data-stu-id="29bae-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="29bae-119">Zjistit [, zda... Pak... ELSE – příkaz](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="29bae-120">Požadováno pro ukončení definice rozhraní, kterou začaly pomocí odpovídajícího [příkazu rozhraní](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="29bae-121">Vyžadovaná k ukončení definice modulu zahájené párovým [příkazem modulu](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="29bae-122">Požadováno pro ukončení definice oboru názvů zahájené párovým [příkazem Namespace](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="29bae-123">Požadováno pro ukončení definice operátora zahájena párovým [příkazem operátoru](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="29bae-124">Požadováno pro ukončení definice vlastnosti zahájené v rámci odpovídajícího [příkazu vlastnosti](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="29bae-125">Vyžadovaná k ukončení přístupového objektu `RaiseEvent` začal pomocí odpovídajícího příkazu `RaiseEvent` ve vlastním [příkazu události](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="29bae-126">Vyžadovaná k ukončení přístupového objektu `RemoveHandler` začal pomocí odpovídajícího příkazu `RemoveHandler` ve vlastním [příkazu události](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="29bae-127">Vyžadovaná k ukončení `Select`...`Case` definice bloku začala pomocí odpovídajícího příkazu `Select`.</span><span class="sxs-lookup"><span data-stu-id="29bae-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="29bae-128">Viz [Vybrat... Příkaz Case](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="29bae-129">Požadováno pro ukončení definice `Property` procedury, kterou začaly pomocí odpovídajícího [příkazu set](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="29bae-130">Pokud spuštění narazí na příkaz `End Set`, vrátí se ovládací prvek do příkazu, který nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="29bae-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="29bae-131">Požadováno pro ukončení definice struktury zahájené [příkazem odpovídajícího struktury](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="29bae-132">Požadováno pro ukončení definice `Sub` procedury zahájené párovým [příkazem Sub sub](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="29bae-133">Pokud spuštění narazí na příkaz `End Sub`, ovládací prvek se vrátí volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="29bae-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="29bae-134">Požadováno pro ukončení definice `SyncLock` bloku zahájené párovým příkazem `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="29bae-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="29bae-135">Viz [příkaz SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="29bae-136">Požadavek na ukončení `Try`...`Catch`...`Finally` definice bloku začala párovým příkazem `Try`.</span><span class="sxs-lookup"><span data-stu-id="29bae-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="29bae-137">Viz [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="29bae-138">Vyžadovaná k ukončení definice `While` smyčky začala pomocí odpovídajícího příkazu `While`.</span><span class="sxs-lookup"><span data-stu-id="29bae-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="29bae-139">Viz [while... Příkaz End While](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="29bae-140">Požadováno pro ukončení definice `With` bloku zahájené párovým příkazem `With`.</span><span class="sxs-lookup"><span data-stu-id="29bae-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="29bae-141">Viz [s... Příkaz end with](with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="29bae-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="29bae-142">Direktivy</span><span class="sxs-lookup"><span data-stu-id="29bae-142">Directives</span></span>

<span data-ttu-id="29bae-143">Pokud předchází znaménko čísla (`#`), klíčové slovo `End` ukončí blok předzpracování, který zavedla odpovídající direktiva.</span><span class="sxs-lookup"><span data-stu-id="29bae-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="29bae-144">Částí</span><span class="sxs-lookup"><span data-stu-id="29bae-144">Part</span></span>|<span data-ttu-id="29bae-145">Popis</span><span class="sxs-lookup"><span data-stu-id="29bae-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="29bae-146">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="29bae-146">Required.</span></span> <span data-ttu-id="29bae-147">Ukončí definici bloku předzpracování.</span><span class="sxs-lookup"><span data-stu-id="29bae-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="29bae-148">Požadováno pro ukončení externího bloku zdroje zahájeného pomocí vyhovující [direktivy #ExternalSource](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="29bae-149">Požadováno pro ukončení podmíněného kompilačního bloku zahájeného pomocí vyhovující direktivy `#If`.</span><span class="sxs-lookup"><span data-stu-id="29bae-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="29bae-150">Viz [#If... Then... #Else direktivy](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="29bae-151">Požadováno pro ukončení bloku zdrojové oblasti, který začal odpovídat [direktivě #Region](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="29bae-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="29bae-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29bae-152">Remarks</span></span>

<span data-ttu-id="29bae-153">[Příkaz end](end-statement.md)bez dalšího klíčového slova ukončí provádění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="29bae-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="29bae-154">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="29bae-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="29bae-155">Příkaz `End` bez dalšího klíčového slova není podporován.</span><span class="sxs-lookup"><span data-stu-id="29bae-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29bae-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29bae-156">See also</span></span>

- [<span data-ttu-id="29bae-157">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="29bae-157">End Statement</span></span>](end-statement.md)
