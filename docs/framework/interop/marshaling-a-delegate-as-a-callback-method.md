---
title: "Zařazování delegáta jako metody zpětného volání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d9269261c6c0ce7573e0a8e298111971ae591c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="be053-102">Zařazování delegáta jako metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="be053-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="be053-103">Tento příklad znázorňuje, jak předat delegáti nespravované funkce byl očekáván ukazatelů na funkce.</span><span class="sxs-lookup"><span data-stu-id="be053-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="be053-104">Delegát je třída, která může pojmout odkazu na třídu metodě a je ekvivalentní ukazatel na funkci zajišťující bezpečnost typů nebo funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="be053-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be053-105">Při použití delegáta uvnitř volání modul common language runtime chrání delegát nebudou uvolnění z paměti po dobu trvání tohoto volání.</span><span class="sxs-lookup"><span data-stu-id="be053-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="be053-106">Ale pokud nespravované funkce ukládá delegát používat po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud nebude dokončeno nespravované funkce s delegátem.</span><span class="sxs-lookup"><span data-stu-id="be053-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="be053-107">Další informace najdete v tématu [HandleRef ukázka](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) a [GCHandle ukázka](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span><span class="sxs-lookup"><span data-stu-id="be053-107">For more information, see the [HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) and [GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span></span>  
  
 <span data-ttu-id="be053-108">Zpětné volání – Ukázka používá následující nespravované funkce s jejich původní deklarace funkce:</span><span class="sxs-lookup"><span data-stu-id="be053-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="be053-109">**TestCallBack** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="be053-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="be053-110">**TestCallBack2** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="be053-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="be053-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) vlastní nespravované knihovnu, která obsahuje implementaci výše uvedených funkcí.</span><span class="sxs-lookup"><span data-stu-id="be053-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="be053-112">V této ukázce `LibWrap` třída obsahuje spravovaných prototypy pro `TestCallBack` a `TestCallBack2` metody.</span><span class="sxs-lookup"><span data-stu-id="be053-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="be053-113">Obě metody předání delegáta zpětného volání funkce jako parametr.</span><span class="sxs-lookup"><span data-stu-id="be053-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="be053-114">Podpis delegáta, musí odpovídat podpis metody, na které odkazuje.</span><span class="sxs-lookup"><span data-stu-id="be053-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="be053-115">Například `FPtr` a `FPtr2` delegáti mít podpisy, které jsou stejné jako `DoSomething` a `DoSomething2` metody.</span><span class="sxs-lookup"><span data-stu-id="be053-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="be053-116">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="be053-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="be053-117">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="be053-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="be053-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="be053-118">See Also</span></span>  
 [<span data-ttu-id="be053-119">Různé zařazování ukázky</span><span class="sxs-lookup"><span data-stu-id="be053-119">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [<span data-ttu-id="be053-120">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="be053-120">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="be053-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="be053-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
