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
ms.openlocfilehash: 145e6b8891735c904aa98a36ccfd27958bdf788d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648609"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="06753-102">Zařazování delegáta jako metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="06753-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="06753-103">Tato ukázka předvádí, jak předat delegáti nespravovaná funkce očekává ukazatele na funkce.</span><span class="sxs-lookup"><span data-stu-id="06753-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="06753-104">Delegát je třída, která může obsahovat odkaz na metodu a je ekvivalentní ukazatele na funkci zajišťující bezpečnost typů nebo zpětného volání funkce.</span><span class="sxs-lookup"><span data-stu-id="06753-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
>  <span data-ttu-id="06753-105">Při použití delegáta uvnitř volání, modul common language runtime chrání delegáta je uvolněna z paměti po dobu trvání tohoto volání.</span><span class="sxs-lookup"><span data-stu-id="06753-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="06753-106">Nicméně pokud nespravovaná funkce ukládá delegáta pro použití po dokončení volání, je nutné ručně zabránit uvolňování paměti až do dokončení nespravovanou funkci s delegátem.</span><span class="sxs-lookup"><span data-stu-id="06753-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="06753-107">Další informace najdete v tématu [handleref – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) a [GCHandle – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="06753-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="06753-108">Ukázka zpětného volání používá následující nespravované funkce zobrazené s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="06753-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="06753-109">`TestCallBack` exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="06753-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="06753-110">`TestCallBack2` exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="06753-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="06753-111">[Knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí.</span><span class="sxs-lookup"><span data-stu-id="06753-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="06753-112">V této ukázce `LibWrap` třída obsahuje spravované prototypy pro `TestCallBack` a `TestCallBack2` metody.</span><span class="sxs-lookup"><span data-stu-id="06753-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="06753-113">Obě metody předat jako parametr delegáta funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="06753-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="06753-114">Signatura delegáta musí odpovídat signatuře metody, na které odkazuje.</span><span class="sxs-lookup"><span data-stu-id="06753-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="06753-115">Například `FPtr` a `FPtr2` delegáty mají podpisy, které jsou stejné jako `DoSomething` a `DoSomething2` metody.</span><span class="sxs-lookup"><span data-stu-id="06753-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="06753-116">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="06753-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="06753-117">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="06753-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="06753-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06753-118">See also</span></span>

- <span data-ttu-id="06753-119">[Různé ukázky zařazování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06753-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="06753-120">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="06753-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="06753-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="06753-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
