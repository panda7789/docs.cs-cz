---
title: statický modifikátor - C# Reference
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102057"
---
# <a name="static-c-reference"></a>static – modifikátor (Referenční dokumentace jazyka C#)

Tato stránka `static` se zabývá klíčovým slovem modifikátoru. Klíčové `static` slovo je také [`using static`](using-static.md) součástí směrnice.

`static` Modifikátor použijte k deklarování statického člena, který patří k samotnému typu, nikoli k určitému objektu. Modifikátor `static` lze deklarovat `static` třídy. Ve třídách, rozhraních a strukturách můžete `static` přidat modifikátor do polí, metod, vlastností, operátorů, událostí a konstruktorů. Modifikátor `static` nelze použít s indexery nebo finalizačními metodami. Další informace naleznete [v tématu Statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example---static-class"></a>Příklad - statická třída

Následující třída je `static` deklarována jako a obsahuje pouze `static` metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklarace konstanty nebo typu `static` je implicitně členem. Na `static` člena nelze odkazovat prostřednictvím instance. Místo toho je odkazováno prostřednictvím názvu typu. Zvažte například následující třídu:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Chcete-li `static` odkazovat na člen `x`, `MyBaseC.MyStruct.x`použijte plně kvalifikovaný název , , pokud člen není přístupný ze stejného oboru:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Zatímco instance třídy obsahuje samostatnou kopii všech polí instance třídy, je `static` pouze jedna kopie každého pole.

Není možné použít [`this`](this.md) k referenční `static` metody nebo přístupové objekty vlastností.

Pokud `static` je klíčové slovo použito pro třídu, musí `static`být všichni členové třídy .

Třídy, rozhraní `static` a třídy mohou mít `static` konstruktory. Konstruktor `static` je volána v určitém okamžiku mezi spuštěním programu a instance třídy.

> [!NOTE]
> Klíčové `static` slovo má omezenější použití než v jazyce C++. Chcete-li porovnat s c++ klíčové slovo, viz [Storage třídy (C++)](/cpp/cpp/storage-classes-cpp#static).

Chcete-li demonstrovat `static` členy, zvažte třídu, která představuje zaměstnance společnosti. Předpokládejme, že třída obsahuje metodu počítání zaměstnanců a pole pro uložení počtu zaměstnanců. Metoda i pole nepatří do žádné instance zaměstnance. Místo toho patří do třídy zaměstnanců jako celku. Měly by `static` být deklarovány jako členové třídy.

## <a name="example---static-field-and-method"></a>Příklad - statické pole a metoda

Tento příklad přečte jméno a ID nového zaměstnance, zintáží čítač zaměstnance o jeden a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců. Tento program čte aktuální počet zaměstnanců z klávesnice.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Příklad - statická inicializace

Tento příklad ukazuje, že můžete `static` inicializovat pole pomocí jiného `static` pole, které ještě není deklarováno. Výsledky nebudou definovány, dokud explicitně nepřiřadíte hodnotu `static` poli.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory](index.md)
- [použití statické direktivy](using-static.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
