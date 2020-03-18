---
title: klauzule join - Odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713406"
---
# <a name="join-clause-c-reference"></a>join – klauzule (Referenční dokumentace jazyka C#)

Klauzule je užitečná `join` pro asociování prvků z různých zdrojových sekvencí, které nemají žádný přímý vztah v objektovém modelu. Jediným požadavkem je, že prvky v každém zdroji sdílejí určitou hodnotu, kterou lze porovnat pro rovnost. Distributor potravin může mít například seznam dodavatelů určitého produktu a seznam kupujících. Klauzule `join` může být použita například k vytvoření seznamu dodavatelů a kupujících tohoto produktu, kteří jsou všichni ve stejné zadané oblasti.

Klauzule `join` trvá dvě zdrojové sekvence jako vstup. Prvky v každé sekvenci musí být nebo obsahovat vlastnost, která může být porovnána s odpovídající vlastností v jiné sekvenci. Klauzule `join` porovnává zadané klíče pro rovnost pomocí `equals` speciální klíčové slovo. Všechna spojení provedená `join` klauzulí jsou equijoins. Tvar výstupu `join` klauzule závisí na konkrétním typu spojení, které provádíte. Následují tři nejběžnější typy spojení:

- Vnitřní spojení

- Spojení se skupinou

- Levé vnější spojení

## <a name="inner-join"></a>Vnitřní spojení

Následující příklad ukazuje jednoduchý vnitřní equijoin. Tento dotaz vytváří plochou sekvenci párů "název produktu / kategorie". Stejný řetězec kategorie se zobrazí ve více prvcích. Pokud prvek `categories` z nemá `products`žádné odpovídající , tato kategorie se nezobrazí ve výsledcích.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Další informace naleznete v [tématu Provedení vnitřních spojení](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Spojení se skupinou

Klauzule `join` s `into` výrazem se nazývá skupinové spojení.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Spojení skupiny vytvoří hierarchickou sekvenci výsledků, která přidruží prvky v levé zdrojové sekvenci s jedním nebo více odpovídajícími prvky v posloupnosti zdroje na pravé straně. Spojení skupiny nemá z relačních podmínek žádný ekvivalent. je v podstatě posloupnost objektových polí.

Pokud žádné prvky z pravé zdrojové sekvence jsou nalezeny `join` tak, aby odpovídaly prvek v levém zdroji, klauzule vytvoří prázdné pole pro tuto položku. Proto spojení skupiny je stále v podstatě vnitřní equijoin s tím rozdílem, že výsledek sekvence je uspořádándo skupin.

Pokud vyberete výsledky skupinového spojení, můžete získat přístup k položkám, ale nemůžete identifikovat klíč, na který se shodují. Proto je obecně užitečnější vybrat výsledky skupiny spojit do nového typu, který má také název klíče, jak je znázorněno v předchozím příkladu.

Můžete také, samozřejmě, použít výsledek skupiny připojit jako generátor jiného poddotazu:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Další informace naleznete v [tématu Perform grouped joins](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Levé vnější spojení

V levém vnějším spojení jsou vráceny všechny prvky v levé zdrojové sekvenci, i když žádné odpovídající prvky jsou v pravém pořadí. Chcete-li provést levé vnější spojení `DefaultIfEmpty` v LINQ, použijte metodu v kombinaci se skupinovým spojením k určení výchozího prvku na pravé straně, který má být k výrobě, pokud prvek na levé straně nemá žádné shody. Jako výchozí `null` hodnotu můžete použít pro libovolný typ odkazu nebo můžete zadat výchozí typ definovaný uživatelem. V následujícím příkladu je zobrazen výchozí typ definovaný uživatelem:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Další informace naleznete v [tématu Provedení levého vnějšího spojení](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Operátor rovná se

Klauzule `join` provádí equijoin. Jinými slovy, můžete pouze založit shody na rovnost dvou klíčů. Jiné typy porovnání, například "větší než" nebo "není rovno" nejsou podporovány. Chcete-li jasně najevo, že všechna spojení `join` jsou `equals` equijoins, klauzule používá klíčové slovo namísto operátoru. `==` Klíčové `equals` slovo lze použít `join` pouze v klauzuli `==` a liší se od operátora jedním důležitým způsobem. S `equals`, levý klíč spotřebovává vnější zdrojové sekvence a pravý klíč spotřebovává vnitřní zdroj. Vnější zdroj je pouze v oboru `equals` na levé straně a vnitřní zdrojsekvence je pouze v oboru na pravé straně.

## <a name="non-equijoins"></a>Nee-spojení

Můžete provádět non-equijoins, křížové spojení a další operace `from` vlastního spojení pomocí více klauzulí zavést nové sekvence nezávisle do dotazu. Další informace naleznete v [tématu Provádění operací vlastního spojení](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Spojení na kolekcích objektů vs. relační tabulky

Ve výrazu dotazu LINQ jsou operace spojení prováděny na kolekcích objektů. Kolekce objektů nelze "spojit" přesně stejným způsobem jako dvě relační tabulky. V LINQ `join` explicitní klauzule jsou vyžadovány pouze v případě, že dvě zdrojové sekvence nejsou vázány žádný vztah. Při práci [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]s , tabulky cizího klíče jsou reprezentovány v objektovém modelu jako vlastnosti primární tabulky. Například v databázi Northwind má tabulka Zákazník vztah cizího klíče s tabulkou Objednávky. Když mapujete tabulky na objektový model, třída Customer má vlastnost Orders, která obsahuje kolekci objednávek přidružených k tomuto zákazníkovi. Ve skutečnosti již bylo spojení provedeno za vás.

Další informace o dotazování napříč souvisejícími tabulkami v kontextu naleznete v tématu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]How [to: Map Database Relationships](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Složené klávesy

Rovnost více hodnot můžete otestovat pomocí složeného klíče. Další informace naleznete v tématu [Join pomocí složených klíčů](../../linq/join-by-using-composite-keys.md). Složené klíče lze také `group` použít v klauzuli.

## <a name="example"></a>Příklad

Následující příklad porovnává výsledky vnitřní spojení, spojení skupiny a levé vnější spojení na stejné zdroje dat pomocí stejné odpovídající klíče. Některé další kód je přidán do těchto příkladů objasnit výsledky v konzolové zobrazení.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Poznámky

Klauzule, `join` která není `into` následuje je <xref:System.Linq.Enumerable.Join%2A> přeložen do volání metody. Klauzule, `join` která `into` je následována, je přeložena do volání <xref:System.Linq.Enumerable.GroupJoin%2A> metody.

## <a name="see-also"></a>Viz také

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [Operace sjednocení](../../programming-guide/concepts/linq/join-operations.md)
- [group – klauzule](group-clause.md)
- [Provedení levých vnějších spojení](../../linq/perform-left-outer-joins.md)
- [Provádění vnitřních spojení](../../linq/perform-inner-joins.md)
- [Provádění seskupených spojení](../../linq/perform-grouped-joins.md)
- [Řazení výsledků klauzule join](../../linq/order-the-results-of-a-join-clause.md)
- [Spojení pomocí složených klíčů](../../linq/join-by-using-composite-keys.md)
- [Kompatibilní databázové systémy pro Visual Studio](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
