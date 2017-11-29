---
title: "unsafe (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords: unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fffbe36e39d279b2364b178188381a403c8ff86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-reference"></a>unsafe (Referenční dokumentace jazyka C#)
`unsafe` – Klíčové slovo označuje unsafe kontext, který je požadován pro všechny operace zahrnutí ukazatelů. Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 Můžete použít `unsafe` modifikátor v deklaraci typu nebo člena. Textové celý rozsah typ nebo člen za nebezpečné kontextu. Například následující je metoda deklarovat s `unsafe` modifikátor:  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Rozsah kontext unsafe rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze také použít v seznamu parametrů:  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 Nezabezpečený bloku můžete taky povolit používání nezabezpečený kód v tomto bloku. Příklad:  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Nezabezpečený kód zkompilovat, je nutné zadat [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru. Nezabezpečený kód není zkontrolovat, že modul common language runtime.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Vyrovnávací paměti pevné velikosti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
