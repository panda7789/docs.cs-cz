---
title: klauzule skupiny - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713473"
---
# <a name="group-clause-c-reference"></a>group – klauzule (Referenční dokumentace jazyka C#)

Klauzule `group` vrátí posloupnost <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které odpovídají hodnotě klíče pro skupinu. Můžete například seskupit posloupnost řetězců podle prvního písmene v každém řetězci. V tomto případě první písmeno je klíč a má [znak](../builtin-types/char.md) `Key` typu a <xref:System.Linq.IGrouping%602> je uložen ve vlastnosti každého objektu. Kompilátor odvodí typ klíče.

Výraz dotazu můžete ukončit klauzulí, `group` jak je znázorněno v následujícím příkladu:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Pokud chcete provést další operace dotazu v každé skupině, můžete zadat dočasný identifikátor pomocí do [kontextové](into.md) klíčové slovo. Při použití `into`je nutné pokračovat v dotazu a nakonec `select` jej ukončit příkazem nebo jinou `group` klauzulí, jak je znázorněno v následujícím výňatku:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Podrobnější příklady použití `group` s a `into` bez jsou uvedeny v příkladu části tohoto článku.

## <a name="enumerating-the-results-of-a-group-query"></a>Výčet výsledků skupinového dotazu

Vzhledem <xref:System.Linq.IGrouping%602> k tomu, že objekty vytvořené dotazem `group` jsou v podstatě seznam seznamy, je nutné použít vnořené [foreach](foreach-in.md) smyčky pro přístup k položkám v každé skupině. Vnější smyčka iterát přes klíče skupiny a vnitřní smyčka iterates přes každou položku v samotné skupině. Skupina může mít klíč, ale žádné prvky. Následuje `foreach` smyčka, která spustí dotaz v předchozích příkladech kódu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy klíčů

Klíče skupiny mohou být libovolný typ, například řetězec, předdefinovaný číselný typ nebo uživatelem definovaný pojmenovaný typ nebo anonymní typ.

### <a name="grouping-by-string"></a>Seskupení podle řetězce

Předchozí příklady kódu `char`používaly . Místo toho mohl být snadno zadán řetězec, například úplný příjmení:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Seskupení podle bool

Následující příklad ukazuje použití bool hodnotu klíče rozdělit výsledky do dvou skupin. Všimněte si, že hodnota je vytvořena `group` podvýraz v klauzuli.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Seskupení podle číselného rozsahu

Další příklad používá výraz k vytvoření číselných skupinových klíčů, které představují rozsah percentilu. Všimněte si použití [let](let-clause.md) jako vhodné umístění pro uložení výsledku volání metody, takže není `group` třeba volat metodu dvakrát v klauzuli. Další informace o bezpečném použití metod ve výrazech dotazu naleznete [v tématu Zpracování výjimek ve výrazech dotazu](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Seskupení podle složených klíčů

Složený klíč použijte, pokud chcete seskupit prvky podle více než jednoho klíče. Složený klíč vytvoříte pomocí anonymního typu nebo pojmenovaného typu pro uložení klíčového prvku. V následujícím příkladu předpokládejme, že třída `Person` `surname` byla `city`deklarována s členy s názvem a . Klauzule `group` způsobí, že samostatná skupina má být vytvořena pro každou sadu osob se stejným příjmením a stejné město.

```csharp
group person by new {name = person.surname, city = person.city};
```

Pojmenovaný typ použijte, pokud je nutné předat proměnnou dotazu jiné metodě. Vytvořte speciální třídu pomocí automaticky implementovaných vlastností <xref:System.Object.Equals%2A> pro <xref:System.Object.GetHashCode%2A> klíče a pak přepsat metody a. Můžete také použít strukturu, v takovém případě není nutné přísně přepsat tyto metody. Další informace naleznete [v tématu Jak implementovat zjednodušenou třídu s automaticky implementovanými vlastnostmi](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [Jak se dotazovat na duplicitní soubory ve stromu adresářů](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Druhý článek má příklad kódu, který ukazuje, jak používat složený klíč s pojmenovaným typem.

## <a name="example"></a>Příklad

Následující příklad ukazuje standardní vzor pro řazení zdrojových dat do skupin, pokud není použita žádná další logika dotazu pro skupiny. To se nazývá seskupení bez pokračování. Prvky v poli řetězců jsou seskupeny podle jejich prvního písmene. Výsledkem <xref:System.Linq.IGrouping%602> dotazu je typ, který `Key` obsahuje `char` veřejnou <xref:System.Collections.Generic.IEnumerable%601> vlastnost typu a kolekci, která obsahuje každou položku ve seskupení.

Výsledkem `group` klauzule je posloupnost sekvencí. Proto pro přístup k jednotlivým prvkům v rámci `foreach` každé vrácené skupiny použijte vnořenou smyčku uvnitř smyčky, která itestraje klíče skupiny, jak je znázorněno v následujícím příkladu.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak provést další logiku ve skupinách *continuation* po `into`jejich vytvoření pomocí pokračování s . Další informace naleznete [v tématu](into.md). Následující příklad dotazuje každou skupinu vybrat pouze ty, jejichž hodnota klíče je samohláská.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Poznámky

V době `group` kompilace klauzule jsou přeloženy do volání <xref:System.Linq.Enumerable.GroupBy%2A> metody.

## <a name="see-also"></a>Viz také

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [Klíčová slova dotazu](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [Vytvoření vnořené skupiny](../../linq/create-a-nested-group.md)
- [Seskupení výsledků dotazu](../../linq/group-query-results.md)
- [Provádění poddotazů na skupinách](../../linq/perform-a-subquery-on-a-grouping-operation.md)
