---
title: Parametry metody – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 4011cbd3bc9306b64df87b1fcde48f1f41df8240
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602038"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="47c2a-102">Parametry metody (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="47c2a-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="47c2a-103">Parametry deklarované pro metodu bez [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md)jsou předány metodě volané hodnotou.</span><span class="sxs-lookup"><span data-stu-id="47c2a-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="47c2a-104">Tuto hodnotu lze v metodě změnit, ale změněná hodnota nebude zachována, pokud řízení projde zpět do volající procedury.</span><span class="sxs-lookup"><span data-stu-id="47c2a-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="47c2a-105">Pomocí klíčového slova parametru metody můžete toto chování změnit.</span><span class="sxs-lookup"><span data-stu-id="47c2a-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="47c2a-106">Tato část popisuje klíčová slova, která můžete použít při deklaraci parametrů metody:</span><span class="sxs-lookup"><span data-stu-id="47c2a-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="47c2a-107">[parametry](./params.md) určuje, že tento parametr může mít proměnlivý počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="47c2a-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="47c2a-108">[v](./in-parameter-modifier.md) určuje, že tento parametr je předán odkazem, ale je čten pouze volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="47c2a-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="47c2a-109">[ref](./ref.md) určuje, že tento parametr je předán odkazem a lze jej číst nebo zapsat pomocí volané metody.</span><span class="sxs-lookup"><span data-stu-id="47c2a-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="47c2a-110">[out](./out-parameter-modifier.md) určuje, že tento parametr je předán odkazem a je zapsán metodou volané.</span><span class="sxs-lookup"><span data-stu-id="47c2a-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="47c2a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47c2a-111">See also</span></span>

- [<span data-ttu-id="47c2a-112">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="47c2a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47c2a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="47c2a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47c2a-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47c2a-114">C# Keywords</span></span>](./index.md)
