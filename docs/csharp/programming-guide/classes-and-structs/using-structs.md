---
title: Používání struktur – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: d85b11204eb1f1de3a95efc67054cdffc4c219e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714666"
---
# <a name="using-structs-c-programming-guide"></a>Používání struktur (C# Průvodce programováním)

`struct` typ je vhodný pro reprezentaci lehkých objektů, jako jsou `Point`, `Rectangle`a `Color`. I když je to tak pohodlné, aby představovala bod jako [třídu](../../language-reference/keywords/class.md) s [automaticky implementovanými vlastnostmi](./auto-implemented-properties.md), [Struktura](../../language-reference/keywords/struct.md) může být v některých scénářích efektivnější. Například pokud deklarujete pole 1000 `Point` objektů, přidělíte další paměť pro odkazování na jednotlivé objekty; v takovém případě by struktura byla levnější. Protože rozhraní .NET již obsahuje objekt s názvem <xref:System.Drawing.Point>, struktura v tomto příkladu je pojmenována `Coords` místo toho.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Pro definování konstruktoru bez parametrů pro strukturu se jedná o chybu. Je také chyba při inicializaci pole instance v těle struktury. Členy struktury s externě přístupnými lze inicializovat pouze pomocí parametrizovaného konstruktoru, implicitního konstruktoru bez parametrů, [inicializátoru objektu](object-and-collection-initializers.md)nebo přístupem k členům jednotlivě po deklaraci struktury. Všichni privátní nebo jinak nepřístupní členové vyžadují použití konstruktorů výhradně.

Když vytvoříte objekt struktury pomocí operátoru [New](../../language-reference/operators/new-operator.md) , vytvoří se a příslušný konstruktor se zavolá podle [signatury konstruktoru](constructors.md#constructor-syntax). Na rozdíl od tříd lze vytvořit instanci struktur bez použití operátoru `new`. V takovém případě neexistuje žádné volání konstruktoru, což zajistí efektivnější přidělení. Pole však zůstanou Nepřiřazeno a objekt nelze použít, dokud nebudou všechna pole inicializována. To zahrnuje neschopnost získat nebo nastavit hodnoty prostřednictvím vlastností.

Pokud vytváříte instanci objektu struct pomocí konstruktoru bez parametrů, jsou všichni členové přiřazeni podle jejich [výchozích hodnot](../../language-reference/keywords/default-values-table.md).

Při psaní konstruktoru s parametry pro strukturu musíte explicitně inicializovat všechny členy; jinak jeden nebo více členů zůstává Nepřiřazeno a strukturu nelze použít, což vyprodukuje chybu kompilátoru [CS0171](../../misc/cs0171.md).

Pro struktury neexistuje žádná dědičnost, protože pro třídy existují třídy. Struktura nemůže dědit z jiné struktury nebo třídy a nemůže být základem třídy. Struktury však dědí ze základní třídy <xref:System.Object>. Struktura může implementovat rozhraní a funguje stejně jako třídy.

Třídu nelze deklarovat pomocí klíčového slova `struct`. V C#, třídy a struktury jsou sémanticky odlišné. Struktura je hodnotový typ, zatímco třída je odkazový typ. Další informace naleznete v tématu [typy hodnot](../../language-reference/keywords/value-types.md) a [typy odkazů](../../language-reference/keywords/reference-types.md).

Pokud nepotřebujete sémantiku typu reference, malá třída může být efektivnějším způsobem zpracována systémem, pokud ji deklarujete jako strukturu.

## <a name="example-1"></a>Příklad 1

Tento příklad ukazuje `struct` inicializaci pomocí parametrů bez parametrů a parametrizovaných konstruktorů.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>Příklad 2

Tento příklad ukazuje funkci, která je jedinečná pro struktury. Vytvoří objekt CoOrds bez použití operátoru `new`. Pokud nahradíte slovo `struct` slovem `class`, program nebude zkompilován.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](index.md)
- [Struktury](structs.md)
