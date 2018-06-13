---
title: group – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 2674986013afccf0a61267e49ca186d2ccb380e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217481"
---
# <a name="group-clause-c-reference"></a>group – klauzule (Referenční dokumentace jazyka C#)
`group` Klauzule vrací posloupnost <xref:System.Linq.IGrouping%602> objekty, které obsahovat nula nebo více položek, které odpovídají hodnotě klíče pro skupinu. Například můžete seskupit posloupnost řetězce podle první písmeno každého řetězce. V takovém případě první písmeno je klíč a má typ [char](../../../csharp/language-reference/keywords/char.md)a je uložen ve `Key` vlastnost jednotlivých <xref:System.Linq.IGrouping%602> objektu. Kompilátor odvodí typ klíče.  
  
 Můžete ukončit výrazu dotazu s `group` klauzule, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 Pokud chcete provést operace další dotazů pro každou skupinu, můžete zadat identifikátor dočasné pomocí [do](../../../csharp/language-reference/keywords/into.md) kontextové klíčové slovo. Při použití `into`, musíte pokračovat dotaz a nakonec ho ukončit některým `select` příkaz nebo jiné `group` klauzule, jak je znázorněno v následující výpis:  
  
 [!code-csharp[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 Více dokončit příklady použití `group` a bez `into` jsou uvedeny v části Příklad v tomto tématu.  
  
## <a name="enumerating-the-results-of-a-group-query"></a>Vytváření výčtu výsledků dotazu skupiny  
 Protože <xref:System.Linq.IGrouping%602> objekty produkovaný `group` dotaz jsou v podstatě seznam seznamů, je nutné použít vnořený [foreach](../../../csharp/language-reference/keywords/foreach-in.md) smyčky přístup k položkám v každé skupině. Vnější smyčky iteruje nad klíče skupiny a vnitřní smyčky iteruje nad každou položku v samotné skupině. Skupina může mít klíč, ale žádné elementy. Toto je `foreach` smyčky, který provede daný dotaz v předchozích příkladech kódu:  
  
 [!code-csharp[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## <a name="key-types"></a>Typy klíčů  
 Klíče skupiny mohou být jakéhokoli typu, například řetězce, integrované číselného typu nebo uživatelsky definovaných s názvem typu nebo anonymního typu.  
  
### <a name="grouping-by-string"></a>Seskupení řetězce  
 V předchozích příkladech kód používá `char`. Řetězec klíč může snadno bylo zadáno místo, například dokončení příjmení:  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### <a name="grouping-by-bool"></a>Seskupování podle bool  
 Následující příklad ukazuje použití bool hodnotu pro klíč k rozdělení výsledky do dvou skupin. Všimněte si, že hodnota je produkovaný dílčích výrazů v `group` klauzule.  
  
 [!code-csharp[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### <a name="grouping-by-numeric-range"></a>Seskupování podle číselný rozsah  
 Další příklad používá k vytvoření klíče číselné skupiny, které představují percentilu rozsah výraz. Všimněte si použití [umožní](../../../csharp/language-reference/keywords/let-clause.md) jako do vhodného umístění pro uložení metodu volat výsledek, takže není nutné volat metodu dvakrát v `group` klauzule. Všimněte si také v `group` klauzule, aby se zabránilo výjimky "dělení nulou" kód zkontroluje, ujistěte se, že student nemá v průměru nula. Další informace o tom, jak bezpečně použít metody ve výrazech dotazů najdete v tématu [postupy: zpracování výjimek ve výrazech dotazů](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).  
  
 [!code-csharp[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### <a name="grouping-by-composite-keys"></a>Seskupování podle složené klíče  
 Složený klíč používejte, pokud chcete seskupení prvků podle více než jeden klíč. Složený klíč vytvoříte pomocí anonymní typ nebo pojmenovaného typu pro uložení klíče elementu. V následujícím příkladu předpokládáme, že třídu `Person` bylo deklarováno se členy s názvem `surname` a `city`. `group` Klauzule způsobí, že má být vytvořen pro každou sadu osob, které mají stejný název poslední a stejné města samostatnou skupinu.  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 Použijte pojmenovaného typu, pokud je nutné předat proměnnou dotaz na jinou metodu. Vytváření speciální třídy pomocí automaticky implementované vlastnosti pro klíče a pak přepsat <xref:System.Object.Equals%2A> a <xref:System.Object.GetHashCode%2A> metody. Můžete také použít struktury, v takovém případě není nutné výhradně přepsat tyto metody. Další informace najdete v části [postupy: implementace třídy Lightweight vlastnostmi Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) a [postup: dotazu na duplicitní soubory v adresářovém stromu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Toto téma obsahuje příklad kódu, který ukazuje, jak použít složený klíč s názvem typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje standardní vzor pro řazení zdroje dat do skupin při použití žádné další dotaz logiku do skupin. Tomu se říká seskupení bez pokračování. Prvků v poli řetězců se seskupí podle jejich první písmeno. Výsledek dotazu je <xref:System.Linq.IGrouping%602> typ, který obsahuje veřejné `Key` vlastnost typu `char` a <xref:System.Collections.Generic.IEnumerable%601> kolekce, která obsahuje každou položku v seskupení.  
  
 Výsledek `group` klauzule je posloupnost pořadí. Proto pro přístup k jednotlivé prvky v rámci skupiny pro každý vrácený, použít vnořený `foreach` smyčky uvnitř smyčky, který iteruje klíče skupiny, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak provádět další logiku navíc na skupiny po vytvoření je pomocí *pokračování* s `into`. Další informace najdete v tématu [do](../../../csharp/language-reference/keywords/into.md). V následujícím příkladu se dotazuje každou skupinu a vyberte pouze ty, jehož hodnota klíče je samohláskou.  
  
 [!code-csharp[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Při kompilaci `group` klauzule jsou přeložit na volání <xref:System.Linq.Enumerable.GroupBy%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.IGrouping%602>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.Enumerable.ThenBy%2A>  
 <xref:System.Linq.Enumerable.ThenByDescending%2A>  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Postupy: vytvoření vnořené skupiny](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [Postupy: seskupení výsledků dotazu](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [Postupy: provádění poddotazů na skupinách](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
