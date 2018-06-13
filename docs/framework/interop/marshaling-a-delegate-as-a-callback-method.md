---
title: Zařazování delegáta jako metody zpětného volání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff875f2807a14493ab81a9e354b5c4dcdf3d5feb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389379"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="30f36-102">Zařazování delegáta jako metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="30f36-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="30f36-103">Tento příklad znázorňuje, jak předat delegáti nespravované funkce byl očekáván ukazatelů na funkce.</span><span class="sxs-lookup"><span data-stu-id="30f36-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="30f36-104">Delegát je třída, která může pojmout odkazu na třídu metodě a je ekvivalentní ukazatel na funkci zajišťující bezpečnost typů nebo funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="30f36-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30f36-105">Při použití delegáta uvnitř volání modul common language runtime chrání delegát nebudou uvolnění z paměti po dobu trvání tohoto volání.</span><span class="sxs-lookup"><span data-stu-id="30f36-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="30f36-106">Ale pokud nespravované funkce ukládá delegát používat po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud nebude dokončeno nespravované funkce s delegátem.</span><span class="sxs-lookup"><span data-stu-id="30f36-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="30f36-107">Další informace najdete v tématu [HandleRef ukázka](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) a [GCHandle ukázka](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="30f36-107">For more information, see the [HandleRef Sample](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) and [GCHandle Sample](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).</span></span>  
  
 <span data-ttu-id="30f36-108">Zpětné volání – Ukázka používá následující nespravované funkce s jejich původní deklarace funkce:</span><span class="sxs-lookup"><span data-stu-id="30f36-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="30f36-109">**TestCallBack** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="30f36-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="30f36-110">**TestCallBack2** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="30f36-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="30f36-111">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementaci výše uvedených funkcí.</span><span class="sxs-lookup"><span data-stu-id="30f36-111">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="30f36-112">V této ukázce `LibWrap` třída obsahuje spravovaných prototypy pro `TestCallBack` a `TestCallBack2` metody.</span><span class="sxs-lookup"><span data-stu-id="30f36-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="30f36-113">Obě metody předání delegáta zpětného volání funkce jako parametr.</span><span class="sxs-lookup"><span data-stu-id="30f36-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="30f36-114">Podpis delegáta, musí odpovídat podpis metody, na které odkazuje.</span><span class="sxs-lookup"><span data-stu-id="30f36-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="30f36-115">Například `FPtr` a `FPtr2` delegáti mít podpisy, které jsou stejné jako `DoSomething` a `DoSomething2` metody.</span><span class="sxs-lookup"><span data-stu-id="30f36-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="30f36-116">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="30f36-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="30f36-117">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="30f36-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="30f36-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="30f36-118">See Also</span></span>  
 <span data-ttu-id="30f36-119">[Různé zařazování ukázky](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30f36-119">[Miscellaneous Marshaling Samples](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))</span></span>  
 <span data-ttu-id="30f36-120">[Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30f36-120">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="30f36-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="30f36-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
