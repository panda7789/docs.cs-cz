---
title: Private – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a817f3f60b76b51868c5cacd8e648ec10497f64a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130998"
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)

`private` – Klíčové slovo je modifikátor přístupu členu.

> Tato stránka popisuje `private` přístup. `private` – Klíčové slovo je také součástí [ `private protected` ](./private-protected.md) modifikátor přístupu.

Soukromý přístup je omezenou úroveň přístupu. Privátní členy jsou přístupné jenom v rámci třídy nebo struktury, ve kterém jsou deklarovány, jako v následujícím příkladu:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Vnořené typy ve stejné tělo se dostanete také tyto soukromé členy.

Je chyba kompilace tak, aby odkazovaly soukromý člen mimo třídy nebo struktury, ve kterém je deklarována.

Porovnání `private` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Příklad

V tomto příkladu `Employee` třída obsahuje dva soukromé datové členy `name` a `salary`. Jako soukromé členy k nim nelze přistupovat s výjimkou metody člena. Veřejné metody s názvem `GetName` a `Salary` přidávají povolit řízený přístup k soukromým členům. `name` Člen přistupuje prostřednictvím veřejnou metodu a `salary` člen přistupuje prostřednictvím veřejné vlastnosti jen pro čtení. (Viz [vlastnosti](../../programming-guide/classes-and-structs/properties.md) Další informace.)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)