---
title: Nebezpečný kód a ukazatele – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711828"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Nebezpečný kód a ukazatele (Průvodce programováním jazyka C#)

Chcete-li zachovat zabezpečení typu, C# nepodporuje aritmetické ukazatele, ve výchozím nastavení. Pomocí [nebezpečného](../../language-reference/keywords/unsafe.md) klíčového slova však můžete definovat nebezpečný kontext, ve kterém lze použít ukazatele. Další informace o ukazatelích naleznete v tématu [Pointer types](pointer-types.md).  
  
> [!NOTE]
> V clr (common language runtime) se nebezpečný kód označuje jako neověřitelný kód. Nebezpečný kód v c# není nutně nebezpečné; je to jen kód, jehož bezpečnost nelze ověřit CLR. CLR proto spustí pouze nebezpečný kód, pokud je v plně důvěryhodném sestavení. Pokud používáte nebezpečný kód, je vaší odpovědností zajistit, aby váš kód nezaváděl bezpečnostní rizika nebo chyby ukazatele.  
  
## <a name="unsafe-code-overview"></a>Přehled nebezpečných kódů

Nebezpečný kód má následující vlastnosti:

- Metody, typy a bloky kódu lze definovat jako nebezpečné.

- V některých případech může nebezpečný kód zvýšit výkon aplikace odebráním kontroly hranice pole.

- Nebezpečný kód je vyžadován při volání nativních funkcí, které vyžadují ukazatele.

- Použití nebezpečného kódu představuje bezpečnostní a stabilizační rizika.

- Kód, který obsahuje nebezpečné bloky, musí být zkompilován s možností [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátoru.
  
## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [Typy ukazatelů](pointer-types.md)

- [Vyrovnávací paměti pevné velikosti](fixed-size-buffers.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v tématu [nebezpečný kód](~/_csharplang/spec/unsafe-code.md) specifikace [jazyka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
