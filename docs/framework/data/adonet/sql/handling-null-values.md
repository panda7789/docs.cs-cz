---
title: "Zpracování hodnot Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f29cbd51c036ecc15306f67fdd32dee6a4f1b68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="handling-null-values"></a>Zpracování hodnot Null
Hodnotu null v relační databázi se používá, pokud je hodnota ve sloupci neznámý nebo chybí. Null není prázdný řetězec (pro datové typy znaků nebo data a času) ani hodnotu nula (pro číselné datové typy). Specifikace ANSI SQL-92 stavy s hodnotou null musí být stejné pro všechny typy dat, tak, aby všechny hodnoty Null zpracovává konzistentně. <xref:System.Data.SqlTypes> Obor názvů obsahuje hodnotu null sémantiku implementací <xref:System.Data.SqlTypes.INullable> rozhraní. Každý dat typy v <xref:System.Data.SqlTypes> má svou vlastní `IsNull` vlastnost a `Null` hodnotu, která lze přiřadit k instanci daného datového typu.  
  
> [!NOTE]
>  Podpora rozhraní .NET Framework verze 2.0 zavedená pro typy s možnou hodnotou Null, která umožňuje programátorům typ hodnoty k reprezentaci všech hodnot základní typ rozšíření. Tyto typy s možnou hodnotou Null CLR představují instanci <xref:System.Nullable> struktura. Tato funkce je obzvláště užitečná při hodnota typy jsou do pole a nezabalený, pokud rozšířené kompatibilitu s typy objektů. Typy s možnou hodnotou Null CLR nejsou určeny pro úložiště databáze hodnoty Null, protože ANSI SQL null není chovají stejně jako `null` odkaz (nebo `Nothing` v jazyce Visual Basic). Pro práci s hodnotami null ANSI SQL databáze, použijte <xref:System.Data.SqlTypes> hodnoty Null místo <xref:System.Nullable>. Další informace o práci s CLR najdete v části typy s možnou hodnotou Null v jazyce Visual Basic [typy s možnou hodnotou Null hodnot](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)a C# najdete v tématu [pomocí typy s možnou hodnotou Null](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Hodnoty Null a s hodnotou tři logiky  
 Povolení hodnoty null v definicích sloupce zavádí s hodnotou tři logiku do vaší aplikace. Porovnání lze vyhodnotit na jednu ze tří podmínek:  
  
-   Hodnota TRUE  
  
-   False  
  
-   Neznámé  
  
 Protože null se považuje za neznámý, ve srovnání s navzájem dvě hodnoty null, se nepovažují za stejná. Pomocí aritmetických operátorů, pokud je některý z operandy hodnotu null ve výrazech, výsledkem je null také.  
  
