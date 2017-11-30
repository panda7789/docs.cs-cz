---
title: "Typy odkazů (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="b9875-102">Typy odkazů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b9875-102">Reference Types (C# Reference)</span></span>
<span data-ttu-id="b9875-103">V jazyce C# existují dva druhy typů: typy odkazu a typy hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9875-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="b9875-104">Proměnné typů odkazu ukládají odkazy na data (objekty), zatímco proměnné typů hodnoty data přímo obsahují příslušná data.</span><span class="sxs-lookup"><span data-stu-id="b9875-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="b9875-105">V případě typů odkazu mohou dvě proměnné odkazovat na stejný objekt. Operace v rámci jedné proměnné tedy mohou ovlivňovat objekt odkazovaný jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="b9875-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="b9875-106">S typy hodnot, každá proměnná má svou vlastní kopii dat a není možné pro operace na jednu proměnnou ovlivnit dalších (s výjimkou v případě ref a out proměnné parametrů najdete v části [ref](../../../csharp/language-reference/keywords/ref.md) a [vnější parametr Modifikátor](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="b9875-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of ref and out parameter variables, see [ref](../../../csharp/language-reference/keywords/ref.md) and [out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).</span></span>  
  
 <span data-ttu-id="b9875-107">Pro deklaraci typů odkazu se používají následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="b9875-107">The following keywords are used to declare reference types:</span></span>  
  
-   [<span data-ttu-id="b9875-108">– Třída</span><span class="sxs-lookup"><span data-stu-id="b9875-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="b9875-109">rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9875-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="b9875-110">Delegát</span><span class="sxs-lookup"><span data-stu-id="b9875-110">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="b9875-111">Jazyk C# nabízí také následující vestavěné typy odkazu:</span><span class="sxs-lookup"><span data-stu-id="b9875-111">C# also provides the following built-in reference types:</span></span>  
  
-   [<span data-ttu-id="b9875-112">dynamické</span><span class="sxs-lookup"><span data-stu-id="b9875-112">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [<span data-ttu-id="b9875-113">objekt</span><span class="sxs-lookup"><span data-stu-id="b9875-113">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
  
-   [<span data-ttu-id="b9875-114">řetězec</span><span class="sxs-lookup"><span data-stu-id="b9875-114">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9875-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9875-115">See Also</span></span>  
 [<span data-ttu-id="b9875-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9875-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b9875-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b9875-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b9875-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9875-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b9875-119">Typy</span><span class="sxs-lookup"><span data-stu-id="b9875-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="b9875-120">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="b9875-120">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
