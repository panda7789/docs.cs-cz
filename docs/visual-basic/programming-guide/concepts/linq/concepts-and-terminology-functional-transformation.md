---
title: Koncepty a terminologie (funkční transformace) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 1a2dd2fe835ada29fdb6639905673b4e0b60aca6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642032"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Koncepty a terminologie (funkční transformace) (Visual Basic)
Toto téma představuje koncepty a terminologie čistě funkční transformace. Funkční transformace přístup k transformaci dat vrací kód, který je často rychlejší program, více výrazovými možnostmi a jednodušší vyladit a udržovat než tradiční, imperativní programování.  
  
 Všimněte si, že témata v této části nejsou určeny k vysvětlení plně funkčního programování. Místo toho tato témata obsahují některé funkční programovací funkce, které usnadňují transformovat XML z jednoho obrazce.  
  
## <a name="what-is-pure-functional-transformation"></a>Co je čistě funkční transformace?  
 V *čistě funkční transformace*, sadu funkcí volaných *čistě funkce*, definovat, jak transformovat sadu strukturovaná data z původní podobě do jiného formátu. Slovo "čistě" označuje, že jsou funkce *sestavitelné*, což vyžaduje, aby byly:  
  
- *Samostatná*, takže je možné libovolně seřazených a změnit jejich uspořádání bez entanglement nebo vzájemných závislostí s využitím zbytku programu. Čistě transformace mít žádné znalosti jazyka nebo vliv na jejich prostředí. To znamená, nemají tyto funkce používají v transformace bez *vedlejší účinky*.  
  
- *Bezstavové*tak, aby provádí stejnou funkci nebo konkrétní sadu funkcí na stejný vstup vždy výsledkem bude stejný výstup. Čistě transformace mají nedostatek paměti jejich předchozí použití.  
  
> [!IMPORTANT]
>  Ve zbývající části tohoto kurzu se používá termín "čistě funkce" v obecném smyslu označující programovací přístup a není funkce konkrétní jazyk.  
>   
>  Všimněte si, že čistě funkce musí být implementovány jako funkce v jazyce Visual Basic.  
>   
>  Také Nezaměňujte čistě funkce s čistě virtuální metody v jazyce C++. Ten označuje, že obsahující třída je abstraktní a že je zadané žádné tělo metody.  
  
### <a name="functional-programming"></a>Funkční programování  
 *Funkční programování* je programovací přístup, který přímo podporuje čistě funkční transformace.  
  
 V minulosti pro obecné účely funkčních programovacích jazycích, jako je například ML, schéma, Haskell, a F#, byla primárně zájmu academic komunitě. I když bylo vždy možné psát v jazyce Visual Basic čistě funkčním transformacím, problémy s dokončením udělat proto nebyla dostal atraktivní možnosti většiny programátorům. V novějších verzích jazyka Visual Basic ale nový jazyk vytvoří jako výrazy lambda a odvození typu proměnné, aby funkční programování mnohem jednodušší a produktivnější.  
  
 Další informace o funkční programování, naleznete v tématu [funkční programování vs. Imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Jazyky FP specifického pro doménu  
 I když obecné funkčních programovacích jazyků nebyly přijaty široce, konkrétní specifického pro doménu funkčních programovacích jazyků měli lepší úspěch. Například stylů CSS (Cascading Style) slouží k určení vzhledu a chování mnoho webových stránek a šablony stylů transformace XSLT (Extensible Language) šablony stylů jsou často používány v manipulaci s daty XML. Další informace o XSLT, naleznete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminologie  
 Následující tabulka definuje termíny týkající se funkční transformace.  
  
 (první třídy) funkce vyššího řádu  
 Funkce, která lze považovat za objekt prostřednictvím kódu programu. Například funkce vyššího řádu můžete předat nebo vrácená z dalších funkcí. V jazyce Visual Basic delegáty a výrazy lambda jsou funkcí jazyka, které podporují funkce vyššího řádu. Zápis funkce vyššího řádu, deklarujte jeden nebo více argumentů se delegáty a při volání metody se často používají výrazy lambda. Mnoho standardních operátorů pro dotazování je funkce vyššího řádu.  
  
 Další informace najdete v tématu [přehled operátory standardního dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Výraz lambda  
 V podstatě vložené anonymní funkce, která se dá použít, kdykoli se očekává typ delegáta. Toto je zjednodušenou definici výrazů lambda, ale je vhodný pro účely tohoto kurzu.  
  
 Další informace najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
  – kolekce  
 Strukturovaného sady dat, obvykle jednotného typu. Aby byl kompatibilní s jazykem LINQ, musí implementovat kolekce <xref:System.Collections.IEnumerable> rozhraní nebo <xref:System.Linq.IQueryable> rozhraní (nebo jeden z jejich obecné protějšky <xref:System.Collections.Generic.IEnumerator%601> nebo <xref:System.Linq.IQueryable%601>).  
  
 řazené kolekce členů (anonymní typy)  
 Matematické koncept, řazené kolekce členů je omezené sekvenci objektů, každý z určitého typu. Řazená kolekce členů se také nazývá uspořádaného seznamu. Anonymní typy jsou implementace jazyka tento koncept, které zajišťují nepojmenovaný typ třídy deklarovat a objekt daného typu má být vytvořena ve stejnou dobu.  
  
 Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 odvození typu (implicitního zápisu)  
 Možnost kompilátoru k určení typu proměnné chybí deklaraci explicitního typu.  
  
 Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 odložené provedení a opožděné vyhodnocení  
 Zpoždění vyhodnocení výrazu do její hodnotu přeložit je skutečně nutná. Odložené provedení je podporována v kolekcích.  
  
 Další informace najdete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) a [odložené provedení a opožděné vyhodnocení v LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Tyto funkce jazyka se použije v ukázky kódu v celé této části.  
  
## <a name="see-also"></a>Viz také:

- [Úvod k čistě funkčním transformacím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. Imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
