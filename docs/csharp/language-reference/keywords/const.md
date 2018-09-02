---
title: Const – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: f586b6d097a8592fd74e92df7886b519d623e478
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393002"
---
# <a name="const-c-reference"></a>const (Referenční dokumentace jazyka C#)

Můžete použít `const` – klíčové slovo k deklaraci konstanty pole nebo místního prostředí konstanty. Konstantní pole a místní hodnoty nejsou proměnné a nejde ho upravit. Konstanty mohou obsahovat čísla, logické hodnoty, řetězce nebo odkaz s hodnotou null. Nevytvářejte konstantu ke znázornění informací, které můžete kdykoli změnit. Například nepoužívejte pole konstanty pro uložení ceny služby, číslo verze produktu nebo název značky společnosti. Tyto hodnoty můžou časem změnit. a protože kompilátory šířit konstanty, jiný kód zkompilovaný s vaší knihovny bude mít třeba znovu zkompilovat, aby se změny projevily. Viz také [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo. Příklad:

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a>Poznámky

Typ deklarace konstanty Určuje typ členů, které deklarace zavádí. Inicializátor místní konstanty nebo pole konstanty musí být konstantní výraz, který lze implicitně převést na typ cíle.

Konstantní výraz je výraz, který může být plně vyhodnocen v době kompilace. Proto jediné možné hodnoty pro konstanty odkazových typů jsou `string` a odkaz s hodnotou null.

Deklarace konstanty může deklarovat více konstant, jako například:

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

`static` Modifikátor není povolen v deklarace konstanty.

Konstanta můžete zúčastnit konstantního výrazu, následujícím způsobem:

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> [Jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo se liší od `const` – klíčové slovo. A `const` pole mohou být inicializovány pouze v deklaraci pole. A `readonly` pole mohou být inicializovány při deklaraci nebo v konstruktoru. Proto `readonly` pole může mít různé hodnoty v závislosti na použitém konstruktoru. Také i když `const` pole je konstantu kompilace `readonly` pole můžete použít pro konstanty z doby běhu, jako v tomto řádku: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít konstanty jako lokální proměnné.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
- [readonly](../../../csharp/language-reference/keywords/readonly.md)
