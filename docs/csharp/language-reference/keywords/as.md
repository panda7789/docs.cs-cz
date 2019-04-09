---
title: jako - C# odkaz
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: b87e75bd4866a191e84465e44d53850e6e2e9723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169920"
---
# <a name="as-c-reference"></a>as (Referenční dokumentace jazyka C#)
Můžete použít `as` operátor pro provádění určitých typů převody mezi typy kompatibilní odkazů nebo [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md). Následující kód ukazuje příklad.  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

Jak ukazuje příklad, potřebujete porovnat výsledek `as` výraz s `null` ke kontrole, pokud je úspěšný převod. Od verze C# 7.0, můžete použít [je](is.md) výraz pro testování, převod bude úspěšné a podmíněně přidělit proměnné v případě, že převod je úspěšný. V mnoha případech je stručnější než při použití `as` operátor. Další informace najdete v tématu [vzor typu](is.md#type) část [ `is` operátor](is.md) článku.
  
## <a name="remarks"></a>Poznámky  
 `as` Operátor je jako operace přetypování. Nicméně, pokud převod není možný, `as` vrátí `null` namísto vyvolání výjimky. Vezměte v úvahu v následujícím příkladu:  
  
```csharp  
expression as type  
```  
  
 Je ekvivalentem následujícího výrazu s výjimkou, že kód `expression` proměnná je vyhodnocen pouze jednou.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Všimněte si, `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a převody zabalení. `as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by místo toho provádět pomocí výrazy přetypování.  
  
## <a name="example"></a>Příklad  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [operátor as](~/_csharplang/spec/expressions.md#the-as-operator) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
 
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [?: Operátor](../../../csharp/language-reference/operators/conditional-operator.md)
- [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)
