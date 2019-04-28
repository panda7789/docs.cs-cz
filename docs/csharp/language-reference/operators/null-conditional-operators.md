---
title: Podmíněné operátory s Null - C# odkaz
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688875"
---
# <a name="-and--null-conditional-operators-c-reference"></a><span data-ttu-id="6ae83-102">?.</span><span class="sxs-lookup"><span data-stu-id="6ae83-102">?.</span></span> <span data-ttu-id="6ae83-103">a? [] podmíněné operátory s null (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="6ae83-103">and ?[] null-conditional operators (C# Reference)</span></span>

<span data-ttu-id="6ae83-104">Testuje hodnotu levý operand pro hodnotu null, před provedením přístup ke členu (`?.`) nebo indexu (`?[]`) časový limit operace; vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="6ae83-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="6ae83-105">Tyto operátory usnadňuje psaní méně kód pro zpracování null kontrol, zejména pro sestupné řazení do datové struktury.</span><span class="sxs-lookup"><span data-stu-id="6ae83-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

<span data-ttu-id="6ae83-106">Podmíněné operátory s null jsou short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="6ae83-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="6ae83-107">Pokud jedna operace v řetězci Podmíněný člen přístup a index operace vrátí hodnotu null, zastaví se zbytek spuštění do řetězce.</span><span class="sxs-lookup"><span data-stu-id="6ae83-107">If one operation in a chain of conditional member access and index operations returns null, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="6ae83-108">V následujícím příkladu `E` neprovede, pokud `A`, `B`, nebo `C` vyhodnotí na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6ae83-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

<span data-ttu-id="6ae83-109">Další možností použití pro přístup ke členům podmíněných null je vyvoláním delegátů způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="6ae83-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="6ae83-110">Starý způsob vyžaduje kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="6ae83-110">The old way requires code like the following:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

<span data-ttu-id="6ae83-111">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="6ae83-111">The new way is much simpler:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="6ae83-112">Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, uchovávání výsledek v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="6ae83-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="6ae83-113">Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="6ae83-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="6ae83-114">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="6ae83-114">Language specifications</span></span>

<span data-ttu-id="6ae83-115">Další informace najdete v tématu [Null podmíněného operátoru](~/_csharplang/spec/expressions.md#null-conditional-operator) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ae83-115">For more information, see [Null-conditional operator](~/_csharplang/spec/expressions.md#null-conditional-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="6ae83-116">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6ae83-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae83-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ae83-117">See also</span></span>

- [<span data-ttu-id="6ae83-118">?? (operátoru nulového sjednocení)</span><span class="sxs-lookup"><span data-stu-id="6ae83-118">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="6ae83-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6ae83-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ae83-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6ae83-120">C# Programming Guide</span></span>](../../programming-guide/index.md)