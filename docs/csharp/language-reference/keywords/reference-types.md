---
title: "Typy odkazů (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e671abac6d49170ac76e4633c4f55c50dcbe01c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="5d167-102">Typy odkazů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5d167-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="5d167-103">V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5d167-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="5d167-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="5d167-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="5d167-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5d167-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="5d167-106">S typy hodnot, každá proměnná má svou vlastní kopii dat a není možné pro operace na jednu proměnnou ovlivnit dalších (s výjimkou u v ref a out proměnné parametrů; viz [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) a [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) – modifikátor parametrů).</span><span class="sxs-lookup"><span data-stu-id="5d167-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter modifier).</span></span>  
  
 <span data-ttu-id="5d167-107">Pro deklaraci typů odkazu se používají následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="5d167-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="5d167-108">class</span><span class="sxs-lookup"><span data-stu-id="5d167-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="5d167-109">interface</span><span class="sxs-lookup"><span data-stu-id="5d167-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="5d167-110">delegate</span><span class="sxs-lookup"><span data-stu-id="5d167-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="5d167-111">Jazyk C# nabízí také následující vestavěné typy odkazu:</span><span class="sxs-lookup"><span data-stu-id="5d167-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="5d167-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="5d167-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="5d167-113">object</span><span class="sxs-lookup"><span data-stu-id="5d167-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="5d167-114">string</span><span class="sxs-lookup"><span data-stu-id="5d167-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d167-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d167-115">See Also</span></span>  
 [<span data-ttu-id="5d167-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5d167-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5d167-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5d167-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d167-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5d167-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5d167-119">Typy</span><span class="sxs-lookup"><span data-stu-id="5d167-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="5d167-120">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="5d167-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
