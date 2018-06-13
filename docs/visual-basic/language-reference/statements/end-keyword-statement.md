---
title: End &lt;– klíčové slovo&gt; – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605261"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="6865b-102">End &lt;– klíčové slovo&gt; – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6865b-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="6865b-103">Když následuje další klíčové slovo, ukončí definici bloku příkaz zavedených v tomto – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6865b-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6865b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6865b-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="6865b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6865b-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="6865b-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6865b-106">Required.</span></span> <span data-ttu-id="6865b-107">Ukončí definici programovací element.</span><span class="sxs-lookup"><span data-stu-id="6865b-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="6865b-108">Požadovaný pro ukončení `AddHandler` přistupujícího objektu spuštěno pomocí odpovídající `AddHandler` příkaz v vlastní [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="6865b-109">Požadovaný pro ukončení definice třídy spuštěno pomocí odpovídající [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="6865b-110">Požadovaný pro ukončení definice výčtu spuštěno pomocí odpovídající [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="6865b-111">Požadovaný pro ukončení `Custom` událostí definice spuštěno pomocí odpovídající [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="6865b-112">Požadovaný pro ukončení `Function` definice procedury spuštěno pomocí odpovídající [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="6865b-113">Pokud provádění dojde `End``Function` ovládací prvek příkaz vrátí kód volání.</span><span class="sxs-lookup"><span data-stu-id="6865b-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="6865b-114">Požadovaný pro ukončení `Property` definice procedury spuštěno pomocí odpovídající [získat příkaz](../../../visual-basic/language-reference/statements/get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="6865b-115">Pokud provádění dojde `End``Get` ovládací prvek prohlášení, vrátí příkaz žádají o hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6865b-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="6865b-116">Požadovaný pro ukončení `If`... `Then`... `Else` blokovat definice spuštěno pomocí odpovídající `If` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6865b-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="6865b-117">V tématu [Pokud... Potom... Else – příkaz](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="6865b-118">Požadovaný pro ukončení definice rozhraní spuštěno pomocí odpovídající [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="6865b-119">Požadovaný pro ukončení definice modulu spuštěno pomocí odpovídající [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="6865b-120">Požadovaný pro ukončení definici oboru názvů spuštěno pomocí odpovídající [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="6865b-121">Požadovaný pro ukončení definici operátor spuštěno pomocí odpovídající [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="6865b-122">Požadovaný pro ukončení definice vlastnosti spuštěno pomocí odpovídající [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="6865b-123">Požadovaný pro ukončení `RaiseEvent` přistupujícího objektu spuštěno pomocí odpovídající `RaiseEvent` příkaz v vlastní [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="6865b-124">Požadovaný pro ukončení `RemoveHandler` přistupujícího objektu spuštěno pomocí odpovídající `RemoveHandler` příkaz v vlastní [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="6865b-125">Požadovaný pro ukončení `Select`... `Case` blokovat definice spuštěno pomocí odpovídající `Select` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6865b-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="6865b-126">V tématu [vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="6865b-127">Požadovaný pro ukončení `Property` definice procedury spuštěno pomocí odpovídající [příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="6865b-128">Pokud provádění dojde `End``Set` ovládací prvek příkaz, vrátí příkaz Nastavení hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6865b-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="6865b-129">Požadovaný pro ukončení definice struktury spuštěno pomocí odpovídající [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="6865b-130">Požadovaný pro ukončení `Sub` definice procedury spuštěno pomocí odpovídající [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="6865b-131">Pokud provádění dojde `End``Sub` ovládací prvek příkaz vrátí kód volání.</span><span class="sxs-lookup"><span data-stu-id="6865b-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="6865b-132">Požadovaný pro ukončení `SyncLock` blokovat definice spuštěno pomocí odpovídající `SyncLock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6865b-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="6865b-133">V tématu [SyncLock – příkaz](../../../visual-basic/language-reference/statements/synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="6865b-134">Požadovaný pro ukončení `Try`... `Catch`... `Finally` blokovat definice spuštěno pomocí odpovídající `Try` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6865b-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="6865b-135">V tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="6865b-136">Požadovaný pro ukončení `While` cykly definice spuštěno pomocí odpovídající `While` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6865b-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="6865b-137">V tématu [při... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="6865b-138">Požadovaný pro ukončení `With` blokovat definice spuštěno pomocí odpovídající `With` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6865b-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="6865b-139">V tématu [s... End With – příkaz](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6865b-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6865b-140">Remarks</span></span>  
 <span data-ttu-id="6865b-141">[End – příkaz](../../../visual-basic/language-reference/statements/end-statement.md), bez další klíčového slova, ukončí provádění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="6865b-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="6865b-142">Když uvozená znakem čísla (`#`), `End` – klíčové slovo ukončí blok předběžného zpracování zaváděné odpovídající direktivu.</span><span class="sxs-lookup"><span data-stu-id="6865b-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="6865b-143">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6865b-143">Required.</span></span> <span data-ttu-id="6865b-144">Ukončí definici předběžného zpracování bloku.</span><span class="sxs-lookup"><span data-stu-id="6865b-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="6865b-145">Požadovaný pro ukončení bloku externí zdroj, který je spuštěno pomocí odpovídající [#ExternalSource – direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="6865b-146">Požadovaný pro ukončení blok Podmíněná kompilace spuštěno pomocí odpovídající `#If` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="6865b-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="6865b-147">V tématu [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="6865b-148">Požadovaný pro ukončení blok oblast zdroj spuštěno pomocí odpovídající [#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="6865b-149">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="6865b-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="6865b-150">`End` Příkaz bez další klíčového slova, není podporován.</span><span class="sxs-lookup"><span data-stu-id="6865b-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6865b-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="6865b-151">See Also</span></span>  
 [<span data-ttu-id="6865b-152">Příkaz End</span><span class="sxs-lookup"><span data-stu-id="6865b-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
