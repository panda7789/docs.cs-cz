---
title: Pojmy a terminologie (funkční transformace) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 3e2ecc4c2f70700ae92ee36b6f122059b922332e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70040631"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Pojmy a terminologie (funkční transformace) (C#)

Toto téma představuje pojmy a terminologii čistě funkčních transformací. Přístup k transformaci transformace dat dává kód, který je často rychlejší programovat, výraznější a snadněji ladit a udržovat než tradiční, imperativní programování.

Všimněte si, že témata v této části nejsou určeny k plně vysvětlit funkční programování. Místo toho tato témata identifikují některé funkce funkčního programování, které usnadňují transformaci XML z jednoho obrazce do druhého.

## <a name="what-is-pure-functional-transformation"></a>Co je čistá funkční transformace?

V *čistě funkční transformaci*definuje sada funkcí nazývaná čisté *funkce*způsob transformace sady strukturovaných dat z původní podoby do jiné podoby. Slovo "čistý" označuje, že funkce jsou *kompozitelné*, což vyžaduje, aby byly:

- *Samostatné*, takže mohou být volně uspořádány a uspořádány bez zapletení nebo vzájemné závislosti se zbytkem programu. Čisté transformace nemají žádné znalosti nebo vliv na jejich životní prostředí. To znamená, že funkce použité v transformaci nemají žádné *vedlejší účinky*.

- *Bezstavový*, tak, aby provádění stejné funkce nebo konkrétní sadu funkcí na stejném vstupu bude vždy mít za následek stejný výstup. Čisté transformace nemají paměť na jejich předchozí použití.

> [!IMPORTANT]
> Ve zbytku tohoto kurzu termín "čistá funkce" se používá v obecném smyslu k označení programovací přístup a není konkrétní jazyk funkce.
>
> Všimněte si, že čisté funkce musí být implementovány jako metody v c#.
>
> Také byste neměli zaměňovat čisté funkce s čistě virtuální metody v jazyce C++. Ten označuje, že obsahující třída je abstraktní a že je zadáno žádné tělo metody.

### <a name="functional-programming"></a>Funkční programování

*Funkční programování* je programovací přístup, který přímo podporuje čistě funkční transformaci.

V minulosti byly univerzální funkční programovací jazyky, jako jsou ML, Scheme, Haskell a F#, primárně zajímavé pro akademickou komunitu. Ačkoli to bylo vždy možné psát čistě funkční transformace v C#, obtížnost přitom není z něj atraktivní volbou pro většinu programátorů. V posledních verzích jazyka C# však nové jazykové konstrukce, jako jsou výrazy lambda a odvození typu, usnadňují a ines udělují funkcionaličtější programování.

Další informace o funkčním programování naleznete v [tématu Funkční programování vs. imperativní programování (C#)](./functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Jazyky FP specifické pro doménu

Ačkoli obecné funkční programovací jazyky nebyly široce přijaty, specifické funkční programovací jazyky specifické pro danou doménu měly větší úspěch. Například kaskádové šablony stylů (CSS) se používají k určení vzhledu a chování mnoha webových stránek a šablony stylů Xml (Extensible Stylesheet Language Transformations) (XSLT) se používají ve velké míře při manipulaci s daty XML. Další informace o XSLT naleznete v tématu [Transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologie

Následující tabulka definuje některé termíny související s funkční transformace.

funkce vyššího řádu (první třída) \
Funkce, která může být považována za programový objekt. Například funkce vyššího řádu může být předána nebo vrácena z jiných funkcí. V jazyce C#c jsou delegáti a výrazy lambda funkce jazyka, které podporují funkce vyššího řádu. Chcete-li napsat funkci vyššího řádu, deklarujete jeden nebo více argumentů pro převzetí delegátů a při volání často používáte výrazy lambda. Mnoho standardních operátorů dotazů jsou funkce vyššího řádu.

Další informace naleznete [v tématu Přehled operátorů standardních dotazů (C#)](./standard-query-operators-overview.md).

lambda výraz \
V podstatě inline anonymní funkce, která lze použít všude tam, kde je očekáván typ delegáta. Toto je zjednodušená definice lambda výrazy, ale je vhodné pro účely tohoto kurzu.

Další informace naleznete v tématu [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).

kolekce \
Strukturovaná sada dat, obvykle jednotného typu. Chcete-li být kompatibilní s LINQ, <xref:System.Collections.IEnumerable> kolekce <xref:System.Linq.IQueryable> musí implementovat rozhraní nebo <xref:System.Collections.Generic.IEnumerator%601> rozhraní <xref:System.Linq.IQueryable%601>(nebo jeden z jejich obecných protějšků, nebo ).

řazené kolekce členů (anonymní typy) \
Matematický koncept, n-tice je konečná posloupnost objektů, každý z určitého typu. Řazená kolekce členů se také označuje jako seřazený seznam. Anonymní typy jsou implementace jazyka tohoto konceptu, které umožňují deklarovat nepojmenovaný typ třídy a současně vytvořit instanci objektu tohoto typu.

Další informace naleznete [v tématu Anonymní typy](../../classes-and-structs/anonymous-types.md).

odvození typu (implicitní psaní) \
Schopnost kompilátoru určit typ proměnné v nepřítomnosti deklarace explicitního typu.

Další informace naleznete [v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).

odložené provedení a opožděné vyhodnocení \
Zpoždění vyhodnocení výrazu, dokud jeho vyřešená hodnota je skutečně požadováno. Odložené spuštění je podporováno v kolekcích.

Další informace naleznete [v tématu Úvod do LINQ dotazy (C#)](./introduction-to-linq-queries.md) a [odložené spuštění a opožděné vyhodnocení v LINQ na XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Tyto jazykové funkce budou použity v ukázkách kódu v této části.

## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. imperativní programování (C#)](./functional-programming-vs-imperative-programming.md)
