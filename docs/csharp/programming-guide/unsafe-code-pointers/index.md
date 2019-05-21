---
title: Nezabezpečený kód a ukazatele – C# Průvodce programováním pro službu
ms.custom: seodec18
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
ms.openlocfilehash: 99f0b925a37bff8b6ab1ff46e9ce2f0ea0a38aed
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959478"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Nezabezpečený kód a ukazatele (C# Programming Guide)

Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetiku ukazatele ve výchozím nastavení. Nicméně pomocí [nebezpečné](../../language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat nezabezpečený kontext, ve které je možné ukazatele. Další informace o ukazatelích naleznete v tématu [typy ukazatelů](pointer-types.md).  
  
> [!NOTE]
> V modulu common language runtime (CLR) nebezpečný kód se označuje jako neověřitelný kód. Nezabezpečený kód v jazyce C# není nutně nebezpečné; je jenom kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR. Modul CLR proto pouze spustí nezabezpečený kód by byl v plně důvěryhodná sestavení. Pokud používáte nebezpečný kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo ukazatel chyby.  
  
## <a name="unsafe-code-overview"></a>Přehled nebezpečného kódu

Nezabezpečený kód má následující vlastnosti:

- Metody, typy a bloků kódu může být definován jako bezpečné.

- V některých případech může nezabezpečený kód zvýšit výkon vaší aplikace tak, že odeberete kontroly hranice pole.

- Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.

- Použití nezabezpečeného kódu představuje rizika zabezpečení a stabilitu.

- Kód, který obsahuje nebezpečné bloky musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.
  
## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [Typy ukazatelů](pointer-types.md)

- [Vyrovnávací paměti pevné velikosti](fixed-size-buffers.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) téma [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
