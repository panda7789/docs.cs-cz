---
description: klauzule JOIN – reference jazyka C#
title: klauzule JOIN – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 44b35bd1243e4715f81513eef9968f30a8f315a3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139746"
---
# <a name="join-clause-c-reference"></a>join – klauzule (Referenční dokumentace jazyka C#)

`join`Klauzule je užitečná pro přidružení prvků z různých zdrojových sekvencí, které nemají přímý vztah v objektovém modelu. Jediným požadavkem je, aby elementy v jednotlivých zdrojích sdílely určitou hodnotu, která může být porovnána s rovností. Například distributor potravinářského prostředí může mít seznam dodavatelů určitého produktu a seznam nákupčích. `join`Klauzuli lze použít například k vytvoření seznamu dodavatelů a nákupčích tohoto produktu, kteří jsou ve stejné konkrétní oblasti.

`join`Klauzule přijímá jako vstup dvě zdrojové sekvence. Prvky v každé sekvenci musí být buď nebo obsahují vlastnost, která může být porovnána s odpovídající vlastností v druhé sekvenci. `join`Klauzule porovnává zadané klíče k rovnosti pomocí `equals` klíčového slova Special. Všechna spojení prováděná `join` klauzulí jsou equijoins. Tvar výstupu `join` klauzule závisí na konkrétním typu spojení, které provádíte. Níže jsou tři nejběžnější typy spojení:

- Vnitřní spojení

- Spojení skupin

- Levé vnější spojení

## <a name="inner-join"></a>Vnitřní spojení

Následující příklad ukazuje jednoduchý vnitřní equijoin. Tento dotaz vytvoří nestrukturovanou posloupnost párů "název produktu/kategorie". Stejný řetězec kategorie se zobrazí ve více prvcích. Pokud prvek z `categories` nemá žádnou shodu `products` , tato kategorie se ve výsledcích nezobrazí.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Další informace najdete v tématu [provádění vnitřních spojení](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Spojení skupin

`join`Klauzule s `into` výrazem se nazývá spojení se skupinou.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Spojení se skupinou vytvoří hierarchickou sekvenci výsledků, která přidruží prvky v levé zdrojové sekvenci k jednomu nebo více shodným prvkům zdrojové sekvence na pravé straně. Spojení se skupinami nemá v relačních výrazech žádný ekvivalent. v podstatě je to sekvence polí objektů.

Pokud se nenajde žádné elementy z pravé zdrojové sekvence, aby odpovídaly elementu v levém zdroji, klauzule vytvoří `join` pro tuto položku prázdné pole. Proto je spojení se skupinou stále v podstatě vnitřní equijoin s tím rozdílem, že je sekvence výsledků uspořádána do skupin.

Pokud jste vybrali jenom výsledky spojení se skupinami, můžete k položkám přistupovat, ale nemůžete identifikovat klíč, na kterém se shodují. Proto je obecně vhodnější vybrat výsledky připojení skupiny do nového typu, který má také název klíče, jak je znázorněno v předchozím příkladu.

Můžete samozřejmě také použít výsledek spojení skupiny jako generátor jiného poddotazu:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Další informace najdete v tématu [provedení seskupených spojení](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Levé vnější spojení

V levém vnějším spojení jsou vráceny všechny prvky v levé zdrojové sekvenci, a to i v případě, že v pravé sekvenci nejsou žádné vyhovující prvky. K provedení levého vnějšího spojení v LINQ použijte `DefaultIfEmpty` metodu v kombinaci s připojením skupiny k určení výchozího prvku na pravé straně, který se vytvoří, pokud element na levé straně nemá žádné shody. Můžete použít `null` jako výchozí hodnotu libovolného typu odkazu nebo můžete zadat uživatelsky definovaný výchozí typ. V následujícím příkladu je zobrazen uživatelsky definovaný výchozí typ:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Další informace najdete v tématu [provedení levých vnějších spojení](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Operátor Equals

`join`Klauzule provede výjimku equijoin. Jinými slovy, můžete pouze základní shody s rovností dvou klíčů. Jiné typy porovnání, jako je "větší než" nebo "nerovnost", nejsou podporovány. Aby bylo jasné, že se všechna spojení equijoins, `join` použije klauzule `equals` místo operátoru klíčové slovo `==` . `equals`Klíčové slovo lze použít pouze v `join` klauzuli a liší se od `==` operátora v jednom důležitém způsobu. Pomocí `equals` , levý klíč spotřebovává vnější zdrojovou sekvenci a pravý klíč spotřebovává vnitřní zdroj. Vnější zdroj je pouze v rozsahu na levé straně `equals` a vnitřní zdrojová sekvence je pouze v rozsahu na pravé straně.

## <a name="non-equijoins"></a>Bez equijoins

`from`K zavedení nových sekvencí nezávisle na dotaz můžete použít více klauzulí, a to pomocí více klauzulí. Další informace najdete v tématu [provádění vlastních operací spojení](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Spojení s kolekcemi objektů vs. relačními tabulkami

Ve výrazu dotazu LINQ se operace join provádí na kolekcích objektů. Kolekce objektů nemohou být "připojené" stejným způsobem jako dvě relační tabulky. V LINQ jsou explicitní `join` klauzule požadovány pouze v případě, že dvě zdrojové sekvence nejsou svázány s žádnou relací. Při práci s se [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tabulky cizích klíčů v objektovém modelu reprezentují jako vlastnosti primární tabulky. Například v databázi Northwind má tabulka Customer relaci cizího klíče s tabulkou Orders. Při mapování tabulek na objektový model má třída Customer vlastnost Orders, která obsahuje kolekci objednávek přidružených k danému zákazníkovi. V důsledku toho se připojení už pro vás udělalo.

Další informace o dotazování napříč souvisejícími tabulkami v kontextu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] naleznete v tématu [How to: map Database Relationships](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Složené klíče

K otestování rovnosti více hodnot můžete použít složený klíč. Další informace najdete v tématu [připojení pomocí složených klíčů](../../linq/join-by-using-composite-keys.md). V klauzuli lze použít také složené klíče `group` .

## <a name="example"></a>Příklad

Následující příklad porovnává výsledky vnitřního spojení, spojení skupin a levé vnější spojení se stejnými zdroji dat pomocí stejných shodných klíčů. Do těchto příkladů se přidá nějaký další kód, který vyjasní výsledky v zobrazení konzoly.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Poznámky

`join`Klauzule, která není následována, `into` je přeložena do <xref:System.Linq.Enumerable.Join%2A> volání metody. `join`Klauzule, která je následována, `into` je přeložena na <xref:System.Linq.Enumerable.GroupJoin%2A> volání metody.

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
