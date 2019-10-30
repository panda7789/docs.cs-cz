---
title: Zpracování hodnot null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: a634667ec8d963ef52abbdbe517a57d10e4a60fa
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040221"
---
# <a name="handling-null-values"></a>Zpracování hodnot null
Hodnota null v relační databázi se používá v případě, že hodnota ve sloupci není známá nebo chybí. Hodnota null není prázdným řetězcem (pro datové typy znaků nebo DateTime) ani nulovou hodnotou (pro číselné datové typy). Specifikace ANSI SQL-92 uvádí, že hodnota null musí být stejná pro všechny datové typy, aby všechny hodnoty null byly zpracovávány konzistentně. Obor názvů <xref:System.Data.SqlTypes> poskytuje sémantiku null implementací rozhraní <xref:System.Data.SqlTypes.INullable>. Každý datový typ v <xref:System.Data.SqlTypes> má svou vlastní vlastnost `IsNull` a `Null` hodnotu, kterou lze přiřadit k instanci daného datového typu.  
  
> [!NOTE]
> .NET Framework verze 2,0 představila podporu pro typy s možnou hodnotou null, které programátorům umožňují rozšiřování hodnotového typu tak, aby představovaly všechny hodnoty základního typu. Tyto typy s možnou hodnotou null reprezentují instanci <xref:System.Nullable> struktury. Tato možnost je užitečná hlavně v případě, že typy hodnot jsou zabalené a rozbalené a poskytují lepší kompatibilitu s typy objektů. Typy s možnou hodnotou null nejsou určené pro ukládání databázových hodnot null, protože ANSI SQL null se nechová stejně jako odkaz na `null` (nebo `Nothing` v Visual Basic). Pro práci s hodnotami null v databázi ANSI SQL použijte místo <xref:System.Nullable><xref:System.Data.SqlTypes> null. Další informace o práci s typy s možnou hodnotou null v Visual Basic naleznete v tématu [typy hodnot](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)s možnou hodnotou null a pro C# zobrazení hodnot s [možnou hodnotou null](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Hodnoty null a logika se třemi hodnotami  
 Povolení hodnot null v definicích sloupců zavádí do vaší aplikace logiku se třemi hodnotami. Porovnání se může vyhodnotit na jednu ze tří podmínek:  
  
- Podmínka  
  
- False  
  
- Neznámé  
  
 Vzhledem k tomu, že hodnota null je považována za neznámou, nepovažují se za dvě hodnoty null ve srovnání se stejnou hodnotou. V výrazech používajících aritmetické operátory, pokud má některý z operandů hodnotu null, má výsledek také hodnotu null.  
  
