---
title: soukromé klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715199"
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)

Klíčové `private` slovo je modifikátor přístupu člena.

> Tato stránka `private` se týká přístupu. Klíčové `private` slovo je také [`private protected`](./private-protected.md) součástí modifikátoru přístupu.

Soukromý přístup je nejméně tolerantní úroveň přístupu. Soukromé členy jsou přístupné pouze v rámci těla třídy nebo struktury, ve kterém jsou deklarovány, jako v tomto příkladu:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Vnořené typy ve stejném těle mohou také přistupovat k těmto soukromým členům.

Jedná se o chybu v době kompilace odkazovat na soukromý člen mimo třídu nebo strukturu, ve které je deklarován.

Porovnání s `private` ostatními modifikátory přístupu naleznete v [tématu Úrovně přístupnosti](accessibility-levels.md) a [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Příklad

V tomto příkladu `Employee` třída obsahuje dva `name` `salary`soukromé datové členy a . Jako soukromé členy, nemohou být přístupné s výjimkou členské metody. Veřejné metody `GetName` `Salary` s názvem a jsou přidány povolit řízený přístup k soukromým členům. Člen `name` je přístupný prostřednictvím veřejné metody a `salary` člen je přístupný prostřednictvím veřejné vlastnosti jen pro čtení. (Další informace naleznete v tématu [Vlastnosti.)](../../programming-guide/classes-and-structs/properties.md)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specifikace jazyka C#  

For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [Veřejné](public.md)
- [protected](protected.md)
- [Vnitřní](internal.md)
