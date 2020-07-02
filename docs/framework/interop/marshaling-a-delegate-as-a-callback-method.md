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
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Zařazování delegáta jako metody zpětného volání
Tato ukázka předvádí, jak předat delegáty nespravované funkci očekávající ukazatele na funkce. Delegát je třída, která může obsahovat odkaz na metodu a je ekvivalentní k ukazateli funkce bezpečnému pro typ nebo funkci zpětného volání.

> [!NOTE]
> Použijete-li delegáta uvnitř volání, modul CLR (Common Language Runtime) chrání delegáta před uvolněním paměti po dobu trvání tohoto volání. Nicméně pokud nespravované funkce uloží delegáta pro použití po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud neskončí nespravovanou funkci s delegátem. Další informace najdete v ukázce [HandleRef – Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) a [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).

Ukázka zpětného volání používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:

- `TestCallBack`exportováno z PinvokeLib.dll.

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- `TestCallBack2`exportováno z PinvokeLib.dll.

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci pro dříve uvedené funkce.

V této ukázce `NativeMethods` Třída obsahuje spravované prototypy pro `TestCallBack` `TestCallBack2` metody a. Obě metody předají delegátovi funkce zpětného volání jako parametr. Signatura delegáta musí odpovídat podpisu metody, na kterou odkazuje. Například `FPtr` `FPtr2` Delegáti a mají signatury, které jsou stejné jako `DoSomething` metody a `DoSomething2` .

## <a name="declaring-prototypes"></a>Deklarace prototypů
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a>Volání funkcí
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a>Viz také:

- [Různé vzorky zařazování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
- [Datové typy vyvolání platformy](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md)
