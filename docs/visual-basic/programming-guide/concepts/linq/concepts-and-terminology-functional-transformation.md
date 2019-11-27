---
title: Koncepty a terminologie (funkční transformace)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: efc1fc5bb738e3d5d9d3fa2a8226c37da69c045c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345697"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Koncepty a terminologie (funkce Transformation) (Visual Basic)
V tomto tématu se seznámíte s koncepty a terminologií čistě funkčních transformací. Přístup k funkcím transformace pro transformaci dat poskytuje kód, který je často rychlejší pro program, větší vyjádření a jednodušší ladění a udržování než tradiční, imperativní programování.

Všimněte si, že témata v této části nejsou určena k úplnému vysvětlení funkčního programování. Místo toho tato témata identifikují některé funkce funkčního programování, které usnadňují transformaci XML z jednoho tvaru na druhý.

## <a name="what-is-pure-functional-transformation"></a>Co je čistě funkční transformace?

V *čistě funkční transformaci*sada funkcí s názvem *Pure Functions*definují, jak transformovat sadu strukturovaných dat z původního formuláře do jiného formuláře. Slovo "Pure" označuje, že funkce jsou *sestavitelované*, což vyžaduje:

- *Samostatně obsažený*, aby bylo možné je volně seřadit a uspořádat bez entanglement nebo vzájemné závislosti se zbytkem programu. Čisté transformace nemají na svém prostředí žádné znalosti ani neplatí. To znamená, že funkce použité v transformaci nemají žádné *vedlejší účinky*.

- *Bez stavu*, takže spuštění stejné funkce nebo konkrétní sady funkcí na stejném vstupu bude mít vždycky stejný výstup. Čisté transformace nemají žádnou paměť jejich předchozího použití.

> [!IMPORTANT]
> Ve zbývající části tohoto kurzu se výraz "čistá funkce" používá v obecném smyslu k označení přístup k programování a nikoli konkrétní funkce jazyka.
>
> Všimněte si, že funkce Pure musí být implementována jako funkce v Visual Basic.
>
> Nepleťte si také čistě virtuální funkce s čistě virtuálními metodami v C++nástroji. Druhá označuje, že obsahující třídu je abstraktní a není dodána žádná část metody.

### <a name="functional-programming"></a>Funkční programování

*Funkční programování* je programovací přístup, který přímo podporuje čistě funkční transformaci.

Historické programovací jazyky pro obecné účely, jako je ML, schéma, Haskell a F#, byly primárně důležité pro akademickou komunitu. I když je vždycky možné zapsat čistě funkční transformace v Visual Basic, tak obtížnost by neudělala atraktivní možnost většiny programátorů. V novějších verzích Visual Basic však nové jazykové konstrukce, jako jsou výrazy lambda a odvození typu, umožňují programování mnohem jednodušší a produktivnější.

Další informace o funkčním programování naleznete v tématu [funkční programování vs. imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Jazyky FP specifické pro doménu

I když se všeobecně nepřijaly obecné funkční programovací jazyky, měly by lepší úspěšnost konkrétních programovacích jazyků specifických pro doménu. Například šablony stylů CSS (CSS) se používají k určení vzhledu a chování mnoha webových stránek a šablony stylů XSLT (Extensible Stylesheet Language Transformations) se v manipulaci s daty XML používají rozsáhle. Další informace o XSLT naleznete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologie

Následující tabulka definuje některé z podmínek souvisejících s funkcemi transformace.

funkce vyššího řádu (první třídy) \
Funkce, která může být považována za programový objekt. Například funkce vyššího pořadí může být předána nebo vrácena z jiných funkcí. V Visual Basic Delegáti a lambda výrazy jsou jazykové funkce, které podporují funkce vyššího řádu. Chcete-li napsat funkci s vyšším pořadím, deklarujete jeden nebo více argumentů pro převzetí delegátů a často používáte lambda výrazy při volání. Mnoho standardních operátorů dotazu je funkce vyššího řádu.

Další informace najdete v tématu [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

výraz lambda \
V podstatě vložená anonymní funkce, kterou lze použít všude, kde se očekává typ delegáta. Toto je zjednodušená definice výrazů lambda, ale je vhodná pro účely tohoto kurzu.

Další informace o naleznete v tématu [lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

kolekce
Strukturovaná sada dat, obvykle s jednotným typem. Aby byla kolekce kompatibilní s technologií LINQ, musí implementovat rozhraní <xref:System.Collections.IEnumerable> nebo rozhraní <xref:System.Linq.IQueryable> (nebo jeden z jejich obecných protějšků, <xref:System.Collections.Generic.IEnumerator%601> nebo <xref:System.Linq.IQueryable%601>).

řazená kolekce členů (anonymní typy) \
Matematický koncept, řazená kolekce členů je konečná sekvence objektů, z nichž každý konkrétní typ. Řazená kolekce členů je také známá jako uspořádaný seznam. Anonymní typy jsou implementací jazyka tohoto konceptu, která umožňuje deklaraci nepojmenovaného typu třídy a vytváření instancí objektu daného typu ve stejnou dobu.

Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

odvození typu (implicitní zadání) \
Schopnost kompilátoru určit typ proměnné v absence explicitní deklarace typu.

Další informace naleznete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

odložené provádění a opožděné vyhodnocení \
Zpoždění vyhodnocení výrazu, dokud není skutečně vyžadováno jeho vyřešená hodnota. Odložené provádění je v kolekcích podporováno.

Další informace naleznete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) a [odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Tyto jazykové funkce budou použity v ukázkách kódu v této části.

## <a name="see-also"></a>Viz také:

- [Úvod do čistě funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
