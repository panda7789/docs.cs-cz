---
description: Private – klíčové slovo – Reference jazyka C#
title: Private – klíčové slovo – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139395"
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)

`private`Klíčové slovo je modifikátor přístupu ke členu.

> Tato stránka se zabývá `private` přístupem. `private`Klíčové slovo je také součástí [`private protected`](./private-protected.md) modifikátoru přístupu.

Privátní přístup je nejnižší úroveň přístupu. Soukromé členy jsou přístupné pouze v těle třídy nebo struktury, ve které jsou deklarovány, jako v tomto příkladu:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

K těmto soukromým členům mohou přistupovat i vnořené typy ve stejném těle.

Jedná se o chybu při kompilaci, která odkazuje na soukromého člena mimo třídu nebo strukturu, ve které je deklarována.

Porovnání `private` s dalšími modifikátory přístupu najdete v tématu [úrovně přístupnosti](accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Příklad

V tomto příkladu `Employee` Třída obsahuje dva soukromé datové členy `name` a `salary` . Jako soukromé členy nejsou k dispozici, s výjimkou metod členů. Veřejné metody s názvem `GetName` a `Salary` jsou přidány, aby umožnily řízený přístup soukromým členům. K `name` členu se dá získat přístup prostřednictvím veřejné metody a k zobrazení `salary` člena se dostanete pomocí veřejné vlastnosti jen pro čtení. (Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md) .)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)
