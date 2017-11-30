---
title: "stackalloc (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referenční dokumentace jazyka C#)
`stackalloc` – Klíčové slovo se používá v kontextu nezabezpečený kód přidělit blok paměti v zásobníku.  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo je platný jenom v místní proměnné inicializátory. Následující kód způsobí, že chyby kompilátoru.  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 Protože se jedná o typy ukazatelů `stackalloc` vyžaduje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu. Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc`je třeba [_alloca –](/cpp/c-runtime-library/reference/alloca) v běhové knihovny jazyka C.  
  
 Následující příklad vypočítá a zobrazuje prvních 20 čísla v pořadí Fibonacciho. Všechna čísla je součet hodnot předchozích dvou čísel. V kódu bloku paměti dostatečná velikost tak, aby obsahovala 20 elementy typu `int` je přidělená v zásobníku, není haldě. Adresu bloku je uložen v ukazatele `fib`. Tuto paměť nevztahují uvolňování paměti a proto nemusí být připnutý (pomocí [pevné](../../../csharp/language-reference/keywords/fixed-statement.md)). Životnost bloku paměti je omezeno na dobu životnosti metody, která ho definuje. Nelze uvolnit paměť, než metoda vrátí.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>Zabezpečení  
 Nezabezpečený kód je méně bezpečné než bezpečné alternativy. Ale použití `stackalloc` automaticky povolí funkce zjišťování přetečení vyrovnávací paměti v common language runtime (CLR). Pokud je zjištěn přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat riziko, že se spustí škodlivý kód ukončení procesu.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
