---
description: Group – klauzule – reference jazyka C#
title: Group – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 5e642492b4b36bb0464baf16baa80c58c19ba9f1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138225"
---
# <a name="group-clause-c-reference"></a>group – klauzule (Referenční dokumentace jazyka C#)

`group`Klauzule vrací sekvenci <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které odpovídají hodnotě klíče pro skupinu. Například můžete seskupit sekvenci řetězců podle prvního písmene v každém řetězci. V tomto případě je prvním písmenem klíč a má typ [char](../builtin-types/char.md)a je uložen ve `Key` vlastnosti každého <xref:System.Linq.IGrouping%602> objektu. Kompilátor odvodí typ klíče.

Můžete ukončit výraz dotazu s `group` klauzulí, jak je znázorněno v následujícím příkladu:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Pokud chcete pro každou skupinu provést další operace dotazování, můžete zadat dočasný identifikátor pomocí klíčového slova [into](into.md) . Když použijete `into` , musíte pokračovat v dotazu a nakonec ho ukončit buď pomocí `select` příkazu, nebo jiné `group` klauzule, jak je znázorněno v následujícím výňatku:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

`group` `into` V příkladu v tomto článku jsou uvedeny úplnější příklady použití příkazů with a bez nich.

## <a name="enumerating-the-results-of-a-group-query"></a>Vyčíslení výsledků dotazu skupiny

Vzhledem k tomu <xref:System.Linq.IGrouping%602> , že objekty vytvořené `group` dotazem jsou v podstatě seznam seznamů, je nutné použít vnořenou smyčku [foreach](foreach-in.md) pro přístup k položkám v každé skupině. Vnější smyčka projde klíče skupiny a vnitřní smyčka projde každou položku v samotné skupině. Skupina může mít klíč, ale neobsahuje žádné prvky. Následuje `foreach` smyčka, která spouští dotaz v předchozích příkladech kódu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy klíčů

Klíče skupiny mohou být libovolného typu, jako je například řetězec, vestavěný číselný typ nebo uživatelsky definovaný pojmenovaný typ nebo anonymní typ.

### <a name="grouping-by-string"></a>Seskupení podle řetězce

Předchozí příklady kódu používaly `char` . Místo toho je možné zadat klíč řetězce, například poslední příjmení:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Seskupení podle bool

Následující příklad ukazuje použití bool hodnoty pro klíč k rozdělení výsledků do dvou skupin. Všimněte si, že hodnota je vytvořena dílčím výrazem v `group` klauzuli.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Seskupení podle číselného rozsahu

Následující příklad používá výraz pro vytvoření číselné skupiny klíčů, které reprezentují rozsah percentilu. Všimněte si použití [let](let-clause.md) jako vhodného umístění pro uložení výsledku volání metody, takže nemusíte volat metodu dvakrát v `group` klauzuli. Další informace o bezpečném použití metod ve výrazech dotazů naleznete v tématu [zpracování výjimek ve výrazech dotazů](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Seskupení podle složených klíčů

Pokud chcete seskupit prvky podle více než jednoho klíče, použijte složený klíč. Složený klíč vytvoříte pomocí anonymního typu nebo pojmenovaného typu pro uložení klíčového elementu. V následujícím příkladu Předpokládejme, že třída `Person` byla deklarována s členy s názvem `surname` a `city` . `group`Klauzule způsobí vytvoření samostatné skupiny pro každou sadu osob se stejným názvem a stejným městem.

```csharp
group person by new {name = person.surname, city = person.city};
```

Pojmenovaný typ použijte v případě, že je nutné předat proměnnou dotazu jiné metodě. Vytvořte speciální třídu pomocí automaticky implementovaných vlastností klíčů a potom přepište <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> metody a. Můžete také použít strukturu. v takovém případě není nutné tyto metody přepsat bezpodmínečně. Další informace najdete v tématu [implementace odlehčené třídy s automaticky implementovanými vlastnostmi](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [Postup dotazování na duplicitní soubory v adresářovém stromu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Druhý článek obsahuje příklad kódu, který ukazuje, jak použít složený klíč s pojmenovaným typem.

## <a name="example"></a>Příklad

Následující příklad ukazuje standardní vzor pro řazení zdrojových dat do skupin, pokud se pro skupiny nepoužívá žádná další logika dotazu. Označuje se jako seskupení bez pokračování. Prvky v poli řetězců jsou seskupeny podle jejich prvního písmene. Výsledek dotazu je <xref:System.Linq.IGrouping%602> typ, který obsahuje veřejnou `Key` vlastnost typu `char` a <xref:System.Collections.Generic.IEnumerable%601> kolekci, která obsahuje každou položku v seskupení.

Výsledkem `group` klauzule je sekvence sekvencí. Proto pro přístup k jednotlivým prvkům v rámci jednotlivých vrácených skupin použijte vnořenou `foreach` smyčku uvnitř smyčky, která provede iteraci klíčů skupiny, jak je znázorněno v následujícím příkladu.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak provést další logiku pro skupiny po jejich vytvoření pomocí *pokračování* s `into` . Další informace najdete [v tématu.](into.md) Následující příklad dotazuje každou skupinu na výběr pouze těch, jejichž klíčová hodnota je samohláska.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Poznámky

V době kompilace `group` jsou klauzule přeloženy do volání <xref:System.Linq.Enumerable.GroupBy%2A> metody.

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
