---
title: klauzule JOIN – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713406"
---
# <a name="join-clause-c-reference"></a>join – klauzule (Referenční dokumentace jazyka C#)

Klauzule `join` je užitečná pro přidružení prvků z různých zdrojových sekvencí, které nemají přímou relaci v objektovém modelu. Jediným požadavkem je, aby elementy v jednotlivých zdrojích sdílely určitou hodnotu, která může být porovnána s rovností. Například distributor potravinářského prostředí může mít seznam dodavatelů určitého produktu a seznam nákupčích. Klauzuli `join` lze použít například k vytvoření seznamu dodavatelů a nákupčích tohoto produktu, kteří jsou ve stejné konkrétní oblasti.

Klauzule `join` přijímá jako vstup dvě zdrojové sekvence. Prvky v každé sekvenci musí být buď nebo obsahují vlastnost, která může být porovnána s odpovídající vlastností v druhé sekvenci. Klauzule `join` porovnává zadané klíče k rovnosti pomocí klíčového slova Special `equals`. Všechna spojení prováděná klauzulí `join` jsou equijoins. Tvar výstupu klauzule `join` závisí na konkrétním typu spojení, které provádíte. Níže jsou tři nejběžnější typy spojení:

- Vnitřní spojení

- Spojení skupin

- Levé vnější spojení

## <a name="inner-join"></a>Vnitřní spojení

Následující příklad ukazuje jednoduchý vnitřní equijoin. Tento dotaz vytvoří nestrukturovanou posloupnost párů "název produktu/kategorie". Stejný řetězec kategorie se zobrazí ve více prvcích. Pokud prvek z `categories` nemá žádné odpovídající `products`, tato kategorie se ve výsledcích nezobrazí.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Další informace najdete v tématu [provádění vnitřních spojení](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Spojení skupin

Klauzule `join` s výrazem `into` se nazývá spojení se skupinou.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Spojení se skupinou vytvoří hierarchickou sekvenci výsledků, která přidruží prvky v levé zdrojové sekvenci k jednomu nebo více shodným prvkům zdrojové sekvence na pravé straně. Spojení se skupinami nemá v relačních výrazech žádný ekvivalent. v podstatě je to sekvence polí objektů.

Pokud se nenajde žádné elementy z pravé zdrojové sekvence, aby odpovídaly elementu v levém zdroji, klauzule `join` vytvoří prázdné pole pro tuto položku. Proto je spojení se skupinou stále v podstatě vnitřní equijoin s tím rozdílem, že je sekvence výsledků uspořádána do skupin.

Pokud jste vybrali jenom výsledky spojení se skupinami, můžete k položkám přistupovat, ale nemůžete identifikovat klíč, na kterém se shodují. Proto je obecně vhodnější vybrat výsledky připojení skupiny do nového typu, který má také název klíče, jak je znázorněno v předchozím příkladu.

Můžete samozřejmě také použít výsledek spojení skupiny jako generátor jiného poddotazu:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Další informace najdete v tématu [provedení seskupených spojení](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Levé vnější spojení

V levém vnějším spojení jsou vráceny všechny prvky v levé zdrojové sekvenci, a to i v případě, že v pravé sekvenci nejsou žádné vyhovující prvky. K provedení levého vnějšího spojení v LINQ použijte metodu `DefaultIfEmpty` v kombinaci s připojením skupiny k určení výchozího prvku na pravé straně, který se vytvoří, pokud element na levé straně nemá žádné shody. Můžete použít `null` jako výchozí hodnotu pro jakýkoli typ odkazu, nebo můžete zadat uživatelsky definovaný výchozí typ. V následujícím příkladu je zobrazen uživatelsky definovaný výchozí typ:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Další informace najdete v tématu [provedení levých vnějších spojení](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Operátor Equals

Klauzule `join` provádí equijoin. Jinými slovy, můžete pouze základní shody s rovností dvou klíčů. Jiné typy porovnání, jako je "větší než" nebo "nerovnost", nejsou podporovány. Aby bylo jasné, že se všechna spojení equijoins, klauzule `join` používá klíčové slovo `equals` namísto operátoru `==`. Klíčové slovo `equals` lze použít pouze v klauzuli `join` a liší se od operátoru `==` v jednom důležitém způsobu. V `equals`levý klíč spotřebovává vnější zdrojovou sekvenci a pravý klíč spotřebuje vnitřní zdroj. Vnější zdroj je pouze v rozsahu na levé straně `equals` a vnitřní zdrojová sekvence je pouze v rozsahu na pravé straně.

## <a name="non-equijoins"></a>Bez equijoins

Pomocí několika klauzulí `from` můžete provádět nezávisle na neequijoins, křížové spojení a další vlastní operace JOIN, které zavádějí nové sekvence nezávisle na dotaz. Další informace najdete v tématu [provádění vlastních operací spojení](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Spojení s kolekcemi objektů vs. relačními tabulkami

Ve výrazu dotazu LINQ se operace join provádí na kolekcích objektů. Kolekce objektů nemohou být "připojené" stejným způsobem jako dvě relační tabulky. V LINQ jsou klauzule Explicit `join` požadovány pouze v případě, že dvě zdrojové sekvence nejsou svázány s žádnou relací. Při práci s [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]jsou tabulky cizích klíčů v objektovém modelu reprezentovány jako vlastnosti primární tabulky. Například v databázi Northwind má tabulka Customer relaci cizího klíče s tabulkou Orders. Při mapování tabulek na objektový model má třída Customer vlastnost Orders, která obsahuje kolekci objednávek přidružených k danému zákazníkovi. V důsledku toho se připojení už pro vás udělalo.

Další informace o dotazování napříč souvisejícími tabulkami v kontextu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]naleznete v tématu [How to: map Database Relationships](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Složené klíče

K otestování rovnosti více hodnot můžete použít složený klíč. Další informace najdete v tématu [připojení pomocí složených klíčů](../../linq/join-by-using-composite-keys.md). Složené klíče lze také použít v klauzuli `group`.

## <a name="example"></a>Příklad

Následující příklad porovnává výsledky vnitřního spojení, spojení skupin a levé vnější spojení se stejnými zdroji dat pomocí stejných shodných klíčů. Do těchto příkladů se přidá nějaký další kód, který vyjasní výsledky v zobrazení konzoly.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Poznámky

Klauzule `join`, která není následována `into` je přeložena do volání metody <xref:System.Linq.Enumerable.Join%2A>. Klauzule `join`, která je následována `into` je přeložena na volání metody <xref:System.Linq.Enumerable.GroupJoin%2A>.

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [ (LINQ)](../../linq/index.md)
- [Operace sjednocení](../../programming-guide/concepts/linq/join-operations.md)
- [group – klauzule](group-clause.md)
- [Provedení levých vnějších spojení](../../linq/perform-left-outer-joins.md)
- [Provádění vnitřních spojení](../../linq/perform-inner-joins.md)
- [Provádění seskupených spojení](../../linq/perform-grouped-joins.md)
- [Řazení výsledků klauzule join](../../linq/order-the-results-of-a-join-clause.md)
- [Spojení pomocí složených klíčů](../../linq/join-by-using-composite-keys.md)
- [Kompatibilní databázové systémy pro Visual Studio](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
