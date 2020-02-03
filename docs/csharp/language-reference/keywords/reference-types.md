---
title: Odkazové typy C# – referenční informace
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744513"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="586ae-102">Typy odkazů (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="586ae-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="586ae-103">V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="586ae-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="586ae-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="586ae-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="586ae-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="586ae-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="586ae-106">S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (s výjimkou proměnných parametrů ref a out, viz [v](in-parameter-modifier.md)tématu modifikátor [ref](ref.md) a [out](out-parameter-modifier.md) ).</span><span class="sxs-lookup"><span data-stu-id="586ae-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="586ae-107">Pro deklaraci typů odkazu se používají následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="586ae-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="586ae-108">class</span><span class="sxs-lookup"><span data-stu-id="586ae-108">class</span></span>](class.md)

- [<span data-ttu-id="586ae-109">interface</span><span class="sxs-lookup"><span data-stu-id="586ae-109">interface</span></span>](interface.md)

- [<span data-ttu-id="586ae-110">delegate</span><span class="sxs-lookup"><span data-stu-id="586ae-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="586ae-111">Jazyk C# nabízí také následující vestavěné typy odkazu:</span><span class="sxs-lookup"><span data-stu-id="586ae-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="586ae-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="586ae-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="586ae-113">object</span><span class="sxs-lookup"><span data-stu-id="586ae-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="586ae-114">string</span><span class="sxs-lookup"><span data-stu-id="586ae-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="586ae-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="586ae-115">See also</span></span>

- [<span data-ttu-id="586ae-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="586ae-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="586ae-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="586ae-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="586ae-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="586ae-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="586ae-119">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="586ae-119">Value types</span></span>](../builtin-types/value-types.md)
