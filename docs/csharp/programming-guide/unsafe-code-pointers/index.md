---
title: Nezabezpečený kód a ukazatele (Průvodce programováním v C#)
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
ms.openlocfilehash: b57a6f607dbdbc84c60889a5ce2b1e3c33d7f435
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331601"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Nezabezpečený kód a ukazatele (Průvodce programováním v C#)
Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetika ukazatele ve výchozím nastavení. Avšak pomocí [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat kontextu unsafe, ve které je možné ukazatele. Další informace o ukazatele, naleznete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  V common language runtime (CLR) nezabezpečený kód se označuje jako neověřitelný kód. Nezabezpečený kód v jazyce C# není nutně nebezpečné; je pouze kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR. Modul CLR bude proto pouze spouštění nezabezpečený kód Pokud je ve plně důvěryhodné sestavení. Pokud používáte nezabezpečený kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo chyby ukazatele.  
  
## <a name="unsafe-code-overview"></a>Přehled nebezpečného kódu  
 Nezabezpečený kód má následující vlastnosti:  
  
-   Metody, typy a bloky kódu je možné definovat jako bezpečné.  
  
-   V některých případech může nezabezpečený kód zvýšit výkon aplikace odebráním kontroly meze pole.  
  
-   Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.  
  
-   Nezabezpečený kód představuje riziko zabezpečení a stability.  
  
-   V pořadí pro jazyk C# zkompilovat nezabezpečený kód, aplikace musí být zkompilovány s [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
-   [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Vyrovnávací paměti pevné velikosti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Postupy: použití ukazatelů ke kopírování pole bajtů](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
