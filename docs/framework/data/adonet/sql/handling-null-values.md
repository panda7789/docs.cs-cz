---
title: Zpracování hodnot null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 0d200ad35d3ab56bf97114b51b4f7fcc898eecdf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332141"
---
# <a name="handling-null-values"></a>Zpracování hodnot null
Hodnotu null v relační databázi se používá při neznámý nebo chybějící hodnota ve sloupci. Hodnota null není prázdný řetězec (pro datové typy znaků nebo datum a čas) ani nulovou hodnotu (pro číselné datové typy). Specifikace ANSI SQL-92 státy, s hodnotou null musí být stejný pro všechny typy dat, tak, aby všechny hodnoty Null se zpracovávají konzistentně. <xref:System.Data.SqlTypes> Obor názvů poskytuje sémantika s hodnotou null implementací <xref:System.Data.SqlTypes.INullable> rozhraní. Každý dat typy, které do <xref:System.Data.SqlTypes> má vlastní `IsNull` vlastnost a `Null` hodnotu, která je možné přiřadit do instance datového typu.  
  
> [!NOTE]
>  Podporu rozhraní .NET Framework verze 2.0 zavedl pro typy připouštějící hodnotu Null, které umožňují programátorům rozšíření typu hodnoty k reprezentaci všech hodnot ze základního typu. Tyto typy s možnou hodnotou Null CLR představují instance <xref:System.Nullable> struktury. Tato funkce je obzvláště užitečná při hodnotu v poli a rozbalit, poskytující typy rozšířeného kompatibilitu s typy objektů. CLR typy s možnou hodnotou Null nejsou určené pro úložiště databáze hodnoty Null, protože ANSI SQL null se nechová stejně jako `null` odkaz (nebo `Nothing` v jazyce Visual Basic). Pro práci s hodnotami null ANSI SQL databáze, použijte <xref:System.Data.SqlTypes> hodnoty Null spíše než <xref:System.Nullable>. Další informace o práci s CLR typy připouštějící hodnotu Null v jazyce Visual Basic naleznete v tématu [hodnotové typy s možnou hodnotou Null](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)a C# najdete v tématu [typy připouštějící hodnotu Null pomocí](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Hodnoty Null a s hodnotou tři logiky  
 Povolujících hodnoty null v definicích sloupce zavádí tři vracející logiky do vaší aplikace. Porovnání lze vyhodnotit na jednu ze tří podmínek:  
  
-   Pravda  
  
-   False  
  
-   Neznámé  
  
 Protože null se považuje za neznámý, dvou hodnot null ve srovnání s vzájemně se nepovažují za stejné. Výrazy v použití aritmetických operátorů, pokud žádný z operandů je null, výsledek je null a.  
  
