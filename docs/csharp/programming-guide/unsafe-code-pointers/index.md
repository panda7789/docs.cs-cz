---
title: Nezabezpečený kód a ukazatele C# – Průvodce programováním
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711828"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Nezabezpečený kód a ukazateleC# (Průvodce programováním)

Aby se zachovala bezpečnost typů a C# zabezpečení, ve výchozím nastavení nepodporuje aritmetický ukazatel. Pomocí klíčového slova [unsafe](../../language-reference/keywords/unsafe.md) můžete však definovat nezabezpečený kontext, ve kterém mohou být ukazatele použity. Další informace o ukazatelích naleznete v tématu [typy ukazatelů](pointer-types.md).  
  
> [!NOTE]
> V modulu CLR (Common Language Runtime) se nezabezpečený kód označuje jako neověřitelný kód. Nezabezpečený C# kód v nástroji není nutně nebezpečný; je to pouze kód, jehož bezpečnost nemůže být ověřena modulem CLR. Modul CLR proto spustí pouze nezabezpečený kód, pokud je v plně důvěryhodném sestavení. Pokud používáte nezabezpečený kód, je vaše zodpovědnost za to, že váš kód nezavádí bezpečnostní rizika nebo chyby ukazatelů.  
  
## <a name="unsafe-code-overview"></a>Přehled nebezpečného kódu

Nezabezpečený kód má následující vlastnosti:

- Metody, typy a bloky kódu lze definovat jako nebezpečné.

- V některých případech může nezabezpečený kód zvýšit výkon aplikace odebráním kontrol hranic pole.

- Nezabezpečený kód je vyžadován při volání nativních funkcí, které vyžadují ukazatele.

- Použití nebezpečného kódu zavádí rizika zabezpečení a stability.

- Kód, který obsahuje nebezpečné bloky, musí být zkompilován s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.
  
## <a name="related-sections"></a>Související oddíly

Další informace najdete v části .

- [Typy ukazatelů](pointer-types.md)

- [Vyrovnávací paměti pevné velikosti](fixed-size-buffers.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v tématu věnovaném [nebezpečnému kódu](~/_csharplang/spec/unsafe-code.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
