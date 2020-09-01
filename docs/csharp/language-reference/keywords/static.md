---
description: static – modifikátor – reference jazyka C#
title: static – modifikátor – reference jazyka C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f42636d1bbdf4342297f46f50ec6dfc2a70eacad
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142060"
---
# <a name="static-c-reference"></a>static – modifikátor (Referenční dokumentace jazyka C#)

Tato stránka obsahuje `static` klíčové slovo modifikátoru. `static`Klíčové slovo je také součástí [`using static`](using-static.md) direktivy.

Použijte `static` Modifikátor k deklaraci statického člena, který patří do samotného typu, nikoli na konkrétní objekt. `static`Modifikátor lze použít k deklaraci `static` tříd. V třídách, rozhraních a strukturách můžete přidat `static` modifikátor pro pole, metody, vlastnosti, operátory, události a konstruktory. `static`Modifikátor nelze použít s indexery nebo finalizační metody. Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example---static-class"></a>Příklad – statická třída

Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklarace konstanty nebo typu je implicitně `static` členem. Na `static` člena se nedá odkazovat prostřednictvím instance. Místo toho je odkazováno pomocí názvu typu. Zvažte například následující třídu:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Chcete-li odkazovat na `static` člena `x` , použijte plně kvalifikovaný název, `MyBaseC.MyStruct.x` Pokud je člen přístupný ze stejného oboru:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

I když instance třídy obsahuje samostatnou kopii všech polí instance třídy, je k dispozici pouze jedna kopie každého `static` pole.

Není možné použít [`this`](this.md) k odkazování `static` metod nebo přístupových objektů vlastností.

Pokud `static` je klíčové slovo použito pro třídu, musí být všichni členové třídy `static` .

Třídy, rozhraní a `static` třídy mohou mít `static` konstruktory. `static`Konstruktor je volán v určitém bodě mezi okamžikem spuštění programu a instancí třídy.

> [!NOTE]
> `static`Klíčové slovo má více omezeného použití než v jazyce C++. Pro porovnání s klíčovým slovem jazyka C++, viz [třídy úložiště (C++)](/cpp/cpp/storage-classes-cpp#static).

Chcete-li předvést `static` členy, zvažte třídu, která představuje zaměstnance společnosti. Předpokládat, že třída obsahuje metodu pro počítání zaměstnanců a pole pro uložení počtu zaměstnanců. Jak metoda, tak pole nepatří do žádné z těchto instancí zaměstnanců. Místo toho patří do třídy zaměstnanci jako celek. Měly by být deklarovány jako `static` členy třídy.

## <a name="example---static-field-and-method"></a>Příklad – statické pole a metoda

Tento příklad přečte jméno a ID nového zaměstnance, zvýší čítač zaměstnanců o jednu a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců. Tento program přečte aktuální počet zaměstnanců z klávesnice.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Příklad – Statická inicializace

Tento příklad ukazuje, že můžete inicializovat `static` pole pomocí jiného `static` pole, které ještě není deklarované. Výsledky budou nedefinovány, dokud explicitně nepřiřadíte hodnotu k `static` poli.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [použití statické direktivy](using-static.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