## <a name="nulls-and-sqlboolean"></a>Hodnoty Null a SqlBoolean  
 Porovnání mezi <xref:System.Data.SqlTypes> vrátí <xref:System.Data.SqlTypes.SqlBoolean>. `IsNull` Funkce pro každou `SqlType` vrátí <xref:System.Data.SqlTypes.SqlBoolean> a je možné pro kontrolu hodnot null. Následující pravdy tabulky zobrazit jak AND, OR a ne operátory funkce za přítomnosti hodnotu null. (T = true, F = false a U = Neznámý, nebo hodnotu null.)  
  
 ![Tabulka pravdy](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>Principy možnosti ANSI_NULLS  
 <xref:System.Data.SqlTypes> poskytuje stejnou sémantiku jako v případě možnosti ANSI_NULLS je nastavena na v systému SQL Server. Všechny aritmetické operátory (+, -, *, /, %), bitové operátory (~ &, &#124;), a většina funkcí vracet hodnotu null, pokud některý z operandů nebo argumenty má hodnotu null, s výjimkou vlastnost `IsNull`.  
  
 Standard ANSI SQL-92 nepodporuje *Názevsloupce* = NULL v klauzuli WHERE. V systému SQL Server určuje možnosti ANSI_NULLS i výchozí možnosti použití hodnoty Null v databázi a hodnocení porovnání proti hodnoty null. Pokud ANSI_NULLS je zapnuté (výchozí), operátoru IS NULL musí použít ve výrazech při testování hodnot null. Například následující porovnání vždy poskytuje Neznámý ANSI_NULLS je na:  
  
```  
colname > NULL  
```  
  
 Porovnání proměnné obsahující hodnotu null také poskytuje neznámý:  
  
```  
colname > @MyVariable  
```  
  
 Test pro hodnotu null, použijte predikát IS NULL a IS NOT NULL. To může přidání složitosti do klauzule WHERE. Například TerritoryID sloupec v tabulce zákazníků AdventureWorks povoluje hodnoty null. Pokud příkaz SELECT pro testování hodnot null kromě dalších, musí obsahovat predikát je NULL:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Pokud nastavíte ANSI_NULLS v systému SQL Server, můžete vytvořit výrazů, které používají operátor rovnosti má být porovnán s hodnotou null. Nelze však zabránit různých připojení z nastavení možností hodnoty null pro toto připojení. Použití IS NULL pro testování hodnot null vždy funguje, bez ohledu na nastavení ANSI_NULLS pro připojení.  
  
 Nastavení ANSI_NULLS vypnout nepodporuje `DataSet`, která vždy následuje standardu ANSI SQL-92 pro zpracování hodnot null ve <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Přiřazení hodnoty Null  
 Hodnoty Null jsou speciální a jejich úložiště a přiřazování sémantika lišit napříč jiný typ systémy a systémy úložišť. A `Dataset` je určen pro použití s různými systémy typu a úložiště.  
  
 Tato část popisuje sémantika s hodnotou null pro přiřazení hodnoty null <xref:System.Data.DataColumn> v <xref:System.Data.DataRow> napříč systémy jiného typu.  
  
 `DBNull.Value`  
 Toto přiřazení není platná pro `DataColumn` libovolného typu. Pokud tento typ implementuje `INullable`, `DBNull.Value` je převést na odpovídající hodnotu silného typu hodnotu Null.  
  
 `SqlType.Null`  
 Všechny <xref:System.Data.SqlTypes> datové typy implementovat `INullable`. Pokud hodnotu silného typu null lze převést na datový typ sloupce pomocí operátorů implicitní přetypování, by měl projít přiřazení. V opačném případě je vyvolána výjimka neplatné přetypování.  
  
 `null`  
 Pokud "null" je platná hodnota pro daný `DataColumn` datový typ, to je převést na odpovídající `DbNull.Value` nebo `Null` přidružené `INullable` typ (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 UDT sloupců, hodnoty Null jsou vždy uloženy založené na typ přidružený k `DataColumn`. Podívejte se na UDT přidružené `DataColumn` , který neimplementuje `INullable` při jeho dílčí třída. V takovém případě pokud je přiřazený silného typu null hodnotu přidruženou k odvozené třídě, uloží se jako netypové `DbNull.Value`, protože je vždy konzistentní s datovým typem objekt DataColumn úložiště hodnotu null.  
  
> [!NOTE]
>  `Nullable<T>` Nebo <xref:System.Nullable> struktury se momentálně nepodporuje ve `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Více přiřazení sloupce (řádků)  
 `DataTable.Add`, `DataTable.LoadDataRow`, nebo jiná rozhraní API, které přijímají <xref:System.Data.DataRow.ItemArray%2A> , který získá namapována na řádek, mapování objekt DataColumn výchozí hodnotu "null". Pokud objekt v poli obsahuje `DbNull.Value` nebo jeho protějšek silného typu, stejná pravidla jak je popsáno výše jsou použity.  
  
 Kromě toho platí následující pravidla pro instanci `DataRow.["columnName"]` přiřazení s hodnotou null:  
  
1. Výchozí hodnota *výchozí* hodnotu `DbNull.Value` pro všechny s výjimkou silného typu null sloupce, ve kterém je příslušný silného typu hodnotu null.  
  
2. Hodnoty Null jsou zapsané nikdy během serializace za účelem soubory XML (jako "xsi: nil").  
  
3. Všechny nenulové hodnoty, včetně výchozích hodnot, jsou vždy zapsané při serializaci do formátu XML. To je rozdíl oproti sémantiku XSD/XML, kde je explicitní hodnotu null (xsi: nil) a výchozí hodnota je implicitní (Pokud není k dispozici ve formátu XML, ověřování analyzátoru můžete ho získat z přidružené schéma XSD). Opak platí pro `DataTable`: hodnota null je implicitní a výchozí hodnota je explicitní.  
  
4. Všechny chybějící hodnoty sloupce pro čtení z XML vstupní řádky se přiřadit hodnotu NULL. Řádky, které jsou vytvořené pomocí <xref:System.Data.DataTable.NewRow%2A> nebo podobné metody jsou přiřazeny výchozí hodnota objekt DataColumn.  
  
5. <xref:System.Data.DataRow.IsNull%2A> Vrátí metoda `true` pro obě `DbNull.Value` a `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Přiřazení hodnoty Null  
 Výchozí hodnota pro všechny <xref:System.Data.SqlTypes> instance má hodnotu null.  
  
 Null v <xref:System.Data.SqlTypes> platí pro konkrétní typ a nemůže být reprezentována jednu hodnotu, jako například `DbNull`. Použití `IsNull` vlastnost ke kontrole hodnoty Null.  
  
 Hodnoty Null lze přiřadit k <xref:System.Data.DataColumn> jak je znázorněno v následujícím příkladu kódu. Můžete přímo přiřadit hodnoty null `SqlTypes` proměnné bez vyvolání výjimky.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří <xref:System.Data.DataTable> se dvěma sloupci, které jsou definované jako <xref:System.Data.SqlTypes.SqlInt32> a <xref:System.Data.SqlTypes.SqlString>. Kód přidá jeden řádek známé hodnoty, jeden řádek null hodnoty a poté iteruje skrz <xref:System.Data.DataTable>, přiřazení hodnoty proměnné a zobrazuje výstup v okně konzoly.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Tento příklad zobrazuje následující výsledky:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porovnání hodnoty Null s SqlTypes a typy CLR  
 Při porovnání hodnoty null, je důležité pochopit rozdíl mezi způsob, jakým `Equals` metoda vyhodnocuje hodnoty null v <xref:System.Data.SqlTypes> mezi tak, jak to funguje s typy CLR. Všechny <xref:System.Data.SqlTypes> `Equals` metody používají sémantiku databáze za vaše rozhodnutí vyzkoušet hodnoty null: Pokud jeden nebo oba z hodnoty null, porovnání vrací hodnotu null. Na druhé straně pomocí CLR `Equals` metoda na dvou <xref:System.Data.SqlTypes> předá hodnotu true, pokud jsou obě hodnotu null. To odpovídá rozdíl mezi použitím metodu instance, jako je například CLR `String.Equals` metoda a pomocí metody statického/shared `SqlString.Equals`.  
  
 Následující příklad ukazuje rozdíl mezi výsledky `SqlString.Equals` metoda a `String.Equals` metoda každý je předána dvojici hodnot null a pak pár prázdné řetězce.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kód vytvoří následující výstup:  
  
```  
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

- [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
