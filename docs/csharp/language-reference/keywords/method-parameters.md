---
title: Parametry metody (Referenční dokumentace jazyka C#)
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
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 35d96066deb866e02f6bf624121376fe3ae94373
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="02ecf-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="02ecf-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="02ecf-103">Parametry deklarovat pro metody bez [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), jsou předány volané metodě hodnotou.</span><span class="sxs-lookup"><span data-stu-id="02ecf-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="02ecf-104">Tuto hodnotu lze změnit v metodě, ale změněné hodnoty nebudou uchována, pokud ovládací prvek předává zpět do volání procedury.</span><span class="sxs-lookup"><span data-stu-id="02ecf-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="02ecf-105">S použitím klíčového slova parametru metody, můžete toto chování změnit.</span><span class="sxs-lookup"><span data-stu-id="02ecf-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="02ecf-106">Tato část popisuje klíčová slova, které můžete použít při deklarování parametry metody:</span><span class="sxs-lookup"><span data-stu-id="02ecf-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="02ecf-107">[Parametry](../../../csharp/language-reference/keywords/params.md) Určuje, že tento parametr může trvat proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="02ecf-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="02ecf-108">[v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Určuje, že tento parametr je předána odkazem, ale je jen pro čtení, volané metodou.</span><span class="sxs-lookup"><span data-stu-id="02ecf-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="02ecf-109">[REF](../../../csharp/language-reference/keywords/ref.md) Určuje, že tento parametr je předána odkazem a může lze číst nebo zapisovat volané metodou.</span><span class="sxs-lookup"><span data-stu-id="02ecf-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="02ecf-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Určuje, že tento parametr je předána odkazem a je zapsán volané metodou.</span><span class="sxs-lookup"><span data-stu-id="02ecf-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="02ecf-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="02ecf-111">See Also</span></span>  
 [<span data-ttu-id="02ecf-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02ecf-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="02ecf-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="02ecf-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="02ecf-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02ecf-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
