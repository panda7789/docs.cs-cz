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
ms.openlocfilehash: 0e2289b3c12c7c83a39f1ad8d5a1365349ca6442
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151799"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Zařazování delegáta jako metody zpětného volání
Tato ukázka předvádí, jak předat delegáty nespravované funkci očekávající ukazatele na funkce. Delegát je třída, která může obsahovat odkaz na metodu a je ekvivalentní k ukazateli funkce bezpečnému pro typ nebo funkci zpětného volání.

> [!NOTE]
> Použijete-li delegáta uvnitř volání, modul CLR (Common Language Runtime) chrání delegáta před uvolněním paměti po dobu trvání tohoto volání. Nicméně pokud nespravované funkce uloží delegáta pro použití po dokončení volání, je nutné ručně zabránit uvolňování paměti, dokud neskončí nespravovanou funkci s delegátem. Další informace najdete v ukázce [HandleRef – Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) a [GCHandle](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).

Ukázka zpětného volání používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:

- `TestCallBack`exportováno z knihovny pinvokelib. dll.

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- `TestCallBack2`exportováno z knihovny pinvokelib. dll.

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci pro dříve uvedené funkce.

V této ukázce `NativeMethods` třída obsahuje spravované prototypy `TestCallBack` pro metody a `TestCallBack2` . Obě metody předají delegátovi funkce zpětného volání jako parametr. Signatura delegáta musí odpovídat podpisu metody, na kterou odkazuje. Například `FPtr` Delegáti a `FPtr2` mají signatury `DoSomething` , které jsou stejné jako metody a `DoSomething2` .

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
