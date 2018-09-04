---
title: Odkazové typy (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: f99415fc9a2b728917cdf829ffb9e25823a824dd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538477"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="9ba43-102">Odkazové typy (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9ba43-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="9ba43-103">V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9ba43-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="9ba43-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="9ba43-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="9ba43-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="9ba43-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="9ba43-106">S typy hodnot, každá proměnná má svou vlastní kopii dat, a není možné pro operace v rámci jedné proměnné k ovlivnit další (s výjimkou v případě třídy v ref a out proměnných parametrů; viz [v](in-parameter-modifier.md), [ref](ref.md) a [si](out-parameter-modifier.md) modifikátor parametrů).</span><span class="sxs-lookup"><span data-stu-id="9ba43-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="9ba43-107">Pro deklaraci typů odkazu se používají následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="9ba43-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="9ba43-108">class</span><span class="sxs-lookup"><span data-stu-id="9ba43-108">class</span></span>](class.md)

- [<span data-ttu-id="9ba43-109">interface</span><span class="sxs-lookup"><span data-stu-id="9ba43-109">interface</span></span>](interface.md)

- [<span data-ttu-id="9ba43-110">delegate</span><span class="sxs-lookup"><span data-stu-id="9ba43-110">delegate</span></span>](delegate.md)

 <span data-ttu-id="9ba43-111">Jazyk C# nabízí také následující vestavěné typy odkazu:</span><span class="sxs-lookup"><span data-stu-id="9ba43-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="9ba43-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="9ba43-112">dynamic</span></span>](dynamic.md)

- [<span data-ttu-id="9ba43-113">object</span><span class="sxs-lookup"><span data-stu-id="9ba43-113">object</span></span>](object.md)

- [<span data-ttu-id="9ba43-114">string</span><span class="sxs-lookup"><span data-stu-id="9ba43-114">string</span></span>](string.md)

## <a name="see-also"></a><span data-ttu-id="9ba43-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ba43-115">See also</span></span>

- [<span data-ttu-id="9ba43-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9ba43-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="9ba43-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9ba43-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9ba43-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9ba43-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9ba43-119">Typy</span><span class="sxs-lookup"><span data-stu-id="9ba43-119">Types</span></span>](types.md)
- [<span data-ttu-id="9ba43-120">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="9ba43-120">Value Types</span></span>](value-types.md)