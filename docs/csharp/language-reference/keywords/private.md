---
title: soukromé klíčové slovo C# – reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602010"
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)

`private` Klíčové slovo je modifikátor přístupu ke členu.

> Tato stránka se `private` zabývá přístupem. Klíčové slovo je také součástí [`private protected`](./private-protected.md) modifikátoru přístupu. `private`

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

Porovnání `private` s dalšími modifikátory přístupu najdete v tématu [úrovně](accessibility-levels.md) přístupnosti a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Příklad

V tomto příkladu `Employee` třída obsahuje dva soukromé datové `name` členy a `salary`. Jako soukromé členy nejsou k dispozici, s výjimkou metod členů. Veřejné metody s `GetName` názvem `Salary` a jsou přidány, aby umožnily řízený přístup soukromým členům. K členu se dá získat přístup prostřednictvím veřejné metody `salary` a k zobrazení člena se dostanete pomocí veřejné vlastnosti jen pro čtení. `name` (Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md) .)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarované](~/_csharplang/spec/basic-concepts.md#declared-accessibility) přístupnosti ve [ C# specifikaci jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)
