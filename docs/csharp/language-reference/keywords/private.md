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
ms.openlocfilehash: 19e2925cd65cc9c68ff50d370398a4f401275940
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422595"
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)

Klíčové slovo `private` je modifikátor přístupu ke členu.

> Tato stránka pokrývá přístup `private`. Klíčové slovo `private` je také součástí modifikátoru přístupu [`private protected`](./private-protected.md) .

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

V tomto příkladu třída `Employee` obsahuje dva soukromé datové členy `name` a `salary`. Jako soukromé členy nejsou k dispozici, s výjimkou metod členů. Jsou přidány veřejné metody s názvem `GetName` a `Salary`, které umožňují řízený přístup k soukromým členům. K `name`mu členu se dá získat přístup prostřednictvím veřejné metody a k `salary`mu členu se dá získat přístup prostřednictvím veřejné vlastnosti jen pro čtení. (Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md) .)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarované přístupnosti](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)
