---
title: -&gt; Operator - C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: bb1ccd026f403e68565c5c7681943d8017578d01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234887"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="4f66c-102">-&gt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4f66c-102">-&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="4f66c-103">Operátor přístupu členů ukazatel `->` kombinuje ukazatel nepřímý odkaz a členské přístup.</span><span class="sxs-lookup"><span data-stu-id="4f66c-103">The pointer member access operator `->` combines pointer indirection and member access.</span></span>

<span data-ttu-id="4f66c-104">Pokud `x` je ukazatel typu `T*` a `y` je přístupný člen `T`, výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="4f66c-104">If `x` is a pointer of the type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="4f66c-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="4f66c-105">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="4f66c-106">`->` Operátor vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="4f66c-106">The `->` operator requires [unsafe](../keywords/unsafe.md) context.</span></span>

<span data-ttu-id="4f66c-107">Další informace najdete v tématu [postupy: přístup ke členu pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="4f66c-107">For more information, see [How to: access a member with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4f66c-108">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="4f66c-108">Operator overloadability</span></span>

<span data-ttu-id="4f66c-109">`->` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="4f66c-109">The `->` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4f66c-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4f66c-110">C# language specification</span></span>

<span data-ttu-id="4f66c-111">Další informace najdete v tématu [přístupu k členovi](~/_csharplang/spec/unsafe-code.md#pointer-member-access) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f66c-111">For more information, see the [Pointer member access](~/_csharplang/spec/unsafe-code.md#pointer-member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f66c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f66c-112">See also</span></span>

- [<span data-ttu-id="4f66c-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4f66c-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4f66c-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4f66c-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4f66c-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4f66c-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4f66c-116">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="4f66c-116">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
