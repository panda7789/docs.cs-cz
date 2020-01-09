---
title: statický modifikátor – C# referenční informace
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f4ca3fcf809e723d2144654f1da949eb4d6de1b4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713063"
---
# <a name="static-c-reference"></a>static – modifikátor (Referenční dokumentace jazyka C#)

Použijte modifikátor `static` k deklaraci statického člena, který patří do samotného typu, nikoli na konkrétní objekt. Modifikátor `static` lze použít s třídami, poli, metodami, vlastnostmi, operátory, událostmi a konstruktory, ale nelze jej použít s indexery, finalizačními metodami nebo jinými typy než třídy. Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Příklad

Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklarace konstanty nebo typu je implicitně statickým členem.

Na statický člen se nedá odkazovat prostřednictvím instance. Místo toho je odkazováno prostřednictvím názvu typu. Zvažte například následující třídu:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Chcete-li odkazovat na statický členský `x`, použijte plně kvalifikovaný název, `MyBaseC.MyStruct.x`, pokud je člen přístupný ze stejného rozsahu:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

I když instance třídy obsahuje samostatnou kopii všech polí instance třídy, je k dispozici pouze jedna kopie každého statického pole.

[Tuto](this.md) možnost nelze použít pro odkazování statických metod nebo přístupových objektů vlastností.

Pokud je klíčové slovo `static` použito pro třídu, všechny členy třídy musí být statické.

Třídy a statické třídy mohou mít statické konstruktory. Statické konstruktory jsou volány v určitém bodě mezi okamžikem spuštění programu a instance třídy.

> [!NOTE]
> Klíčové slovo `static` má více omezeného použití než C++v. Pro porovnání s C++ klíčovým slovem, viz [třídyC++úložiště ()](/cpp/cpp/storage-classes-cpp#static).

Chcete-li předvést statické členy, zvažte třídu, která představuje zaměstnance společnosti. Předpokládat, že třída obsahuje metodu pro počítání zaměstnanců a pole pro uložení počtu zaměstnanců. Jak metoda, tak pole nepatří žádnému zaměstnanci instance. Místo toho patří do třídy Company. Proto by měly být deklarovány jako statické členy třídy.

## <a name="example"></a>Příklad

Tento příklad přečte jméno a ID nového zaměstnance, zvýší čítač zaměstnanců o jednu a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců. Pro zjednodušení tento program přečte aktuální počet zaměstnanců z klávesnice. V reálné aplikaci by měly být tyto informace čteny ze souboru.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Příklad

Tento příklad ukazuje, že i když můžete inicializovat statické pole pomocí jiného statického pole, které dosud nebylo deklarováno, výsledky budou nedefinovány, dokud explicitně nepřiřadíte hodnotu do statického pole.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
