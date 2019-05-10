---
title: Nezabezpečený kód a ukazatele – C# Průvodce programováním
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
ms.openlocfilehash: 9f4e74e1e8fa71d1492a10162191822c1edfb635
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608042"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Nezabezpečený kód a ukazatele (Průvodce programováním v C#)
Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetiku ukazatele ve výchozím nastavení. Nicméně pomocí [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat nezabezpečený kontext, ve které je možné ukazatele. Další informace o ukazatelích naleznete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  V modulu common language runtime (CLR) nebezpečný kód se označuje jako neověřitelný kód. Nezabezpečený kód v jazyce C# není nutně nebezpečné; je jenom kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR. Modul CLR proto pouze spustí nezabezpečený kód by byl v plně důvěryhodná sestavení. Pokud používáte nebezpečný kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo ukazatel chyby.  
  
## <a name="unsafe-code-overview"></a>Přehled nebezpečného kódu  
 Nezabezpečený kód má následující vlastnosti:  
  
- Metody, typy a bloků kódu může být definován jako bezpečné.  
  
- V některých případech může nezabezpečený kód zvýšit výkon vaší aplikace tak, že odeberete kontroly hranice pole.  
  
- Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.  
  
- Použití nezabezpečeného kódu představuje rizika zabezpečení a stabilitu.  
  
- V pořadí pro jazyk C# ke kompilaci nezabezpečený kód aplikace musí být kompilována s [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [Vyrovnávací paměti pevné velikosti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [Postupy: Použití ukazatelů ke kopírování pole bajtů](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
