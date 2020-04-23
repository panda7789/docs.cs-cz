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
ms.openlocfilehash: c71c89e5797745144a2baed2d4846e3d9f9f26be
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114016"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="c58fd-102">Zařazování delegáta jako metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="c58fd-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="c58fd-103">Tato ukázka předvádí, jak předat delegáty nespravované funkci očekávající ukazatele na funkce.</span><span class="sxs-lookup"><span data-stu-id="c58fd-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="c58fd-104">Delegát je třída, která může obsahovat odkaz na metodu a je ekvivalentní k ukazateli funkce bezpečnému pro typ nebo funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c58fd-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="c58fd-105">Použijete-li delegáta uvnitř volání, modul CLR (Common Language Runtime) chrání delegáta před uvolněním paměti po dobu trvání tohoto volání.</span><span class="sxs-lookup"><span data-stu-id="c58fd-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="c58fd-106">Nicméně pokud nespravované funkce uloží delegáta pro použití po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud neskončí nespravovanou funkci s delegátem.</span><span class="sxs-lookup"><span data-stu-id="c58fd-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="c58fd-107">Další informace najdete v ukázce [HandleRef – Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) a [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c58fd-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="c58fd-108">Ukázka zpětného volání používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="c58fd-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="c58fd-109">`TestCallBack`exportováno z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="c58fd-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="c58fd-110">`TestCallBack2`exportováno z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="c58fd-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="c58fd-111">[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci pro dříve uvedené funkce.</span><span class="sxs-lookup"><span data-stu-id="c58fd-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="c58fd-112">V této ukázce `NativeMethods` třída obsahuje spravované prototypy pro metody `TestCallBack` a. `TestCallBack2`</span><span class="sxs-lookup"><span data-stu-id="c58fd-112">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="c58fd-113">Obě metody předají delegátovi funkce zpětného volání jako parametr.</span><span class="sxs-lookup"><span data-stu-id="c58fd-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="c58fd-114">Signatura delegáta musí odpovídat podpisu metody, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="c58fd-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="c58fd-115">Například delegáti `FPtr` a `FPtr2` mají signatury, které jsou stejné jako metody `DoSomething` a `DoSomething2` .</span><span class="sxs-lookup"><span data-stu-id="c58fd-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="c58fd-116">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="c58fd-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="c58fd-117">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="c58fd-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="c58fd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c58fd-118">See also</span></span>

- <span data-ttu-id="c58fd-119">[Různé vzorky zařazování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c58fd-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="c58fd-120">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="c58fd-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="c58fd-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="c58fd-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
