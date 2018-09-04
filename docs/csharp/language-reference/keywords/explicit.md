---
title: Explicit – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 3567a2c5aa549aa3141ed59c3e93e7b07975da70
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525458"
---
# <a name="explicit-c-reference"></a>explicit (Referenční dokumentace jazyka C#)

`explicit` – Klíčové slovo deklaruje uživatelem definovaného typu operátoru převodu, který je nutné volat s přetypování.

Následující příklad definuje operátor, který převede z `Fahrenheit` třídu `Celsius` třídy. Operátor musí být definovány uvnitř `Fahrenheit` třídy nebo `Celsius` třídy:

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

Vyvolání definovaný převod operátorem přetypování, jak ukazuje následující příklad:

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

Operátor převodu převede zdrojový typ na typ cíle. Zdrojový typ obsahuje operátor převodu. Na rozdíl od implicitních převodů je nutné explicitní operátory převodu volat pomocí přetypování. Pokud operaci převodu může způsobit výjimky nebo dojít ke ztrátě informací, byste měli označit `explicit`. To zabrání tomu, aby kompilátor tiše vyvolání operace převodu s může být nepředvídatelné následky.

Vynechání výsledkem přetypování CS0266 chybu v době kompilace.

Další informace najdete v tématu [použití operátorů převodu](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="example"></a>Příklad

Následující příklad uvádí `Fahrenheit` a `Celsius` tříd, z nichž každý obsahuje explicitní operátor převodu na třídu.

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a>Příklad

V následujícím příkladu definuje strukturu, `Digit`, představující jednomístné číslo. Operátor je definována pro převod z `byte` k `Digit`, ale protože ne všechny bajty mohou být převedeny do `Digit`, je explicitní převod.

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [implicit](implicit.md)  
- [– Operátor (referenční dokumentace jazyka C#)](operator.md)  
- [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
- [Zřetězit uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  
