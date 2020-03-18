---
title: const klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713681"
---
# <a name="const-c-reference"></a>const (Referenční dokumentace jazyka C#)

`const` Klíčové slovo slouží k deklarování konstantní pole nebo konstantní místní. Konstantní pole a místní jsou proměnné a nemusí být změněny. Konstantami mohou být čísla, logické hodnoty, řetězce nebo nulový odkaz. Nevytvářejte konstantu představující informace, které očekáváte, že kdykoli změníte. Nepoužívejte například konstantní pole k uložení ceny služby, čísla verze produktu nebo názvu značky společnosti. Tyto hodnoty se mohou v průběhu času měnit a protože kompilátory šíří konstanty, další kód zkompilovaný s knihovnami bude muset být znovu zkompilován, aby se zobcházely změny. Viz také klíčové slovo [jen pro čtení.](./readonly.md) Například:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Poznámky

Typ konstantní deklarace určuje typ členů, které deklarace zavádí. Inicializátor konstantní místní nebo konstantní pole musí být konstantní výraz, který lze implicitně převést na cílový typ.

Konstantní výraz je výraz, který lze plně vyhodnotit v době kompilace. Proto pouze možné hodnoty pro konstanty `string` typy odkazů jsou a null odkaz.

Konstantní deklarace může deklarovat více konstant, například:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

Modifikátor `static` není povolen v konstantní deklaraci.

Konstanta se může účastnit konstantního výrazu takto:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> Klíčové slovo [jen pro](./readonly.md) `const` čtení se liší od klíčového slova. Pole `const` lze inicializovat pouze při deklaraci tohoto pole. Pole `readonly` lze inicializovat buď v deklaraci, nebo v konstruktoru. `readonly` Pole proto mohou mít různé hodnoty v závislosti na použitém konstruktoru. I když `const` je pole konstantou v `readonly` době kompilace, lze toto pole použít pro konstanty za běhu, jako v tomto řádku:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak používat konstanty jako místní proměnné.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Modifikátory](index.md)
- [Readonly](./readonly.md)
