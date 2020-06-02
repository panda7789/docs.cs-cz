---
title: Zpracování hodnot null
description: Přečtěte si, jak .NET Framework Zprostředkovatel dat pro SQL Server zpracovává hodnotu null, a přečtěte si o hodnotách null a SqlBoolean, Logic se třemi hodnotami a přiřazení hodnot null.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: a4d086d81f1c2c959780366cfeb59f2d265bc40c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286452"
---
# <a name="handling-null-values"></a>Zpracování hodnot null
Hodnota null v relační databázi se používá v případě, že hodnota ve sloupci není známá nebo chybí. Hodnota null není prázdným řetězcem (pro datové typy znaků nebo DateTime) ani nulovou hodnotou (pro číselné datové typy). Specifikace ANSI SQL-92 uvádí, že hodnota null musí být stejná pro všechny datové typy, aby všechny hodnoty null byly zpracovávány konzistentně. <xref:System.Data.SqlTypes>Obor názvů poskytuje sémantiku null implementací <xref:System.Data.SqlTypes.INullable> rozhraní. Každý z datových typů v <xref:System.Data.SqlTypes> má svou vlastní `IsNull` vlastnost a `Null` hodnotu, kterou lze přiřadit k instanci daného datového typu.  
  
> [!NOTE]
> .NET Framework verze 2,0 představila podporu pro typy hodnot s možnou hodnotou null, které umožňují programátorům roztáhnout hodnotový typ, který představuje všechny hodnoty nadřazeného typu. Tyto typy hodnot s možnou hodnotou null reprezentují instanci <xref:System.Nullable> struktury. Tato možnost je užitečná hlavně v případě, že typy hodnot jsou zabalené a rozbalené a poskytují lepší kompatibilitu s typy objektů. Typy hodnot s možnou hodnotou null nejsou určeny pro ukládání databázových hodnot null, protože hodnota null jazyka ANSI SQL se chová stejným způsobem jako `null` odkaz (nebo `Nothing` v Visual Basic). Pro práci s hodnotami null v databázi ANSI SQL použijte hodnoty <xref:System.Data.SqlTypes> null namísto <xref:System.Nullable> . Další informace o práci s hodnotou null typů CLR v Visual Basic naleznete v tématu [typy hodnot](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)s možnou hodnotou null a v jazyce C# zobrazení [typů hodnot s možnou hodnotou null](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Hodnoty null a logika se třemi hodnotami  
 Povolení hodnot null v definicích sloupců zavádí do vaší aplikace logiku se třemi hodnotami. Porovnání se může vyhodnotit na jednu ze tří podmínek:  
  
- True  
  
- False  
  
- Není známo  
  
 Vzhledem k tomu, že hodnota null je považována za neznámou, nepovažují se za dvě hodnoty null ve srovnání se stejnou hodnotou. V výrazech používajících aritmetické operátory, pokud má některý z operandů hodnotu null, má výsledek také hodnotu null.  
  
