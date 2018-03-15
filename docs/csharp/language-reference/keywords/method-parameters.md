---
title: "Parametry metody (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b20d2d233350cfb9de55cbd07e722082ec311597
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="085e2-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="085e2-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="085e2-103">Parametry deklarovat pro metody bez [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), jsou předány volané metodě hodnotou.</span><span class="sxs-lookup"><span data-stu-id="085e2-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="085e2-104">Tuto hodnotu lze změnit v metodě, ale změněné hodnoty nebudou uchována, pokud ovládací prvek předává zpět do volání procedury.</span><span class="sxs-lookup"><span data-stu-id="085e2-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="085e2-105">S použitím klíčového slova parametru metody, můžete toto chování změnit.</span><span class="sxs-lookup"><span data-stu-id="085e2-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="085e2-106">Tato část popisuje klíčová slova, které můžete použít při deklarování parametry metody:</span><span class="sxs-lookup"><span data-stu-id="085e2-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="085e2-107">params</span><span class="sxs-lookup"><span data-stu-id="085e2-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="085e2-108">in</span><span class="sxs-lookup"><span data-stu-id="085e2-108">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
  
-   [<span data-ttu-id="085e2-109">ref</span><span class="sxs-lookup"><span data-stu-id="085e2-109">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="085e2-110">out</span><span class="sxs-lookup"><span data-stu-id="085e2-110">out</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
  
## <a name="see-also"></a><span data-ttu-id="085e2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="085e2-111">See Also</span></span>  
 [<span data-ttu-id="085e2-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="085e2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="085e2-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="085e2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="085e2-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="085e2-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
