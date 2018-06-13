---
title: Parametry metody (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 8a8d300661eec42030900dd9ee85a17e66aa0922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269343"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="242b4-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="242b4-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="242b4-103">Parametry deklarovat pro metody bez [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), jsou předány volané metodě hodnotou.</span><span class="sxs-lookup"><span data-stu-id="242b4-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="242b4-104">Tuto hodnotu lze změnit v metodě, ale změněné hodnoty nebudou uchována, pokud ovládací prvek předává zpět do volání procedury.</span><span class="sxs-lookup"><span data-stu-id="242b4-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="242b4-105">S použitím klíčového slova parametru metody, můžete toto chování změnit.</span><span class="sxs-lookup"><span data-stu-id="242b4-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="242b4-106">Tato část popisuje klíčová slova, které můžete použít při deklarování parametry metody:</span><span class="sxs-lookup"><span data-stu-id="242b4-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="242b4-107">[Parametry](../../../csharp/language-reference/keywords/params.md) Určuje, že tento parametr může trvat proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="242b4-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="242b4-108">[v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Určuje, že tento parametr je předána odkazem, ale je jen pro čtení, volané metodou.</span><span class="sxs-lookup"><span data-stu-id="242b4-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="242b4-109">[REF](../../../csharp/language-reference/keywords/ref.md) Určuje, že tento parametr je předána odkazem a může lze číst nebo zapisovat volané metodou.</span><span class="sxs-lookup"><span data-stu-id="242b4-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="242b4-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Určuje, že tento parametr je předána odkazem a je zapsán volané metodou.</span><span class="sxs-lookup"><span data-stu-id="242b4-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="242b4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="242b4-111">See Also</span></span>  
 [<span data-ttu-id="242b4-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="242b4-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="242b4-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="242b4-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="242b4-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="242b4-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
