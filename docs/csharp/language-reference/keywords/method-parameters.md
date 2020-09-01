---
description: Parametry metody – reference jazyka C#
title: Parametry metody – reference jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134403"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="e98eb-103">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e98eb-103">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="e98eb-104">Parametry deklarované pro metodu bez [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md)jsou předány metodě volané hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e98eb-104">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="e98eb-105">Tuto hodnotu lze v metodě změnit, ale změněná hodnota nebude zachována, pokud řízení projde zpět do volající procedury.</span><span class="sxs-lookup"><span data-stu-id="e98eb-105">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="e98eb-106">Pomocí klíčového slova parametru metody můžete toto chování změnit.</span><span class="sxs-lookup"><span data-stu-id="e98eb-106">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="e98eb-107">Tato část popisuje klíčová slova, která můžete použít při deklaraci parametrů metody:</span><span class="sxs-lookup"><span data-stu-id="e98eb-107">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="e98eb-108">[parametry](./params.md) určuje, že tento parametr může mít proměnlivý počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="e98eb-108">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="e98eb-109">[v](./in-parameter-modifier.md) určuje, že tento parametr je předán odkazem, ale je čten pouze volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="e98eb-109">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="e98eb-110">[ref](./ref.md) určuje, že tento parametr je předán odkazem a lze jej číst nebo zapsat pomocí volané metody.</span><span class="sxs-lookup"><span data-stu-id="e98eb-110">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="e98eb-111">[out](./out-parameter-modifier.md) určuje, že tento parametr je předán odkazem a je zapsán metodou volané.</span><span class="sxs-lookup"><span data-stu-id="e98eb-111">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e98eb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e98eb-112">See also</span></span>

- [<span data-ttu-id="e98eb-113">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e98eb-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e98eb-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e98eb-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e98eb-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e98eb-115">C# Keywords</span></span>](./index.md)
