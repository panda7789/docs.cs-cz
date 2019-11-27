---
title: Throw – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352781"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="d61a3-102">Throw – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d61a3-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="d61a3-103">Vyvolá výjimku v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="d61a3-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="d61a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d61a3-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="d61a3-105">Částí</span><span class="sxs-lookup"><span data-stu-id="d61a3-105">Part</span></span>

`expression`\
<span data-ttu-id="d61a3-106">Poskytuje informace o výjimce, která má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="d61a3-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="d61a3-107">Volitelné, pokud je umístěn v příkazu `Catch`, je vyžadováno jinak.</span><span class="sxs-lookup"><span data-stu-id="d61a3-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="d61a3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d61a3-108">Remarks</span></span>

<span data-ttu-id="d61a3-109">Příkaz `Throw` vyvolá výjimku, kterou lze zpracovat pomocí strukturovaného kódu zpracování výjimek (`Try`...`Catch`...`Finally`) nebo nestrukturovaný kód pro zpracování výjimek (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="d61a3-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="d61a3-110">Můžete použít příkaz `Throw` k zachycení chyb v rámci kódu, protože Visual Basic přesune zásobník volání, dokud nenajde příslušný kód pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="d61a3-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="d61a3-111">Příkaz `Throw` bez výrazu lze použít pouze v příkazu `Catch`. v takovém případě příkaz znovu vyvolá výjimku, která je aktuálně zpracována příkazem `Catch`.</span><span class="sxs-lookup"><span data-stu-id="d61a3-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="d61a3-112">Příkaz `Throw` obnoví zásobník volání pro výjimku `expression`.</span><span class="sxs-lookup"><span data-stu-id="d61a3-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="d61a3-113">Pokud není zadán `expression`, zásobník volání zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="d61a3-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="d61a3-114">Můžete získat přístup k zásobníku volání pro výjimku prostřednictvím vlastnosti <xref:System.Exception.StackTrace%2A>.</span><span class="sxs-lookup"><span data-stu-id="d61a3-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="d61a3-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d61a3-115">Example</span></span>

<span data-ttu-id="d61a3-116">Následující kód používá příkaz `Throw` k vyvolání výjimky:</span><span class="sxs-lookup"><span data-stu-id="d61a3-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="d61a3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d61a3-117">See also</span></span>

- [<span data-ttu-id="d61a3-118">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="d61a3-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="d61a3-119">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="d61a3-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
