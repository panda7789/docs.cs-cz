---
title: Zpracování hodnot null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: c45c6672983866df6c47ec84981cc7bd11637c0c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249074"
---
# <a name="handling-null-values"></a>Zpracování hodnot null
Hodnota null v relační databázi se používá, pokud je hodnota ve sloupci neznámá nebo chybí. Null není prázdný řetězec (pro datové typy znaku nebo datetime) ani nulová hodnota (pro číselné datové typy). Specifikace ANSI SQL-92 uvádí, že null musí být stejné pro všechny datové typy, takže všechny hodnoty null jsou zpracovány konzistentně. Obor <xref:System.Data.SqlTypes> názvů poskytuje null sémantiku <xref:System.Data.SqlTypes.INullable> implementací rozhraní. Každý z datových <xref:System.Data.SqlTypes> typů `IsNull` v aplikaci má svou vlastní vlastnost a hodnotu, `Null` kterou lze přiřadit k instanci tohoto datového typu.  
  
> [!NOTE]
> Rozhraní .NET Framework verze 2.0 zavedla podporu pro typy hodnot s hodnotou s hodnotou s hodnotou, které umožňují programátorům rozšířit typ hodnoty tak, aby představoval všechny hodnoty základního typu. Tyto clr null hodnoty typy představují <xref:System.Nullable> instanci struktury. Tato funkce je užitečná zejména v případě, že jsou typy hodnot zabaleny a nezabaleny, což poskytuje rozšířenou kompatibilitu s typy objektů. Clr null typy hodnot nejsou určeny pro ukládání databáze nulls, protože ANSI SQL `null` null `Nothing` se nechová stejným způsobem jako odkaz (nebo v jazyce Visual Basic). Pro práci s databázemi ANSI <xref:System.Data.SqlTypes> SQL null <xref:System.Nullable>hodnoty, použijte nulls spíše než . Další informace o práci s typy s hodnotou CLR s možnou hodnotou null v jazyce Visual Basic naleznete v [tématech Typy hodnot s možnou hodnotou Null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)a C# naleznete v [tématech Typy hodnot S možnou hodnotou Null](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Null a logika se třemi hodnotami  
 Povolení hodnot null v definicích sloupců zavádí do aplikace logiku se třemi hodnotami. Porovnání lze vyhodnotit na jednu ze tří podmínek:  
  
- True  
  
- False  
  
- Není známo  
  
 Protože null je považován za neznámý, dvě hodnoty null ve srovnání s sebou nejsou považovány za rovné. Ve výrazech používajících aritmetické operátory, pokud má některý z operandů hodnotu null, je výsledek také null.  
  
