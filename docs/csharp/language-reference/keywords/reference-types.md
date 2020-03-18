---
title: Typy odkazů – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: b2d6cc94c11ca6305a75e9ee489af53ad957201e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744513"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="f88a7-102">Typy odkazů (odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f88a7-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="f88a7-103">V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f88a7-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="f88a7-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="f88a7-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="f88a7-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f88a7-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="f88a7-106">U typů hodnot má každá proměnná vlastní kopii dat a není možné, aby operace na jedné proměnné ovlivnily druhou proměnnou (s výjimkou v případě proměnných parametrů in, ref a out; [viz](in-parameter-modifier.md)modifikátor parametrů [, ref](ref.md) a [out).](out-parameter-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="f88a7-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="f88a7-107">Pro deklaraci typů odkazu se používají následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="f88a7-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="f88a7-108">Třída</span><span class="sxs-lookup"><span data-stu-id="f88a7-108">class</span></span>](class.md)

- [<span data-ttu-id="f88a7-109">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f88a7-109">interface</span></span>](interface.md)

- [<span data-ttu-id="f88a7-110">delegát</span><span class="sxs-lookup"><span data-stu-id="f88a7-110">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="f88a7-111">Jazyk C# nabízí také následující vestavěné typy odkazu:</span><span class="sxs-lookup"><span data-stu-id="f88a7-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="f88a7-112">Dynamické</span><span class="sxs-lookup"><span data-stu-id="f88a7-112">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="f88a7-113">Objekt</span><span class="sxs-lookup"><span data-stu-id="f88a7-113">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="f88a7-114">Řetězec</span><span class="sxs-lookup"><span data-stu-id="f88a7-114">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="f88a7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f88a7-115">See also</span></span>

- [<span data-ttu-id="f88a7-116">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f88a7-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f88a7-117">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f88a7-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f88a7-118">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f88a7-118">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f88a7-119">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="f88a7-119">Value types</span></span>](../builtin-types/value-types.md)
