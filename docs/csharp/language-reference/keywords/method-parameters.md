---
title: Parametry metody (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 446a5239fa1de8559dea50f7e8b8869aed0297c5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389997"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="ac2c5-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ac2c5-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="ac2c5-103">Deklarované parametry pro metody bez [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md), jsou předávány hodnotou volané metody.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="ac2c5-104">Tuto hodnotu můžete změnit v metodě, ale změněné hodnoty nebudou uchována, při řízení se předá zpět do volající procedury.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="ac2c5-105">Toto chování můžete změnit pomocí klíčové slovo parametru metody.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="ac2c5-106">Tato část popisuje klíčová slova, které můžete použít při deklarování parametrů metody:</span><span class="sxs-lookup"><span data-stu-id="ac2c5-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="ac2c5-107">[params](../../../csharp/language-reference/keywords/params.md) Určuje, že tento parametr může trvat proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="ac2c5-108">[v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Určuje, že tento parametr je předána odkazem, ale je jen pro čtení ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="ac2c5-109">[REF](../../../csharp/language-reference/keywords/ref.md) Určuje, že tento parametr je předána odkazem a mohou lze číst nebo zapisovat ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="ac2c5-110">[navýšení kapacity](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Určuje, že tento parametr je předána odkazem a je zapsaný ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="ac2c5-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ac2c5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac2c5-111">See Also</span></span>

- [<span data-ttu-id="ac2c5-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ac2c5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ac2c5-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ac2c5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ac2c5-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ac2c5-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
