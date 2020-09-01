---
description: Typy odkazů – reference jazyka C#
title: Typy odkazů – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 1a9df3c95d6f5052821be8db5ecf5a8ed99a8ba7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137055"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="c0761-103">Typy odkazů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c0761-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="c0761-104">V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c0761-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="c0761-105">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="c0761-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="c0761-106">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="c0761-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="c0761-107">S typy hodnot každá proměnná má svou vlastní kopii dat a není možné, aby operace s jednou proměnnou ovlivnily jiný (s výjimkou proměnných parametrů ref a out, viz [v](in-parameter-modifier.md)tématu modifikátor [ref](ref.md) a [out](out-parameter-modifier.md) ).</span><span class="sxs-lookup"><span data-stu-id="c0761-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="c0761-108">Pro deklaraci typů odkazu se používají následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="c0761-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="c0761-109">Deník</span><span class="sxs-lookup"><span data-stu-id="c0761-109">class</span></span>](class.md)

- [<span data-ttu-id="c0761-110">prostředí</span><span class="sxs-lookup"><span data-stu-id="c0761-110">interface</span></span>](interface.md)

- [<span data-ttu-id="c0761-111">dostával</span><span class="sxs-lookup"><span data-stu-id="c0761-111">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="c0761-112">Jazyk C# nabízí také následující vestavěné typy odkazu:</span><span class="sxs-lookup"><span data-stu-id="c0761-112">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="c0761-113">dynamic</span><span class="sxs-lookup"><span data-stu-id="c0761-113">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="c0761-114">object</span><span class="sxs-lookup"><span data-stu-id="c0761-114">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="c0761-115">řetezce</span><span class="sxs-lookup"><span data-stu-id="c0761-115">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="c0761-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0761-116">See also</span></span>

- [<span data-ttu-id="c0761-117">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0761-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c0761-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0761-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c0761-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="c0761-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="c0761-120">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="c0761-120">Value types</span></span>](../builtin-types/value-types.md)