## <a name="nulls-and-sqlboolean"></a>Hodnoty Null a SqlBoolean  
 Porovnání mezi všechny <xref:System.Data.SqlTypes> vrátí <xref:System.Data.SqlTypes.SqlBoolean>. `IsNull` Funkce pro každou `SqlType` vrátí <xref:System.Data.SqlTypes.SqlBoolean> a slouží ke kontrole hodnot null. Následující pravdivosti tabulky zobrazit, jak AND, OR a ne operátory funkce případě hodnotu null. (T = true, F = false a U = Neznámý, nebo hodnotu null.)  
  
 ![Tabulka pravdivosti](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>Principy možnosti ANSI_NULLS  
 <xref:System.Data.SqlTypes>poskytuje stejnou sémantiku jako možnosti ANSI_NULLS nastavena na v systému SQL Server. Všech aritmetických operátorů (+, -, *, /, %), bitové operátory (~ &, &#124;), a většina funkce vrátí hodnotu null, pokud je některý z operandy nebo argumenty null, s výjimkou vlastnost `IsNull`.  
  
 Standardu ANSI SQL-92 nepodporuje *columnName* = NULL v klauzuli WHERE. V systému SQL Server možnosti ANSI_NULLS Určuje, jak výchozí možnost použití hodnoty Null v databázi a vyhodnocení porovnání s hodnotami null. Pokud ANSI_NULLS je zapnuté (výchozí), musí být operátoru IS NULL použít ve výrazech při testování hodnoty null. Například na toto porovnání vždy vypočítá Neznámý ANSI_NULLS je na:  
  
```  
colname > NULL  
```  
  
 Porovnání proměnné obsahující hodnotu null také vypočítá neznámý:  
  
```  
colname > @MyVariable  
```  
  
 Predikát je NULL nebo je NOT NULL použijte k testování pro hodnotu null. Složitost to můžete přidat do klauzule WHERE. Například TerritoryID sloupec v tabulce Zákazník AdventureWorks povoluje hodnoty null. Pokud příkaz SELECT k testování hodnot null kromě ostatní, musí obsahovat predikát je NULL:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Pokud nastavíte ANSI_NULLS v systému SQL Server, můžete vytvořit výrazy, které používají operátor rovnosti k porovnání na hodnotu null. Nelze však zabránit jiné připojení z nastavení null možností pro toto připojení. Použití IS NULL k testování hodnot null vždy funguje, bez ohledu na nastavení ANSI_NULLS pro připojení.  
  
 Nastavení ANSI_NULLS vypnout nepodporuje `DataSet`, který následuje vždy standardu ANSI SQL-92 pro zpracování hodnot null ve <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Přiřazení hodnoty Null  
 Hodnoty Null jsou speciální a jejich úložiště a přiřazení sémantiku se mezi systémy jiného typu a úložných systémů liší. A `Dataset` je určen k použití s různými systémy typu a úložiště.  
  
 Tato část popisuje null sémantiky pro přiřazení hodnoty null do <xref:System.Data.DataColumn> v <xref:System.Data.DataRow> mezi systémy jiného typu.  
  
 `DBNull.Value`  
 Je platná pro toto přiřazení `DataColumn` libovolného typu. Pokud typ implementuje `INullable`, `DBNull.Value` je má odpovídající silného typu hodnotu Null.  
  
 `SqlType.Null`  
 Všechny <xref:System.Data.SqlTypes> implementovat datové typy `INullable`. Pokud hodnotu silného typu null můžete převést na datový typ sloupce pomocí operátory implicitního přetypování, by měl projít přiřazení. V opačném případě je vyvolána výjimka neplatné přetypování.  
  
 `null`  
 Pokud "null" není platnou hodnotou pro v dané `DataColumn` datový typ, je do příslušné má `DbNull.Value` nebo `Null` přidružené `INullable` typu (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 Pro UDT sloupce jsou hodnoty Null vždy uloženy na základě typu přidružené `DataColumn`. Podívejte se UDT přidružené `DataColumn` který neimplementuje `INullable` při jeho dílčí třída nepodporuje. V takovém případě pokud má přiřazenou hodnotu silného typu null přidružené odvozené třídy, bude uložena jako netypové `DbNull.Value`, protože je vždy v souladu s sloupci DataColumn datový typ úložiště hodnotu null.  
  
> [!NOTE]
>  `Nullable<T>` Nebo <xref:System.Nullable> struktura aktuálně nepodporuje `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Více přiřazení sloupec (řádek)  
 `DataTable.Add`, `DataTable.LoadDataRow`, nebo jiná rozhraní API, které přijímají <xref:System.Data.DataRow.ItemArray%2A> , získá namapovaná na řádek, mapy null na sloupci DataColumn výchozí hodnotu. Pokud obsahuje objekt v poli `DbNull.Value` nebo se použijí jeho protějšek silného typu, stejná pravidla jak je popsáno výše.  
  
 Kromě toho platí následující pravidla pro instanci `DataRow.["columnName"]` null přiřazení:  
  
1.  Výchozí hodnota *výchozí* hodnota je `DbNull.Value` pro všechny kromě silného typu null sloupce tam, kde je odpovídající silně typované hodnotu null.  
  
2.  Hodnoty Null se nikdy zapisují během serializace za účelem souborů XML (jako "xsi: nil").  
  
3.  Všechny hodnoty null, včetně výchozí hodnoty, jsou vždy zapsána při serializaci do formátu XML. To je rozdíl oproti sémantiku XSD/XML, kde je explicitní hodnotu null (xsi: nil) a výchozí hodnota je implicitní (Pokud není přítomný v XML, ověřuje analyzátor můžete ho získat prostřednictvím přidruženému schématu XSD). Jako opak platí pro `DataTable`: hodnota null je implicitní a explicitní je výchozí hodnota.  
  
4.  Všechny chybějící hodnoty sloupce pro čtení z vstup XML řádky jsou přiřadit hodnotu NULL. Řádky, které jsou vytvořené pomocí <xref:System.Data.DataTable.NewRow%2A> nebo podobné metody jsou přiřazeny sloupci DataColumn výchozí hodnotu.  
  
5.  <xref:System.Data.DataRow.IsNull%2A> Metoda vrátí `true` pro obě `DbNull.Value` a `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Přiřazení hodnoty Null  
 Výchozí hodnota pro některý <xref:System.Data.SqlTypes> instance je null.  
  
 Hodnoty Null v <xref:System.Data.SqlTypes> jsou specifické pro typ a nemůže být reprezentovaná jednu hodnotu, jako například `DbNull`. Použití `IsNull` vlastnost zkontrolujte hodnoty Null.  
  
 Hodnoty Null lze přiřadit k <xref:System.Data.DataColumn> jak je znázorněno v následujícím příkladu kódu. Můžete přímo přiřadit hodnoty null do `SqlTypes` proměnné bez vyvolání k výjimce.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří <xref:System.Data.DataTable> s dva sloupce, které jsou definované jako <xref:System.Data.SqlTypes.SqlInt32> a <xref:System.Data.SqlTypes.SqlString>. Kód přidá jeden řádek známé hodnoty, jeden řádek Null hodnoty a pak provádí iteraci <xref:System.Data.DataTable>, přiřazení hodnoty k proměnné a zobrazení výstupu v okně konzoly.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Tento příklad zobrazí následující výsledky:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porovnání hodnoty Null s SqlTypes a typy CLR  
 Při porovnávání hodnoty null, je důležité si uvědomit rozdíl mezi způsob, jakým `Equals` metoda vyhodnotí hodnoty null v <xref:System.Data.SqlTypes> ve srovnání s způsob, jak to funguje s typy CLR. Všechny <xref:System.Data.SqlTypes> `Equals` metody používají sémantiku databáze pro vyhodnocení hodnoty null: Pokud má jednu nebo obě hodnoty hodnotu null, je výsledkem porovnávání vypočítá hodnotu null. Na druhé straně pomocí modulu CLR `Equals` metoda na dva <xref:System.Data.SqlTypes> předá hodnotu true, pokud jsou obě hodnotu null. Tento údaj zohledňuje rozdíl mezi použitím metody instance například modulu CLR `String.Equals` metoda a pomocí metody statické nebo sdílené `SqlString.Equals`.  
  
 Následující příklad ukazuje rozdíl mezi výsledky `SqlString.Equals` metoda a `String.Equals` metoda když každý předána pár hodnoty null a poté páru prázdné řetězce.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Data serveru SQL typy a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
