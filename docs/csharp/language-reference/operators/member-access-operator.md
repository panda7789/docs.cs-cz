---
title: . Operator - C# odkaz
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689200"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cfcb9-103">.</span><span class="sxs-lookup"><span data-stu-id="cfcb9-103">.</span></span> <span data-ttu-id="cfcb9-104">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cfcb9-104">operator (C# Reference)</span></span>

<span data-ttu-id="cfcb9-105">Tečka, `.`, se obvykle používá pro přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="cfcb9-105">The dot, `.`, is typically used for member access.</span></span>

<span data-ttu-id="cfcb9-106">Můžete použít `.` token pro přístup k oboru názvů nebo typ, jak ukazují následující příklady:</span><span class="sxs-lookup"><span data-stu-id="cfcb9-106">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="cfcb9-107">Použití `.` pro přístup k vnořené oboru názvů v oboru názvů, jako následující příklad [ `using` směrnice](../keywords/using-directive.md) ukazuje:</span><span class="sxs-lookup"><span data-stu-id="cfcb9-107">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- <span data-ttu-id="cfcb9-108">Použití `.` do formuláře *kvalifikovaný název* pro přístup k typu v rámci oboru názvů, jak ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="cfcb9-108">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  <span data-ttu-id="cfcb9-109">Použít [ `using` směrnice](../keywords/using-directive.md) provést volitelné použijte kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="cfcb9-109">Use the [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="cfcb9-110">Použití `.` přístup [členy typu](../../programming-guide/classes-and-structs/index.md#members), statické a nestatické, pokud jako ukazuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="cfcb9-110">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

<span data-ttu-id="cfcb9-111">Můžete také použít `.` k vyvolání [– metoda rozšíření](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="cfcb9-111">You can also use `.` to invoke an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="cfcb9-112">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="cfcb9-112">Operator overloadability</span></span>

<span data-ttu-id="cfcb9-113">Operátor `.` nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="cfcb9-113">The operator `.` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cfcb9-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cfcb9-114">C# language specification</span></span>

<span data-ttu-id="cfcb9-115">Další informace najdete v tématu [přístup ke členu](~/_csharplang/spec/expressions.md#member-access) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="cfcb9-115">For more information, see the [Member access](~/_csharplang/spec/expressions.md#member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfcb9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfcb9-116">See also</span></span>

- [<span data-ttu-id="cfcb9-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cfcb9-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cfcb9-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cfcb9-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cfcb9-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cfcb9-119">C# Operators</span></span>](index.md)
- <span data-ttu-id="cfcb9-120">[?. a? operátory]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="cfcb9-120">[?. and ?[] operators](null-conditional-operators.md)</span></span>