## <a name="nulls-and-sqlboolean"></a>Hodnoty null a SqlBoolean  
 Porovnání mezi libovolnými <xref:System.Data.SqlTypes> vrátí <xref:System.Data.SqlTypes.SqlBoolean>. Funkce `IsNull` pro každý `SqlType` vrací <xref:System.Data.SqlTypes.SqlBoolean> a lze ji použít ke kontrole hodnot null. Následující tabulky pravdy ukazují, jak operátory AND, OR a NOT fungují v přítomnosti hodnoty null. (T = true, F = false a U = Unknown nebo null)  
  
 ![Tabulka pravdy](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Princip možnosti ANSI_NULLS  
 <xref:System.Data.SqlTypes> poskytuje stejnou sémantiku jako při nastavení možnosti ANSI_NULLS v SQL Server. Všechny aritmetické operátory (+,-, \*,/,%), bitové operátory (~, &, \|) a většina funkcí vrací hodnotu null, pokud některý z operandů nebo argumentů má hodnotu null, s výjimkou `IsNull`vlastnosti.  
  
 Standard ANSI SQL-92 nepodporuje vlastnost *ColumnName* = null v klauzuli WHERE. V SQL Server možnost ANSI_NULLS řídí jako výchozí hodnotu null v databázi a vyhodnocení porovnání s hodnotami null. Pokud je zapnutá funkce ANSI_NULLS (výchozí), musí být při testování hodnot null ve výrazech použit operátor IS NULL. Například následující porovnání vždy vrátí Neznámý, pokud je ANSI_NULLS:  
  
```sql
colname > NULL  
```  
  
 Porovnání s proměnnou obsahující hodnotu null také neznáte:  
  
```sql
colname > @MyVariable  
```  
  
 Pro otestování hodnoty null použijte predikát IS NULL nebo NOT NULL. To může do klauzule WHERE přidat složitost. Například sloupec TerritoryID v tabulce zákazníků AdventureWorks povoluje hodnoty null. Pokud příkaz SELECT slouží k otestování hodnot null kromě ostatních, musí obsahovat predikát IS NULL:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Pokud jste v SQL Server nastavili ANSI_NULLS, můžete vytvořit výrazy, které používají operátor rovnosti k porovnání s hodnotou null. Nemůžete ale zabránit různým připojením v nastavení možností null pro toto připojení. Použití má hodnotu NULL k otestování hodnot null vždy funguje bez ohledu na nastavení ANSI_NULLS pro připojení.  
  
 Nastavení ANSI_NULLS off není v `DataSet`podporováno, což vždy vyhovuje standardu ANSI SQL-92 pro zpracování hodnot null v <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Přiřazení hodnot null  
 Hodnoty null jsou zvláštní a jejich sémantika úložiště a přiřazení se liší v různých systémech typů a úložných systémech. `Dataset` je navržená tak, aby se mohla používat s různými typy a úložnými systémy.  
  
 Tato část popisuje sémantiku null pro přiřazení hodnot null <xref:System.Data.DataColumn> v <xref:System.Data.DataRow> napříč různými systémy typů.  
  
 `DBNull.Value`  
 Toto přiřazení je platné pro `DataColumn` jakéhokoli typu. Pokud typ implementuje `INullable`, `DBNull.Value` je převedena do odpovídající hodnoty null typu s silnými typy.  
  
 `SqlType.Null`  
 Všechny datové typy <xref:System.Data.SqlTypes> implementují `INullable`. Pokud je hodnota null typu s hodnotou null převedena na datový typ sloupce pomocí operátorů implicitního přetypování, přiřazení by mělo projít. V opačném případě je vyvolána neplatná výjimka přetypování.  
  
 `null`  
 Pokud je hodnota null platnou hodnotou pro daný `DataColumn` datový typ, je převedena do příslušné `DbNull.Value` nebo `Null` přidružená k `INullable` typu (`SqlType.Null`).  
  
 `derivedUdt.Null`  
 Pro sloupce UDT jsou vždy uloženy hodnoty null na základě typu přidruženého k `DataColumn`. Vezměte v úvahu případ typu UDT přidruženého k `DataColumn`, který neimplementuje `INullable` v průběhu jeho dílčí třídy. V takovém případě, pokud je přiřazena hodnota null typu, která je přidružena k odvozené třídě, je uložena jako netypové `DbNull.Value`, protože úložiště s hodnotou null je vždy konzistentní s datovým typem DataColumn.  
  
> [!NOTE]
> `Nullable<T>` nebo struktura <xref:System.Nullable> se v `DataSet`aktuálně nepodporuje.  
  
### <a name="multiple-column-row-assignment"></a>Přiřazení více sloupců (řádků)  
 `DataTable.Add`, `DataTable.LoadDataRow`nebo jiná rozhraní API, která přijímají <xref:System.Data.DataRow.ItemArray%2A>, která jsou namapována na řádek, namapujte ' null ' na výchozí hodnotu DataColumn. Pokud objekt v poli obsahuje `DbNull.Value` nebo jeho protějšek se silným typem, jsou použita stejná pravidla, jak je popsáno výše.  
  
 Kromě toho platí následující pravidla pro instanci `DataRow.["columnName"]` přiřazení null:  
  
1. Výchozí *výchozí* hodnota je `DbNull.Value` pro všechny kromě silně typované sloupce s hodnotou null, kde se jedná o odpovídající silně typovou hodnotu null.  
  
2. Hodnoty null nejsou při serializaci do souborů XML nikdy zapsány (jako v "xsi: nil").  
  
3. Všechny hodnoty, které nejsou null, včetně výchozích hodnot, jsou při serializaci do jazyka XML vždy zapisovány. To je na rozdíl od sémantiky XSD/XML, kde hodnota null (xsi: nil) je explicitní a výchozí hodnota je implicitní (Pokud není obsažena v XML, je možné, že analyzátor ověří z přidruženého schématu XSD). U `DataTable`je opak true: hodnota null je implicitní a výchozí hodnota je explicitní.  
  
4. Všechny chybějící hodnoty sloupce pro řádky načtené ze vstupu XML mají přiřazenou hodnotu NULL. K řádkům vytvořeným pomocí <xref:System.Data.DataTable.NewRow%2A> nebo podobných metod jsou přiřazena výchozí hodnota DataColumn.  
  
5. Metoda <xref:System.Data.DataRow.IsNull%2A> vrací `true` jak pro `DbNull.Value`, tak pro `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Přiřazení hodnot null  
 Výchozí hodnota pro libovolnou instanci <xref:System.Data.SqlTypes> je null.  
  
 Hodnoty null v <xref:System.Data.SqlTypes> jsou specifické pro typ a nemohou být reprezentovány jedinou hodnotou, například `DbNull`. Pro kontrolu hodnot null použijte vlastnost `IsNull`.  
  
 Hodnotám null lze přiřadit <xref:System.Data.DataColumn>, jak je znázorněno v následujícím příkladu kódu. Hodnoty null můžete přímo přiřadit `SqlTypes` proměnným bez vyvolání výjimky.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří <xref:System.Data.DataTable> se dvěma sloupci definovanými jako <xref:System.Data.SqlTypes.SqlInt32> a <xref:System.Data.SqlTypes.SqlString>. Kód přidá jeden řádek známých hodnot, jeden řádek hodnot null a poté provede iteraci <xref:System.Data.DataTable>, přiřazením hodnot proměnným a zobrazením výstupu v okně konzoly.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 V tomto příkladu se zobrazí následující výsledky:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porovnání hodnot null s typy SqlTypes a CLR  
 Při porovnávání hodnot null je důležité pochopit rozdíl mezi způsobem, jakým metoda `Equals` vyhodnocuje hodnoty null v <xref:System.Data.SqlTypes> ve srovnání se způsobem, jakým funguje s typy CLR. Všechny metody <xref:System.Data.SqlTypes>`Equals` používají sémantiku databáze pro vyhodnocení hodnot null: Pokud buď nebo obě hodnoty mají hodnotu null, porovnání vrátí hodnotu null. Na druhé straně použití metody CLR `Equals` u dvou <xref:System.Data.SqlTypes> bude vracet hodnotu true, pokud jsou obě hodnoty null. To odráží rozdíl mezi použitím metody instance, jako je například CLR `String.Equals` metodou, a použitím statické/sdílené metody `SqlString.Equals`.  
  
 Následující příklad ukazuje rozdíl ve výsledcích mezi `SqlString.Equals` metodou a metodou `String.Equals`, když každá z nich předává dvojici hodnot null a pak dvojici prázdných řetězců.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kód generuje následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