## <a name="nulls-and-sqlboolean"></a>Nulla a SqlBoolean  
 Porovnání mezi <xref:System.Data.SqlTypes> any <xref:System.Data.SqlTypes.SqlBoolean>vrátí . Funkce `IsNull` pro `SqlType` každý <xref:System.Data.SqlTypes.SqlBoolean> vrátí a lze zkontrolovat hodnoty null. Následující tabulky pravdy ukazují, jak operátory AND, OR a NOT fungují v přítomnosti hodnoty null. (T = pravda, F = false a U = neznámý, nebo null.)  
  
 ![Tabulka pravdy](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Principy možnosti ANSI_NULLS  
 <xref:System.Data.SqlTypes>poskytuje stejnou sémantiku jako při ANSI_NULLS možnost je nastavena na SQL Server. Všechny aritmetické operátory (+, -, \*, ,,, %), bitové operátory (~, &), \|a většina funkcí vrátí `IsNull`hodnotu null, pokud je některý z operandů nebo argumentů null, s výjimkou vlastnosti .  
  
 Standard ANSI SQL-92 nepodporuje *columnName* = NULL v klauzuli WHERE. V SQL Server ANSI_NULLS možnost řídí výchozí nullability v databázi a vyhodnocení porovnání s hodnotami null. Pokud je ANSI_NULLS zapnuto (výchozí), musí být operátor IS NULL použit ve výrazech při testování hodnot NULL. Například následující porovnání vždy dává neznámý, když je ANSI_NULLS zapnuto:  
  
```sql
colname > NULL  
```  
  
 Porovnání s proměnnou obsahující hodnotu null také poskytuje neznámý:  
  
```sql
colname > @MyVariable  
```  
  
 K testování nulové hodnoty použijte predikát IS NULL nebo IS NOT NULL. To může přidat složitost klauzule WHERE. Například sloupec TerritoryID v tabulce AdventureWorks Customer umožňuje hodnoty null. Pokud select příkaz je test pro hodnoty null kromě jiných, musí obsahovat predikát IS NULL:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Pokud nastavíte ANSI_NULLS off v SQL Server, můžete vytvořit výrazy, které používají operátor rovnosti porovnat s null. Nelze však zabránit různým připojením v nastavení nulových možností pro toto připojení. Použití IS NULL k testování nulových hodnot vždy funguje, bez ohledu na ANSI_NULLS nastavení připojení.  
  
 Nastavení ANSI_NULLS vypnuto není `DataSet`podporováno v aplikaci , která vždy dodržuje standard <xref:System.Data.SqlTypes>ANSI SQL-92 pro zpracování hodnot null v aplikaci .  
  
## <a name="assigning-null-values"></a>Přiřazení nulových hodnot  
 Hodnoty Null jsou zvláštní a jejich sémantiku úložiště a přiřazení se liší v různých typech systémů a systémů úložiště. A `Dataset` je určen pro použití s různými typy a úložnými systémy.  
  
 Tato část popisuje nulovou sémantiku pro <xref:System.Data.DataColumn> přiřazení <xref:System.Data.DataRow> nulových hodnot v systémech v různých typech.  
  
 `DBNull.Value`  
 Toto přiřazení je `DataColumn` platné pro libovolného typu. Pokud typ implementuje , `INullable` `DBNull.Value` je vykonaněn do příslušné silného typu Null hodnotu.  
  
 `SqlType.Null`  
 Všechny <xref:System.Data.SqlTypes> datové `INullable`typy implementují . Pokud lze hodnotu null silného typu převést na datový typ sloupce pomocí implicitních operátorů přetypování, přiřazení by mělo projít. V opačném případě je vyvolána neplatná výjimka přetypovaného vysílání.  
  
 `null`  
 Pokud 'null' je právní hodnota `DataColumn` pro daný datový typ, je `DbNull.Value` vynutí do příslušné nebo `Null` spojené s typem `INullable` (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 Pro sloupce UDT jsou hodnoty null vždy uloženy `DataColumn`na základě typu přidruženého k souboru . Zvažte případ UDT přidružené `DataColumn` s, který `INullable` neimplementuje, zatímco jeho podtřídy. V tomto případě pokud je přiřazena hodnota null silného typu přidružená k odvozené `DbNull.Value`třídě, je uložena jako netypová , protože úložiště null je vždy konzistentní s datovým typem DataColumn.  
  
> [!NOTE]
> Struktura `Nullable<T>` <xref:System.Nullable> nebo není aktuálně podporována `DataSet`v .  
  
### <a name="multiple-column-row-assignment"></a>Přiřazení s více sloupci (řádek)  
 `DataTable.Add`, `DataTable.LoadDataRow`nebo jiná rozhraní API, <xref:System.Data.DataRow.ItemArray%2A> která přijímají, který získá mapovány na řádek, mapovat 'null' na výchozí hodnotu DataColumn. Pokud objekt v poli `DbNull.Value` obsahuje nebo jeho protějšk silného typu, jsou použita stejná pravidla, jak je popsáno výše.  
  
 Kromě toho platí následující pravidla pro `DataRow.["columnName"]` instanci přiřazení null:  
  
1. Výchozí *výchozí* hodnota `DbNull.Value` je pro všechny kromě sloupců null silného typu, kde je příslušná hodnota null silného typu.  
  
2. Hodnoty null nejsou nikdy zapsány během serializace na soubory XML (jako v "xsi:nil").  
  
3. Všechny hodnoty bez nuly, včetně výchozích hodnot, jsou vždy zapsány při serializaci do xml. To je na rozdíl od sémantiky XSD/XML, kde je hodnota null (xsi:nil) explicitní a výchozí hodnota je implicitní (pokud není k dispozici ve formátu XML, validující analyzátor ji může získat z přidruženého schématu XSD). Opak platí pro `DataTable`: hodnota null je implicitní a výchozí hodnota je explicitní.  
  
4. Všem chybějícím hodnotám sloupců pro řádky přečtené ze vstupu XML je přiřazena hodnota NULL. Řádkům <xref:System.Data.DataTable.NewRow%2A> vytvořeným pomocí nebo podobným metodám je přiřazena výchozí hodnota datacolumnu.  
  
5. Metoda <xref:System.Data.DataRow.IsNull%2A> vrátí `true` pro `DbNull.Value` `INullable.Null`obě a .  
  
## <a name="assigning-null-values"></a>Přiřazení nulových hodnot  
 Výchozí hodnota pro <xref:System.Data.SqlTypes> libovolnou instanci je null.  
  
 Nulls <xref:System.Data.SqlTypes> v jsou specifické pro typ a nemohou být `DbNull`reprezentovány jedinou hodnotou, například . Pomocí `IsNull` vlastnosti zkontrolujte null.  
  
 Hodnoty Null lze přiřadit <xref:System.Data.DataColumn> k a, jak je znázorněno v následujícím příkladu kódu. Proměnným můžete přímo `SqlTypes` přiřadit nulové hodnoty bez spuštění výjimky.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu <xref:System.Data.DataTable> vytvoří se dvěma sloupci definovanými jako <xref:System.Data.SqlTypes.SqlInt32> a <xref:System.Data.SqlTypes.SqlString>. Kód přidá jeden řádek známých hodnot, jeden řádek hodnot null <xref:System.Data.DataTable>a pak iterates přes , přiřazení hodnoty proměnným a zobrazení výstupu v okně konzoly.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Tento příklad zobrazuje následující výsledky:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porovnání hodnot Null s typy SqlTypes a CLR  
 Při porovnávání hodnot null je důležité pochopit rozdíl `Equals` mezi způsobem, jakým <xref:System.Data.SqlTypes> metoda vyhodnocuje hodnoty null ve srovnání se způsobem, jakým pracuje s typy CLR. <xref:System.Data.SqlTypes> `Equals` Všechny metody používají databázovou sémantiku pro vyhodnocení hodnot null: pokud je jedna nebo obě hodnoty null, porovnání dává hodnotu null. Na druhou stranu pomocí CLR `Equals` metoda <xref:System.Data.SqlTypes> na dva výnos true, pokud jsou oba null. To odráží rozdíl mezi použitím metody instance, `String.Equals` jako je například metoda CLR, a použitím statické/sdílené metody `SqlString.Equals`.  
  
 Následující příklad ukazuje rozdíl ve výsledcích `SqlString.Equals` mezi `String.Equals` metodou a metodou, když je každý předán dvojici hodnot null a pak dvojice prázdných řetězců.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kód vytváří následující výstup:  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a>Viz také

- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
