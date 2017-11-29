---
title: "Principy a terminologií (funkční transformaci) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12b40d31688d852c9f9b3f644f64fc273c76209c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Principy a terminologií (funkční transformaci) (Visual Basic)
Toto téma představuje koncepty a přehled terminologie čistý funkční transformací. Funkční transformace přístup k transformaci dat poskytuje kód, který je často rychlejší programu, více výrazovou a snazší ladit a udržovat než tradiční, imperativní programování.  
  
 Všimněte si, že témata v této části nejsou určeny k vysvětlují plně funkční programování. Místo toho tato témata identifikovat některé funkční programovací možnosti, které usnadňují transformace XML z jednoho obrazce do jiného.  
  
## <a name="what-is-pure-functional-transformation"></a>Co je čistě funkční transformace?  
 V *čistý funkční transformace*, sadu funkcí, nazývá *čistý funkce*, definovat, jak sadu strukturovaná data z původní podobě transformace do jiného formátu. Slovo "čistý" označuje, že jsou funkce *bez možnosti složení*, která vyžaduje, aby byly:  
  
-   *Samostatný*tak, aby bylo možné volně seřazené a přeskupení bez entanglement nebo vzájemné závislosti se zbytkem programu. Čistý transformace mít žádné znalosti nebo platnost při jejich prostředí. To znamená, obsahovat funkcí používaných v transformaci *vedlejší účinky*.  
  
-   *Bezstavové*tak, aby provedením stejnou funkci nebo konkrétní sadu funkcí na stejné vstup vždy způsobí stejný výstup. Čistý transformace mít žádná paměť jeho předchozí použití.  
  
> [!IMPORTANT]
>  Ve zbývající části tohoto kurzu termín "čistý funkce" se používá v obecném smyslu označíte programovací přístup a ne funkce konkrétní jazyk.  
>   
>  Všimněte si, že čistý funkce musí být implementována jako funkce v jazyce Visual Basic.  
>   
>  Navíc Nezaměňujte čistý funkce s čistě virtuální metody v jazyce C++. Ta označuje, že obsahující třída je abstraktní a, jsou dodané žádná metoda textu.  
  
### <a name="functional-programming"></a>Funkční programování  
 *Funkční programování* je programovací přístup, který přímo podporuje čistý funkční transformace.  
  
 Pro obecné účely funkční programovací jazyky, jako je například ML, schéma, Haskell a F # upřednostňovaly především v zájmu academic komunity. I když ho vždy bylo možné zapisovat čistý funkční transformace v jazyce Visual Basic, je obtížné to tak není provedené ho atraktivní možnost většina programátory v jazyce. Pomocí novější verze jazyka Visual Basic ale nový jazyk vytvoří, jako je lambda – výrazy a odvození typu, aby funkční programování mnohem snazší a zvýšit produktivitu.  
  
 Další informace o funkční programování najdete v tématu [funkční programování vs. Imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Specifické pro doménu FP jazyky  
 I když obecné funkční programovací jazyky nebyly přijaty široce, konkrétní specifické pro doménu funkční programovací jazyky předtím lepší úspěch. Například stylů CSS (Cascading Style) slouží k určení vzhledu a chování mnoho webových stránek a stylů transformace jazyk (XSLT) jsou často používány v manipulaci s daty XML. Další informace o XSLT najdete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminologie  
 Následující tabulka definuje některé podmínky týkající se funkční transformace.  
  
 Funkce vyšší pořadí (první třídy)  
 Funkce, která lze považovat za programový objektu. Například funkce vyšší pořadí můžete předaný nebo vrácená z dalších funkcí. V jazyce Visual Basic Delegáti a výrazy lambda jsou jazykové funkce, které podporují funkce vyšší pořadí. Zápis funkce vyšší pořadí, deklarovat jeden nebo více argumentů provést Delegáti a při volání metody se často použití výrazů lambda. Mnoho standardní operátory dotazu je funkce vyšší pořadí.  
  
 Další informace najdete v tématu [standardní dotaz přehled operátory (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 výraz lambda  
 V podstatě vložené anonymní funkce, která lze použít bez ohledu na očekáván je typ delegáta. Toto je zjednodušená definice výrazů lambda, ale je dostačující pro účely tohoto kurzu.  
  
 Další informace najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 – kolekce  
 Strukturované sada dat, obvykle uniform typu. Aby byl kompatibilní s dotazy LINQ, kolekce musí implementovat <xref:System.Collections.IEnumerable> rozhraní nebo <xref:System.Linq.IQueryable> rozhraní (nebo jeden z jejich obecné protějšky <xref:System.Collections.Generic.IEnumerator%601> nebo <xref:System.Linq.IQueryable%601>).  
  
 řazené kolekce členů (anonymní typy)  
 Matematické koncept, řazené kolekce členů je omezené pořadí objektů, každý z konkrétního typu. Řazené kolekce členů se taky říká uspořádaného seznamu. Anonymní typy jsou jazyk implementace tohoto konceptu, která umožnit typ nepojmenované třídu deklarovat a objekt typu, které se vytvořit instanci ve stejnou dobu.  
  
 Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 odvození typu (implicitní zadáním)  
 Možnost kompilátor určit typ proměnné chybí deklarace explicitního typu.  
  
 Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 odložené provedení a opožděné vyhodnocení  
 Zpozdit vyhodnocení výrazu, dokud jeho vyřešit hodnota je ve skutečnosti povinný. Odložené provedení je podporována v kolekcích.  
  
 Další informace najdete v tématu [základní operace dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) a [odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Tyto funkce jazyk se použije v ukázky kódu v této části.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkční programování vs. Imperativní programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
