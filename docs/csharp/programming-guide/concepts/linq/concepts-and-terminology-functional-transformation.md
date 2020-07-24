---
title: Koncepty a terminologie (transformace funkcí) (C#)
description: Funkce funkčního programování usnadňují transformaci XML. Přečtěte si o konceptech a terminologii čistě funkčních transformací v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: ee972b376f0d0898b7681049b9641b43780ed353
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103982"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Koncepty a terminologie (transformace funkcí) (C#)

V tomto tématu se seznámíte s koncepty a terminologií čistě funkčních transformací. Přístup k funkcím transformace pro transformaci dat poskytuje kód, který je často rychlejší pro program, větší vyjádření a jednodušší ladění a udržování než tradiční, imperativní programování.

Všimněte si, že témata v této části nejsou určena k úplnému vysvětlení funkčního programování. Místo toho tato témata identifikují některé funkce funkčního programování, které usnadňují transformaci XML z jednoho tvaru na druhý.

## <a name="what-is-pure-functional-transformation"></a>Co je čistě funkční transformace?

V *čistě funkční transformaci*sada funkcí s názvem *Pure Functions*definují, jak transformovat sadu strukturovaných dat z původního formuláře do jiného formuláře. Slovo "Pure" označuje, že funkce jsou *sestavitelované*, což vyžaduje:

- *Samostatně obsažený*, aby bylo možné je volně seřadit a uspořádat bez entanglement nebo vzájemné závislosti se zbytkem programu. Čisté transformace nemají na svém prostředí žádné znalosti ani neplatí. To znamená, že funkce použité v transformaci nemají žádné *vedlejší účinky*.

- *Bez stavu*, takže spuštění stejné funkce nebo konkrétní sady funkcí na stejném vstupu bude mít vždycky stejný výstup. Čisté transformace nemají žádnou paměť jejich předchozího použití.

> [!IMPORTANT]
> Ve zbývající části tohoto kurzu se výraz "čistá funkce" používá v obecném smyslu k označení přístup k programování a nikoli konkrétní funkce jazyka.
>
> Všimněte si, že čisté funkce musí být implementovány jako metody v jazyce C#.
>
> Nepleťte si také čistě virtuální funkce s čistě virtuálními metodami v jazyce C++. Druhá označuje, že obsahující třídu je abstraktní a není dodána žádná část metody.

### <a name="functional-programming"></a>Funkční programování

*Funkční programování* je programovací přístup, který přímo podporuje čistě funkční transformaci.

Historické programovací jazyky pro obecné účely, jako je ML, schéma, Haskell a F #, byly primárně důležité pro akademickou komunitu. I když je v jazyce C# vždycky možné zapisovat čistě funkční transformace, obtížnost by se tak neudělala zajímavou možností pro většinu programátorů. V posledních verzích C#, ale nové jazykové konstrukce, jako jsou výrazy lambda a odvození typu, umožňují, aby funkční programování bylo mnohem jednodušší a produktivnější.

Další informace o funkčním programování naleznete v tématu [funkční programování vs. imperativní programování (C#)](./functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Jazyky FP specifické pro doménu

I když se všeobecně nepřijaly obecné funkční programovací jazyky, měly by lepší úspěšnost konkrétních programovacích jazyků specifických pro doménu. Například šablony stylů CSS (CSS) se používají k určení vzhledu a chování mnoha webových stránek a šablony stylů XSLT (Extensible Stylesheet Language Transformations) se v manipulaci s daty XML používají rozsáhle. Další informace o XSLT naleznete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologie

Následující tabulka definuje některé z podmínek souvisejících s funkcemi transformace.

funkce vyššího řádu (první třídy) \
Funkce, která může být považována za programový objekt. Například funkce vyššího pořadí může být předána nebo vrácena z jiných funkcí. V jazyce C # c jsou delegáti a výrazy lambda podporovány jazykové funkce, které podporují funkce vyššího řádu. Chcete-li napsat funkci s vyšším pořadím, deklarujete jeden nebo více argumentů pro převzetí delegátů a často používáte lambda výrazy při volání. Mnoho standardních operátorů dotazu je funkce vyššího řádu.

Další informace najdete v tématu [Přehled standardních operátorů dotazu (C#)](./standard-query-operators-overview.md).

výraz lambda \
V podstatě vložená anonymní funkce, kterou lze použít všude, kde se očekává typ delegáta. Toto je zjednodušená definice výrazů lambda, ale je vhodná pro účely tohoto kurzu.

Další informace o naleznete v tématu [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).

kolekce
Strukturovaná sada dat, obvykle s jednotným typem. Aby bylo možné kompatibilitu s LINQ, kolekce musí implementovat <xref:System.Collections.IEnumerable> rozhraní nebo <xref:System.Linq.IQueryable> rozhraní (nebo jeden z jeho obecných protějšků <xref:System.Collections.Generic.IEnumerator%601> nebo <xref:System.Linq.IQueryable%601> ).

řazená kolekce členů (anonymní typy) \
Matematický koncept, řazená kolekce členů je konečná sekvence objektů, z nichž každý konkrétní typ. Řazená kolekce členů je také známá jako uspořádaný seznam. Anonymní typy jsou implementací jazyka tohoto konceptu, která umožňuje deklaraci nepojmenovaného typu třídy a vytváření instancí objektu daného typu ve stejnou dobu.

Další informace najdete v tématu [anonymní typy](../../classes-and-structs/anonymous-types.md).

odvození typu (implicitní zadání) \
Schopnost kompilátoru určit typ proměnné v absence explicitní deklarace typu.

Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).

odložené provádění a opožděné vyhodnocení \
Zpoždění vyhodnocení výrazu, dokud není skutečně vyžadováno jeho vyřešená hodnota. Odložené provádění je v kolekcích podporováno.

Další informace naleznete v tématu [Úvod do dotazů LINQ (C#)](./introduction-to-linq-queries.md) a [odložené provádění a opožděné vyhodnocení v LINQ to XML (c#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Tyto jazykové funkce budou použity v ukázkách kódu v této části.

## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. imperativní programování (C#)](./functional-programming-vs-imperative-programming.md)
