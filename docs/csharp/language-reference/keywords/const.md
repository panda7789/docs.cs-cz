---
title: const – C# klíčové slovo – Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 81660e6a56efe5737600122d4ff7e182654f9a9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422896"
---
# <a name="const-c-reference"></a>const (Referenční dokumentace jazyka C#)

Použijete klíčové slovo `const` k deklaraci konstantního pole nebo konstanty místní. Konstantní pole a místní hodnoty nejsou proměnné a nelze je upravovat. Konstanty můžou být čísla, logické hodnoty, řetězce nebo odkazy s hodnotou null. Nevytvářejte konstantu, která bude představovat informace, které byste měli kdykoli změnit. Například nepoužívejte pole konstanty k uložení ceny služby, čísla verze produktu nebo značky společnosti. Tyto hodnoty se mohou v průběhu času měnit a vzhledem k tomu, že kompilátory šíří konstanty, je nutné znovu zkompilovat další kód kompilovaný s vašimi knihovnami, aby se změny projevily. Viz také klíčové slovo [ReadOnly](./readonly.md) . Příklad:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Poznámky

Typ deklarace konstanty určuje typ členů, které deklarace zavádí. Inicializátor konstantního místního nebo konstantního pole musí být konstantní výraz, který lze implicitně převést na cílový typ.

Konstantní výraz je výraz, který lze plně vyhodnotit v době kompilace. Proto jediné možné hodnoty pro konstanty odkazových typů jsou `string` a odkaz s hodnotou null.

Deklarace konstanty může deklarovat více konstant, například:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

Modifikátor `static` není v deklaraci konstanty povolen.

Konstanta se může účastnit konstantního výrazu, a to následujícím způsobem:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> Klíčové slovo [ReadOnly](./readonly.md) se liší od klíčového slova `const`. Pole `const` lze inicializovat pouze v deklaraci pole. Pole `readonly` lze inicializovat buď v deklaraci, nebo v konstruktoru. Proto `readonly` pole mohou mít různé hodnoty v závislosti na použitém konstruktoru. I když `const` pole je konstanta při kompilaci, pole `readonly` lze použít pro konstanty run-time, jako v tomto řádku: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít konstanty jako lokální proměnné.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Modifikátory](index.md)
- [readonly](./readonly.md)
