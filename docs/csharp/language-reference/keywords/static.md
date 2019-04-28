---
title: statický modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 90b043fa13f1737db81518151daaeceabf930c5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660681"
---
# <a name="static-c-reference"></a>static – modifikátor (Referenční dokumentace jazyka C#)

Použití `static` modifikátor deklarovat statický člen, který patří do samotného typu, nikoli s určitým objektem. `static` Modifikátor lze použít s třídami, pole, metody, vlastnosti, operátory, události a konstruktory, ale nelze použít s indexery, finalizační metody nebo jiné typy než třídy. Další informace najdete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Příklad

Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklarace konstanty nebo typu je implicitně statický člen.

Statický člen se nedá odkazovat prostřednictvím instance. Místo toho se odkazuje pomocí názvu typu. Představte si třeba následující třídy:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Odkazovat na statického člena `x`, použijte plně kvalifikovaný název `MyBaseC.MyStruct.x`, pokud člen není přístupný ze stejného oboru:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Zatímco instance třídy obsahuje kopii všechna pole instancí třídy, je jenom jednu kopii každého statické pole.

Není možné použít [to](this.md) odkazovat statické metody nebo přistupující objekty vlastnosti.

Pokud `static` – klíčové slovo je aplikován na třídu, musí být statické členy třídy.

Statické třídy a třídy mohou mít statické konstruktory. Statické konstruktory jsou volány v určitém okamžiku mezi při spuštění programu a je vytvořena instance třídy.

> [!NOTE]
> `static` – Klíčové slovo má omezenější použití než v jazyce C++. Porovnat s klíčovým slovem C++, naleznete v tématu [třídy úložiště (C++)](/cpp/cpp/storage-classes-cpp#static).

Abychom si předvedli statické členy, vezměte v úvahu třídu, která představuje zaměstnance společnosti. Předpokládejme, že třída obsahuje metody pro počet zaměstnanců a pole pro uložení tohoto čísla zaměstnanců. Metody a pole nepatří do jakékoli instance zaměstnance. Místo toho patří do třídy společnosti. Proto by měly být deklarovány jako statické členy třídy.

## <a name="example"></a>Příklad

Tento příklad načte název a ID nového zaměstnance, zvýší čítač zaměstnance jednou a zobrazí informace o nových zaměstnanců a nový počet zaměstnanců. Pro zjednodušení tento program přečte aktuální počet zaměstnanců z klávesnice. V reálné aplikaci by měli číst tyto informace ze souboru.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Příklad

Tento příklad ukazuje, že i když inicializujete statické pole pomocí jiné statické pole ještě nebyla deklarována, budou výsledky nedefinované dokud explicitně přiřadit hodnotu statické pole.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](modifiers.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)