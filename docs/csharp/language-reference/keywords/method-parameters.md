---
title: Parametry metody - c# odkaz
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713372"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="43a4f-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="43a4f-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="43a4f-103">Parametry deklarované pro metodu bez [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md)jsou předány volané metodě hodnotou.</span><span class="sxs-lookup"><span data-stu-id="43a4f-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="43a4f-104">Tuto hodnotu lze změnit v metodě, ale změněná hodnota nebude zachována, když ovládací prvek předá zpět do volající procedury.</span><span class="sxs-lookup"><span data-stu-id="43a4f-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="43a4f-105">Pomocí klíčového slova parametr u metody můžete toto chování změnit.</span><span class="sxs-lookup"><span data-stu-id="43a4f-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="43a4f-106">Tato část popisuje klíčová slova, která můžete použít při deklarování parametrů metody:</span><span class="sxs-lookup"><span data-stu-id="43a4f-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="43a4f-107">[params](./params.md) určuje, že tento parametr může mít proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="43a4f-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="43a4f-108">[v](./in-parameter-modifier.md) určuje, že tento parametr je předán odkazem, ale je přečten pouze volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="43a4f-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="43a4f-109">[ref](./ref.md) určuje, že tento parametr je předán odkazem a může být přečten nebo zapsán volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="43a4f-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="43a4f-110">[určuje,](./out-parameter-modifier.md) že tento parametr je předán odkazem a je zapsán volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="43a4f-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="43a4f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="43a4f-111">See also</span></span>

- [<span data-ttu-id="43a4f-112">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43a4f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43a4f-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43a4f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43a4f-114">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="43a4f-114">C# Keywords</span></span>](./index.md)
