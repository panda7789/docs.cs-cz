---
title: Nezabezpečený kód a ukazatele – Průvodce programováním v C#
Description: Seznamte se s nebezpečným kódem a ukazateli. Jazyk C# nepodporuje ukazatele, ale můžete definovat nezabezpečený kontext, ve kterém mohou být ukazatele použity s klíčovým slovem unsafe.
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
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381772"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Nezabezpečený kód a ukazatele (Průvodce programováním v C#)

Aby bylo možné zachovat bezpečnost typů a zabezpečení, C# ve výchozím nastavení nepodporuje aritmetické operace s ukazatelem. Pomocí klíčového slova [unsafe](../../language-reference/keywords/unsafe.md) můžete však definovat nezabezpečený kontext, ve kterém mohou být ukazatele použity. Další informace o ukazatelích naleznete v tématu [typy ukazatelů](pointer-types.md).  
  
> [!NOTE]
> V modulu CLR (Common Language Runtime) se nezabezpečený kód označuje jako neověřitelný kód. Nezabezpečený kód v jazyce C# není nutně nebezpečný; je to pouze kód, jehož bezpečnost nemůže být ověřena modulem CLR. Modul CLR proto spustí pouze nezabezpečený kód, pokud je v plně důvěryhodném sestavení. Pokud používáte nezabezpečený kód, je vaše zodpovědnost za to, že váš kód nezavádí bezpečnostní rizika nebo chyby ukazatelů.  
  
## <a name="unsafe-code-overview"></a>Přehled nebezpečného kódu

Nezabezpečený kód má následující vlastnosti:

- Metody, typy a bloky kódu lze definovat jako nebezpečné.

- V některých případech může nezabezpečený kód zvýšit výkon aplikace odebráním kontrol hranic pole.

- Nezabezpečený kód je vyžadován při volání nativních funkcí, které vyžadují ukazatele.

- Použití nebezpečného kódu zavádí rizika zabezpečení a stability.

- Kód, který obsahuje nebezpečné bloky, musí být zkompilován s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.
  
## <a name="related-sections"></a>Související oddíly

Další informace naleznete v tématu:

- [Typy ukazatelů](pointer-types.md)

- [Vyrovnávací paměti pevné velikosti](fixed-size-buffers.md)

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v tématu [nezabezpečeného kódu](~/_csharplang/spec/unsafe-code.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [UNSAFE](../../language-reference/keywords/unsafe.md)
