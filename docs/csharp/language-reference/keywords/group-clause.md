---
title: klauzule Group – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 806bc3de138ebae682d2e248593230c753eb7ba2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422762"
---
# <a name="group-clause-c-reference"></a>group – klauzule (Referenční dokumentace jazyka C#)

Klauzule `group` vrací sekvenci <xref:System.Linq.IGrouping%602> objektů, které obsahují nula nebo více položek, které se shodují s hodnotou klíče pro skupinu. Například můžete seskupit sekvenci řetězců podle prvního písmene v každém řetězci. V tomto případě je prvním písmenem klíč a má typ [char](char.md)a je uložen ve vlastnosti `Key` každého objektu <xref:System.Linq.IGrouping%602>. Kompilátor odvodí typ klíče.

Můžete ukončit výraz dotazu s klauzulí `group`, jak je znázorněno v následujícím příkladu:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Pokud chcete pro každou skupinu provést další operace dotazování, můžete zadat dočasný identifikátor pomocí klíčového slova [into](into.md) . Při použití `into`musíte pokračovat v dotazu a nakonec ho ukončit buď pomocí příkazu `select` nebo jiné klauzule `group`, jak je znázorněno v následujícím výpisu:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Úplnější příklady použití `group` s a bez `into` jsou uvedené v příkladu v tomto článku.

## <a name="enumerating-the-results-of-a-group-query"></a>Vyčíslení výsledků dotazu skupiny

Vzhledem k tomu, že <xref:System.Linq.IGrouping%602> objekty vytvořené pomocí dotazu `group` jsou v podstatě seznam seznamů, je nutné použít vnořenou smyčku [foreach](foreach-in.md) pro přístup k položkám v každé skupině. Vnější smyčka projde klíče skupiny a vnitřní smyčka projde každou položku v samotné skupině. Skupina může mít klíč, ale neobsahuje žádné prvky. Následuje `foreach` smyčka, která spouští dotaz v předchozích příkladech kódu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy klíčů

Klíče skupiny mohou být libovolného typu, jako je například řetězec, vestavěný číselný typ nebo uživatelsky definovaný pojmenovaný typ nebo anonymní typ.

### <a name="grouping-by-string"></a>Seskupení podle řetězce

Předchozí příklady kódu používaly `char`. Místo toho je možné zadat klíč řetězce, například poslední příjmení:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Seskupení podle bool

Následující příklad ukazuje použití bool hodnoty pro klíč k rozdělení výsledků do dvou skupin. Všimněte si, že hodnota je vytvořena dílčím výrazem v klauzuli `group`.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Seskupení podle číselného rozsahu

Následující příklad používá výraz pro vytvoření číselné skupiny klíčů, které reprezentují rozsah percentilu. Všimněte si, že použití [let](let-clause.md) jako vhodného umístění pro uložení výsledku volání metody, takže nemusíte volat metodu dvakrát v klauzuli `group`. Další informace o bezpečném použití metod ve výrazech dotazů naleznete v tématu [How to: Handle Exceptions in Query Expressions](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Seskupení podle složených klíčů

Pokud chcete seskupit prvky podle více než jednoho klíče, použijte složený klíč. Složený klíč vytvoříte pomocí anonymního typu nebo pojmenovaného typu pro uložení klíčového elementu. V následujícím příkladu Předpokládejme, že třída `Person` byla deklarována s členy s názvem `surname` a `city`. Klauzule `group` způsobí, že se vytvoří samostatná skupina pro každou sadu osob se stejným názvem a stejným městem.

```csharp
group person by new {name = person.surname, city = person.city};
```

Pojmenovaný typ použijte v případě, že je nutné předat proměnnou dotazu jiné metodě. Vytvořte speciální třídu s použitím automaticky implementovaných vlastností klíčů a potom přepište metody <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A>. Můžete také použít strukturu. v takovém případě není nutné tyto metody přepsat bezpodmínečně. Další informace naleznete v tématu [How to: Implementing Lightweight Class s automaticky implementovanými vlastnostmi](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [Postupy: dotaz na duplicitní soubory ve stromové struktuře adresáře](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Druhý článek obsahuje příklad kódu, který ukazuje, jak použít složený klíč s pojmenovaným typem.

## <a name="example"></a>Příklad

Následující příklad ukazuje standardní vzor pro řazení zdrojových dat do skupin, pokud se pro skupiny nepoužívá žádná další logika dotazu. Označuje se jako seskupení bez pokračování. Prvky v poli řetězců jsou seskupeny podle jejich prvního písmene. Výsledkem dotazu je typ <xref:System.Linq.IGrouping%602>, který obsahuje vlastnost Public `Key` typu `char` a kolekci <xref:System.Collections.Generic.IEnumerable%601> obsahující každou položku v seskupení.

Výsledkem klauzule `group` je sekvence sekvencí. Proto pro přístup k jednotlivým prvkům v rámci jednotlivých vrácených skupin použijte vnořený `foreach` smyčka uvnitř smyčky, která opakuje klíče skupiny, jak je znázorněno v následujícím příkladu.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak provést další logiku pro skupiny po jejich vytvoření pomocí *pokračování* s `into`. Další informace najdete [v tématu.](into.md) Následující příklad dotazuje každou skupinu na výběr pouze těch, jejichž klíčová hodnota je samohláska.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Poznámky

V době kompilace jsou klauzule `group` přeloženy do volání metody <xref:System.Linq.Enumerable.GroupBy%2A>.

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
