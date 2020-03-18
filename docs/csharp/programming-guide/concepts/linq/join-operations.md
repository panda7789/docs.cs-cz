---
title: JoinOperace (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868002"
---
# <a name="join-operations-c"></a>Operace spojení (C#)

*Spojení* dvou zdrojů dat je přidružení objektů v jednom zdroji dat k objektům, které sdílejí společný atribut v jiném zdroji dat.  
  
 Spojení je důležitá operace v dotazech, které cílí na zdroje dat, jejichž vzájemné vztahy nelze sledovat přímo. V objektově orientovaném programování to může znamenat korelaci mezi objekty, které nejsou modelovány, jako je například směr dozadu jednosměrného vztahu. Příkladem jednosměrného vztahu je třída Customer, která má vlastnost typu Město, ale třída Město nemá vlastnost, která je kolekcí objektů Customer. Pokud máte seznam objektů City a chcete najít všechny zákazníky v každém městě, můžete je najít pomocí operace spojení.  
  
 Metody spojení poskytované v rámci LINQ jsou <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>. Tyto metody provádět equijoins nebo spojení, které odpovídají dva zdroje dat na základě rovnosti jejich klíče. (Pro srovnání, Transact-SQL podporuje operátory spojení jiné než "rovná", například operátor "menší než".) V termínech relační databáze <xref:System.Linq.Enumerable.Join%2A> implementuje vnitřní spojení, typ spojení, ve kterém jsou vráceny pouze ty objekty, které mají shodu v jiné datové sadě. Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nemá žádný přímý ekvivalent v termínech relační databáze, ale implementuje nadmnožinu vnitřní spojení a levé vnější spojení. Levé vnější spojení je spojení, které vrací každý prvek prvního (levého) zdroje dat, i když nemá žádné korelované prvky v jiném zdroji dat.  
  
 Následující obrázek znázorňuje koncepční zobrazení dvou sad a prvků v rámci těchto sad, které jsou zahrnuty buď v vnitřní spojení nebo levé vnější spojení.  
  
 ![Dva překrývající se kruhy zobrazující vnitřní&#47;vnější.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Spojí dvě sekvence založené na funkcích selektoru klíčů a extrahuje dvojice hodnot.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Spojí dvě sekvence založené na funkcích selektoru klíčů a seskupí výsledné shody pro každý prvek.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu
  
### Join  
  
Následující příklad používá `join … in … on … equals …` klauzuli spojit dvě sekvence na základě určité hodnoty:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

Následující příklad používá `join … in … on … equals … into …` klauzuli spojit dvě sekvence na základě určité hodnoty a seskupí výsledné shody pro každý prvek:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Anonymní typy](../../classes-and-structs/anonymous-types.md)
- [Formulování spojení a dotazů napříč produkty](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [spojit klauzuli](../../../language-reference/keywords/join-clause.md)
- [Joinpomocí složených klíčů](../../../linq/join-by-using-composite-keys.md)
- [Jak se připojit k obsahu z odlišných souborů (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Řazení výsledků klauzule join](../../../linq/order-the-results-of-a-join-clause.md)
- [Provádění vlastních operací spojování](../../../linq/perform-custom-join-operations.md)
- [Provádění seskupených spojení](../../../linq/perform-grouped-joins.md)
- [Provádění vnitřních spojení](../../../linq/perform-inner-joins.md)
- [Provedení levých vnějších spojení](../../../linq/perform-left-outer-joins.md)
- [Jak naplnit kolekce objektů z více zdrojů (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
