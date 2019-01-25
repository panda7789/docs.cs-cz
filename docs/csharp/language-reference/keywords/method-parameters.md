---
title: Parametry metody - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 72917d356ed0fce96502faeef68494c7fdcb214f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564757"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="5f495-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5f495-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="5f495-103">Deklarované parametry pro metody bez [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md), jsou předávány hodnotou volané metody.</span><span class="sxs-lookup"><span data-stu-id="5f495-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="5f495-104">Tuto hodnotu můžete změnit v metodě, ale změněné hodnoty nebudou uchována, při řízení se předá zpět do volající procedury.</span><span class="sxs-lookup"><span data-stu-id="5f495-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="5f495-105">Toto chování můžete změnit pomocí klíčové slovo parametru metody.</span><span class="sxs-lookup"><span data-stu-id="5f495-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="5f495-106">Tato část popisuje klíčová slova, které můžete použít při deklarování parametrů metody:</span><span class="sxs-lookup"><span data-stu-id="5f495-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="5f495-107">[params](../../../csharp/language-reference/keywords/params.md) Určuje, že tento parametr může trvat proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="5f495-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="5f495-108">[v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Určuje, že tento parametr je předána odkazem, ale je jen pro čtení ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="5f495-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="5f495-109">[REF](../../../csharp/language-reference/keywords/ref.md) Určuje, že tento parametr je předána odkazem a mohou lze číst nebo zapisovat ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="5f495-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="5f495-110">[navýšení kapacity](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Určuje, že tento parametr je předána odkazem a je zapsaný ve volané metody.</span><span class="sxs-lookup"><span data-stu-id="5f495-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5f495-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f495-111">See also</span></span>

- [<span data-ttu-id="5f495-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f495-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="5f495-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5f495-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5f495-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5f495-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