## <a name="nulls-and-sqlboolean"></a>Hodnoty null a SqlBoolean  
 Porovnání mezi všemi <xref:System.Data.SqlTypes> vrátí <xref:System.Data.SqlTypes.SqlBoolean> . `IsNull`Funkce pro každý `SqlType` vrátí hodnotu <xref:System.Data.SqlTypes.SqlBoolean> a a lze ji použít ke kontrole hodnot null. Následující tabulky pravdy ukazují, jak operátory AND, OR a NOT fungují v přítomnosti hodnoty null. (T = true, F = false a U = Unknown nebo null)  
  
 ![Tabulka pravdy](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Princip možnosti ANSI_NULLS  
 <xref:System.Data.SqlTypes>poskytuje stejnou sémantiku jako při nastavení možnosti ANSI_NULLS v v SQL Server. Všechny aritmetické operátory (+,-, \* ,/,%), bitové operátory (~, &, \| ) a většina funkcí vrátí hodnotu null, pokud některý z operandů nebo argumentů má hodnotu null, s výjimkou vlastnosti `IsNull` .  
  
 Standard ANSI SQL-92 nepodporuje vlastnost *ColumnName* = null v klauzuli WHERE. V SQL Server možnost ANSI_NULLS řídí obě výchozí hodnoty null v databázi a vyhodnocení porovnání s hodnotami null. Pokud je zapnutá funkce ANSI_NULLS (výchozí), musí být při testování hodnot null ve výrazech použit operátor IS NULL. Například následující porovnání vždy vrátí Neznámý, pokud je ANSI_NULLS na:  
  
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
  
 Pokud jste v SQL Server nastavili ANSI_NULLS vypnuto, můžete vytvořit výrazy, které používají operátor rovnosti k porovnání s hodnotou null. Nemůžete ale zabránit různým připojením v nastavení možností null pro toto připojení. Použití má hodnotu NULL k otestování hodnot null vždy funguje bez ohledu na nastavení ANSI_NULLS pro připojení.  
  
 Nastavení ANSI_NULLS vypnuto není podporováno v `DataSet` , který vždy následuje standard ANSI SQL-92 pro zpracování hodnot null v <xref:System.Data.SqlTypes> .  
  
## <a name="assigning-null-values"></a>Přiřazení hodnot null  
 Hodnoty null jsou zvláštní a jejich sémantika úložiště a přiřazení se liší v různých systémech typů a úložných systémech. `Dataset`Je navržený tak, aby se mohl používat s různými typy a úložnými systémy.  
  
 Tato část popisuje sémantiku null pro přiřazení hodnot null do <xref:System.Data.DataColumn> v <xref:System.Data.DataRow> rámci různých systémů typů.  
  
 `DBNull.Value`  
 Toto přiřazení je platné pro `DataColumn` libovolný typ. Pokud typ implementuje `INullable` , `DBNull.Value` je převedena do odpovídající hodnoty null typu s silnými typy.  
  
 `SqlType.Null`  
 Všechny <xref:System.Data.SqlTypes> typy dat implementují `INullable` . Pokud je hodnota null typu s hodnotou null převedena na datový typ sloupce pomocí operátorů implicitního přetypování, přiřazení by mělo projít. V opačném případě je vyvolána neplatná výjimka přetypování.  
  
 `null`  
 Pokud je hodnota null platnou hodnotou pro daný `DataColumn` datový typ, je převedena do příslušné `DbNull.Value` nebo `Null` přidružené k `INullable` typu ( `SqlType.Null` ).  
  
 `derivedUdt.Null`  
 Pro sloupce UDT jsou vždy uloženy hodnoty null na základě typu přidruženého k `DataColumn` . Vezměte v úvahu případ typu UDT přidruženého k `DataColumn` , který není implementován `INullable` během jeho dílčí třídy. V tomto případě, je-li přiřazena hodnota null typu, která je přidružena k odvozené třídě, uložena jako netypové `DbNull.Value` , protože úložiště s hodnotou null je vždy konzistentní s datovým typem DataColumn.  
  
> [!NOTE]
> `Nullable<T>`Struktura nebo není <xref:System.Nullable> aktuálně podporována v `DataSet` .  
  
### <a name="multiple-column-row-assignment"></a>Přiřazení více sloupců (řádků)  
 `DataTable.Add`, `DataTable.LoadDataRow` nebo jiná rozhraní API, která přijímají objekt <xref:System.Data.DataRow.ItemArray%2A> , který je namapován na řádek, namapujte ' null ' na výchozí hodnotu DataColumn. Pokud objekt v poli obsahuje `DbNull.Value` nebo jeho protějšek se silným typem, jsou použita stejná pravidla, jak je popsáno výše.  
  
 Kromě toho platí následující pravidla pro instanci `DataRow.["columnName"]` přiřazení s hodnotou null:  
  
1. Výchozí *výchozí* hodnota je `DbNull.Value` pro všechny s výjimkou silně typované sloupce s hodnotou null, kde se jedná o příslušnou silně typovou hodnotu null.  
  
2. Hodnoty null nejsou při serializaci do souborů XML nikdy zapsány (jako v "xsi: nil").  
  
3. Všechny hodnoty, které nejsou null, včetně výchozích hodnot, jsou při serializaci do jazyka XML vždy zapisovány. To je na rozdíl od sémantiky XSD/XML, kde hodnota null (xsi: nil) je explicitní a výchozí hodnota je implicitní (Pokud není obsažena v XML, je možné, že analyzátor ověří z přidruženého schématu XSD). Opak je true pro `DataTable` : hodnota null je implicitní a výchozí hodnota je explicitní.  
  
4. Všechny chybějící hodnoty sloupce pro řádky načtené ze vstupu XML mají přiřazenou hodnotu NULL. Řádkům vytvořeným pomocí <xref:System.Data.DataTable.NewRow%2A> nebo podobných metod je přiřazena výchozí hodnota DataColumn.  
  
5. <xref:System.Data.DataRow.IsNull%2A>Metoda vrátí `true` pro i `DbNull.Value` `INullable.Null` .  
  
## <a name="assigning-null-values"></a>Přiřazení hodnot null  
 Výchozí hodnota pro libovolnou <xref:System.Data.SqlTypes> instanci je null.  
  
 Hodnoty null v <xref:System.Data.SqlTypes> jsou specifické pro typ a nemohou být reprezentovány jedinou hodnotou, například `DbNull` . `IsNull`Pro kontrolu hodnot null použijte vlastnost.  
  
 Hodnotám null lze přiřadit, <xref:System.Data.DataColumn> jak je znázorněno v následujícím příkladu kódu. Můžete přímo přiřadit hodnoty null `SqlTypes` proměnným bez vyvolání výjimky.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří <xref:System.Data.DataTable> pomocí dvou sloupců definovaných jako <xref:System.Data.SqlTypes.SqlInt32> a <xref:System.Data.SqlTypes.SqlString> . Kód přidá jeden řádek známých hodnot, jeden řádek hodnot null a poté provede iteraci <xref:System.Data.DataTable> , přiřazením hodnot proměnným a zobrazením výstupu v okně konzoly.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 V tomto příkladu se zobrazí následující výsledky:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porovnání hodnot null s typy SqlTypes a CLR  
 Při porovnávání hodnot null je důležité pochopit rozdíl mezi způsobem, `Equals` ve kterém metoda vyhodnocuje hodnoty null ve <xref:System.Data.SqlTypes> srovnání se způsobem, který funguje s typy CLR. Všechny <xref:System.Data.SqlTypes> `Equals` metody používají sémantiku databáze pro vyhodnocení hodnot null: Pokud buď nebo obě hodnoty mají hodnotu null, porovnávání vrátí hodnotu null. Na druhé straně použití `Equals` metody CLR na dvou <xref:System.Data.SqlTypes> povede hodnotu true, pokud jsou obě hodnoty null. To odráží rozdíl mezi použitím metody instance, jako je například metoda CLR `String.Equals` , a použitím statické/sdílené metody, `SqlString.Equals` .  
  
 Následující příklad ukazuje rozdíl ve výsledcích mezi `SqlString.Equals` metodou a `String.Equals` metodou, kdy každá z nich předává dvojici hodnot null a pak dvojici prázdných řetězců.  
  
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
  
## <a name="see-also"></a>Viz také

- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
