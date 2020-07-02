---
title: Zařazování delegáta jako metody zpětného volání
description: Naučte se zařadit delegáta jako metodu zpětného volání. Podívejte se na příklad, jak předat delegáty nespravované funkci, která očekává ukazatele na funkci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: bf9ef3b9d48c0869dcc96820c3a2fb6fb608479e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618945"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="36d29-104">Zařazování delegáta jako metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="36d29-104">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="36d29-105">Tato ukázka předvádí, jak předat delegáty nespravované funkci očekávající ukazatele na funkce.</span><span class="sxs-lookup"><span data-stu-id="36d29-105">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="36d29-106">Delegát je třída, která může obsahovat odkaz na metodu a je ekvivalentní k ukazateli funkce bezpečnému pro typ nebo funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="36d29-106">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="36d29-107">Použijete-li delegáta uvnitř volání, modul CLR (Common Language Runtime) chrání delegáta před uvolněním paměti po dobu trvání tohoto volání.</span><span class="sxs-lookup"><span data-stu-id="36d29-107">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="36d29-108">Nicméně pokud nespravované funkce uloží delegáta pro použití po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud neskončí nespravovanou funkci s delegátem.</span><span class="sxs-lookup"><span data-stu-id="36d29-108">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="36d29-109">Další informace najdete v ukázce [HandleRef – Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) a [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="36d29-109">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="36d29-110">Ukázka zpětného volání používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="36d29-110">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="36d29-111">`TestCallBack`exportováno z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="36d29-111">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="36d29-112">`TestCallBack2`exportováno z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="36d29-112">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="36d29-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci pro dříve uvedené funkce.</span><span class="sxs-lookup"><span data-stu-id="36d29-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="36d29-114">V této ukázce `NativeMethods` Třída obsahuje spravované prototypy pro `TestCallBack` `TestCallBack2` metody a.</span><span class="sxs-lookup"><span data-stu-id="36d29-114">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="36d29-115">Obě metody předají delegátovi funkce zpětného volání jako parametr.</span><span class="sxs-lookup"><span data-stu-id="36d29-115">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="36d29-116">Signatura delegáta musí odpovídat podpisu metody, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="36d29-116">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="36d29-117">Například `FPtr` `FPtr2` Delegáti a mají signatury, které jsou stejné jako `DoSomething` metody a `DoSomething2` .</span><span class="sxs-lookup"><span data-stu-id="36d29-117">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="36d29-118">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="36d29-118">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="36d29-119">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="36d29-119">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="36d29-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36d29-120">See also</span></span>

- <span data-ttu-id="36d29-121">[Různé vzorky zařazování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="36d29-121">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="36d29-122">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="36d29-122">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="36d29-123">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="36d29-123">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
