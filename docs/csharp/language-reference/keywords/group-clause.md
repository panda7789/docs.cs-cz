---
title: Group – klauzule - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 6c28f9f4cdcb2ec2d84f299dddb13dc821c1739a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238166"
---
# <a name="group-clause-c-reference"></a>group – klauzule (Referenční dokumentace jazyka C#)

`group` Klauzule vrátí sekvenci <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které odpovídají hodnotě klíče pro skupinu. Můžete například seskupit posloupnost řetězce jsou první písmena jednotlivých řetězců. V tomto případě první písmeno jednotky je klíč a má typ [char](char.md)a je uložen v `Key` vlastnosti každého <xref:System.Linq.IGrouping%602> objektu. Kompilátor odvodí typ klíče.

Můžete ukončit pomocí výrazu dotazu `group` klauzule, jak je znázorněno v následujícím příkladu:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Pokud chcete provádět operace dalšího dotazu pro každou skupinu, můžete určit identifikátor dočasné pomocí [do](into.md) kontextové klíčové slovo. Při použití `into`, musíte pokračovat s dotazem a nakonec ukončit některým `select` příkazu nebo jiného `group` klauzule, jak je znázorněno v následujícím výtažku:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Více kompletní příklady použití `group` a nemusíte `into` jsou k dispozici v oddíle Příklad tohoto článku.

## <a name="enumerating-the-results-of-a-group-query"></a>Vytváření výčtu výsledků dotazu skupiny

Protože <xref:System.Linq.IGrouping%602> objekty vytvářené `group` dotaz jsou v podstatě seznam seznamů, je nutné použít vnořený [foreach](foreach-in.md) smyčky pro přístup k položkám v každé skupině. Vnější smyčka Iteruje přes skupiny klíče a vnitřní smyčku iteruje každou položku v samotnou skupinu. Skupina může mít klíč, ale žádné elementy. Tady je `foreach` smyčku, která spustí dotaz v předchozích příkladech kódu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy klíčů

Skupiny klíče může být libovolný typ, například řetězce, vestavěným číselným typem nebo uživatelem definované s názvem typu nebo anonymního typu.

### <a name="grouping-by-string"></a>Seskupení podle řetězce

V předchozích příkladech kódu použít `char`. Řetězec klíče může snadno nebyli určeni místo, například dokončení příjmení:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Seskupení podle bool

Následující příklad ukazuje použití bool hodnotu pro klíč k rozdělení výsledky do dvou skupin. Všimněte si, že hodnota je produkovaný dílčí výraz v `group` klauzuli.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Seskupení podle číselného rozsahu

Následující příklad používá výraz k vytvoření klíče číselné skupiny, které představují širokou percentil. Všimněte si použití [nechat](let-clause.md) jako vhodné umístění pro uložení metodu výsledek volání, takže není nutné volat metodu dvěma časy `group` klauzuli. Další informace o tom, jak bezpečně použít metody ve výrazech dotazů najdete v tématu [jak: Zpracování výjimek ve výrazech dotazů](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Seskupování pomocí složených klíčů

Složený klíč používejte, pokud chcete seskupit elementy podle více než jeden klíč. Vytvoříte složený klíč pomocí anonymního typu nebo typu s názvem pro uložení klíčovým prvkem. V následujícím příkladu se předpokládá, že třída `Person` byla deklarována s členy s názvem `surname` a `city`. `group` Klauzule způsobí, že mají být vytvořeny pro každou sadu osoby se stejným názvem poslední a stejném městě samostatnou skupinu.

```csharp
group person by new {name = person.surname, city = person.city};
```

Použijte pojmenovaného typu, pokud je proměnná dotazu musí předávat na jinou metodu. Vytváření speciální třídy pomocí automaticky implementovaných vlastností pro klíče a potom přepsat <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody. Můžete také použít – struktura, v takovém případě není nutné výhradně přepsat tyto metody. Další informace najdete v části [jak: Implementace lehké třídy s automaticky implementovanými vlastnostmi](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [jak: Dotazu na duplicitní soubory v adresářovém stromu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Ten článek obsahuje příklad kódu, který ukazuje, jak použít složený klíč s názvem typu.

## <a name="example"></a>Příklad

Následující příklad ukazuje standardní vzor k řazení zdroje dat do skupin, při použití logiky bez dalšího dotazu do skupin. Tomu se říká seskupení bez pokračování. Prvky v poli řetězců jsou seskupeny podle jejich první písmeno. Výsledek dotazu je <xref:System.Linq.IGrouping%602> typ, který obsahuje veřejnou `Key` vlastnost typu `char` a <xref:System.Collections.Generic.IEnumerable%601> kolekce, která obsahuje každou položku v seskupení.

Výsledek `group` sekvence sekvencí je klauzule. Proto se pro přístup k jednotlivým prvkům v rámci jednotlivých skupin vrácené, použití vnořeného `foreach` smyčky uvnitř smyčky, která iteruje skupiny klíče, jak je znázorněno v následujícím příkladu.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak provádět další logiku na skupiny po jejich vytvoření s použitím *pokračování* s `into`. Další informace najdete v tématu [do](into.md). V následujícím příkladu se dotazuje každou skupinu a vybrat jenom na ty, jejichž hodnota klíče je samohláskou.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Poznámky

V době kompilace `group` klauzule jsou přeloženy do volání <xref:System.Linq.Enumerable.GroupBy%2A> metody.

## <a name="see-also"></a>Viz také:

- <xref:System.Linq.IGrouping%602>  
- <xref:System.Linq.Enumerable.GroupBy%2A>  
- <xref:System.Linq.Enumerable.ThenBy%2A>  
- <xref:System.Linq.Enumerable.ThenByDescending%2A>  
- [Klíčová slova dotazu](query-keywords.md)  
- [LINQ (Language Integrated Query)](../../linq/index.md)  
- [Vytvoření vnořené skupiny](../../linq/create-a-nested-group.md)  
- [Seskupení výsledků dotazu](../../linq/group-query-results.md)  
- [Provádění poddotazů na skupinách](../../linq/perform-a-subquery-on-a-grouping-operation.md)
