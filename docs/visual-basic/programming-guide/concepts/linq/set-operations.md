---
title: Množinové operace
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406817"
---
# <a name="set-operations-visual-basic"></a>Operace set (Visual Basic)

Operace s nastavením v LINQ odkazují na operace dotazů, které tvoří sadu výsledků dotazu založenou na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).

Standardní metody operátoru dotazu, které provádějí operace set, jsou uvedeny v následující části.

## <a name="methods"></a>Metody

|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|Odebere z kolekce duplicitní hodnoty.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|S výjimkou|Vrátí množinu rozdílů, což znamená prvky jedné kolekce, které se nezobrazují v druhé kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Krývají|Vrátí průnik sady, což znamená prvky, které se zobrazují v každé ze dvou kolekcí.|Neužívá se.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|Sjednocení|Vrátí sjednocení set, což znamená jedinečné prvky, které se zobrazí v obou dvou kolekcích.|Neužívá se.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>Porovnání operací set

### <a name="distinct"></a>Distinct

Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody v sekvenci znaků. Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.

![Obrázek znázorňující chování odlišného&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>S výjimkou

Následující ilustrace znázorňuje chování nástroje <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> . Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou ve druhé vstupní sekvenci.

![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")

### <a name="intersect"></a>Krývají

Následující ilustrace znázorňuje chování nástroje <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> . Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.

![Obrázek znázorňující průnik dvou sekvencí](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>Sjednocení

Následující ilustrace znázorňuje operaci sjednocení na dvou sekvencích znaků. Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.

![Obrázek znázorňující sjednocení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu

V následujícím příkladu je použita `Distinct` klauzule v dotazu LINQ pro vrácení jedinečných čísel ze seznamu celých čísel.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Distinct – klauzule](../../../language-reference/queries/distinct-clause.md)
- [Postupy: kombinování a porovnávání kolekcí řetězců (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)
- [Postupy: Vyhledání nastaveného rozdílu mezi dvěma seznamy (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)
