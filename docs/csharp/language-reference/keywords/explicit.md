---
title: Explicit – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027938"
---
# <a name="explicit-c-reference"></a>explicit (Referenční dokumentace jazyka C#)

`explicit` – Klíčové slovo deklaruje operátor převodu uživatelem definovaný typ, který musí být volána s přetypování. Tento operátor například převede ze třídy s názvem Fahrenheita na třídu s názvem c:

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

Tento operátor převodu nelze vyvolat takto:

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

Operátor převodu převede ze zdroje typu na typ cíle. Typ zdroje poskytuje operátor převodu. Na rozdíl od implicitní převod musí být volána operátory explicitního převodu prostřednictvím přetypování. Pokud operaci převodu může způsobit, že výjimky nebo dojít ke ztrátě informací, byste měli označit `explicit`. Kompilátor zabrání bezobslužně vyvolání operaci převodu s pravděpodobně nepředpokládaného důsledky.

Vynechání přetypování výsledky v chybě kompilace CS0266.

Další informace najdete v tématu [použití operátorů převodu](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="example"></a>Příklad

Následující příklad uvádí `Fahrenheit` a `Celsius` třída, z nichž každý obsahuje operátor explicitní převod na jinou třídu.

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a>Příklad

V následujícím příkladu definuje struktury, `Digit`, která představuje jednu desítková číslice. Operátor je definována pro převody z `byte` k `Digit`, ale protože ne všechny bajtů můžete převést na `Digit`, je explicitní převod.

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../index.md)  
[Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
[Klíčová slova jazyka C#](index.md)  
[implicit](implicit.md)  
[operátor (referenční dokumentace jazyka C#)](operator.md)  
[Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[Zřetězené uživatelem definované explicitní převody v jazyce C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  