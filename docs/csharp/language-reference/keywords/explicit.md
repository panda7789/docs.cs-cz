---
title: "explicit (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eab79d3ac48192f3c176ed44685ab58e50fc89be
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="explicit-c-reference"></a>explicit (Referenční dokumentace jazyka C#)
`explicit` – Klíčové slovo deklaruje operátor převodu uživatelem definovaný typ, který musí být volána s přetypování. Tento operátor například převede ze třídy s názvem Fahrenheita na třídu s názvem c:  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 Tento operátor převodu nelze vyvolat takto:  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 Operátor převodu převede ze zdroje typu na typ cíle. Typ zdroje poskytuje operátor převodu. Na rozdíl od implicitní převod musí být volána operátory explicitního převodu prostřednictvím přetypování. Pokud operaci převodu může způsobit, že výjimky nebo dojít ke ztrátě informací, byste měli označit `explicit`. Kompilátor zabrání bezobslužně vyvolání operaci převodu s pravděpodobně nepředpokládaného důsledky.  
  
 Vynechání přetypování výsledky v chybě kompilace CS0266.  
  
 Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí `Fahrenheit` a `Celsius` třída, z nichž každý obsahuje operátor explicitní převod na jinou třídu.  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje struktury, `Digit`, která představuje jednu desítková číslice. Operátor je definována pro převody z `byte` k `Digit`, ale protože ne všechny bajtů můžete převést na `Digit`, je explicitní převod.  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [implicitní](../../../csharp/language-reference/keywords/implicit.md)  
 [operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Postupy: implementace uživatelem definovaných převodů mezi strukturami](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Zřetězené uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
