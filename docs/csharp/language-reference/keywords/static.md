---
title: statický modifikátor – C# referenční informace
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744658"
---
# <a name="static-c-reference"></a>static – modifikátor (Referenční dokumentace jazyka C#)

Použijte modifikátor `static` k deklaraci statického člena, který patří do samotného typu, nikoli na konkrétní objekt. Modifikátor `static` lze použít k deklarování `static` tříd. V třídách, rozhraních a strukturách můžete přidat modifikátor `static` do polí, metod, vlastností, operátorů, událostí a konstruktorů. Modifikátor `static` nelze použít s indexery nebo finalizační metody. Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Příklad

Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklarace konstanty nebo typu je implicitně `static` člen. Na člena `static` nelze odkazovat prostřednictvím instance. Místo toho je odkazováno pomocí názvu typu. Zvažte například následující třídu:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Chcete-li odkazovat na `static` členský `x`, použijte plně kvalifikovaný název `MyBaseC.MyStruct.x`, pokud je člen přístupný ze stejného rozsahu:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

I když instance třídy obsahuje samostatnou kopii všech polí instance třídy, je k dispozici pouze jedna kopie každého pole `static`.

Není možné použít [`this`](this.md) k odkazování na `static` metod nebo přístupových objektů vlastností.

Pokud je klíčové slovo `static` použito pro třídu, musí být všichni členové třídy `static`.

Třídy, rozhraní a `static` třídy mohou mít `static` konstruktory. `static` konstruktor je volán v určitém bodě mezi okamžikem spuštění programu a instancí třídy.

> [!NOTE]
> Klíčové slovo `static` má více omezeného použití než C++v. Pro porovnání s C++ klíčovým slovem, viz [třídyC++úložiště ()](/cpp/cpp/storage-classes-cpp#static).

K předvedení `static`ch členů zvažte třídu, která představuje zaměstnance společnosti. Předpokládat, že třída obsahuje metodu pro počítání zaměstnanců a pole pro uložení počtu zaměstnanců. Jak metoda, tak pole nepatří do žádné z těchto instancí zaměstnanců. Místo toho patří do třídy zaměstnanci jako celek. Měly by být deklarovány jako `static` členy třídy.

## <a name="example"></a>Příklad

Tento příklad přečte jméno a ID nového zaměstnance, zvýší čítač zaměstnanců o jednu a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců. Tento program přečte aktuální počet zaměstnanců z klávesnice.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Příklad

Tento příklad ukazuje, že můžete inicializovat pole `static` pomocí jiného pole `static`, které ještě není deklarované. Výsledky nebudou definovány, dokud explicitně nepřiřadíte hodnotu poli `static`.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [C#Odkaz](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
