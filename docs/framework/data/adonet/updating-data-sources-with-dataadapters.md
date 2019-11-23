---
title: Aktualizace zdrojů dat pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 4a6e22352a309f9d624c6922abc531cb31a5baf1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736689"
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizace zdrojů dat pomocí adaptérů dat

Metoda `Update` <xref:System.Data.Common.DataAdapter> je volána k vyřešení změn z <xref:System.Data.DataSet> zpět do zdroje dat. Metoda `Update`, jako je například metoda `Fill`, přijímá jako argumenty instanci `DataSet`a nepovinný <xref:System.Data.DataTable> objekt nebo `DataTable` název. Instance `DataSet` je `DataSet` obsahující změny, které byly provedeny, a `DataTable` identifikuje tabulku, ze které se mají změny načíst. Pokud není zadán žádný `DataTable`, použije se první `DataTable` v `DataSet`.

Když zavoláte metodu `Update`, `DataAdapter` analyzuje provedené změny a spustí příslušný příkaz (INSERT, UPDATE nebo DELETE). Když `DataAdapter` narazí na změnu v <xref:System.Data.DataRow>, ke zpracování změny se použije <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>nebo <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>. Díky tomu můžete maximalizovat výkon aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a pokud je to možné, pomocí uložených procedur. Před voláním `Update`je nutné explicitně nastavit příkazy. Pokud je zavolána `Update` a příslušný příkaz pro konkrétní aktualizaci neexistuje (například není `DeleteCommand` pro odstraněné řádky), je vyvolána výjimka.

> [!NOTE]
> Pokud používáte SQL Server uložené procedury k úpravám nebo odstraňování dat pomocí `DataAdapter`, ujistěte se, že v definici uložené procedury nepoužíváte nastavení počet. To způsobí, že počet ovlivněných řádků vrátil hodnotu nula, kterou `DataAdapter` interpretuje jako konflikt souběžnosti. V tomto případě bude vyvolána <xref:System.Data.DBConcurrencyException>.

Parametry příkazu lze použít k určení vstupních a výstupních hodnot příkazu SQL nebo uložené procedury pro každý upravený řádek v `DataSet`. Další informace naleznete v tématu [parametry DataAdapter](dataadapter-parameters.md).

> [!NOTE]
> Je důležité pochopit rozdíl mezi odstraněním řádku v <xref:System.Data.DataTable> a odebráním řádku. Když zavoláte metodu `Remove` nebo `RemoveAt`, řádek se okamžitě odebere. Pokud předáte `DataTable` nebo `DataSet` `DataAdapter` a zavoláte `Update`, nebudou ovlivněny žádné odpovídající řádky ve zdroji dat back-endu. Když použijete metodu `Delete`, řádek zůstane v `DataTable` a je označený k odstranění. Pokud předáte `DataTable` nebo `DataSet` `DataAdapter` a volání `Update`, je odstraněn odpovídající řádek ve zdroji dat back-endu.

Pokud se vaše `DataTable` mapuje na nebo je vygenerována z jedné tabulky databáze, můžete využít výhod objektu <xref:System.Data.Common.DbCommandBuilder> k automatickému vygenerování `DeleteCommand`ch, `InsertCommand`a `UpdateCommand` objektů pro `DataAdapter`. Další informace najdete v tématu [generování příkazů pomocí CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapování hodnot na datovou sadu pomocí UpdatedRowSource

Můžete určit, jak budou hodnoty vrácené ze zdroje dat mapovány zpět na `DataTable` po volání metody aktualizace `DataAdapter`pomocí vlastnosti <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> objektu <xref:System.Data.Common.DbCommand>. Nastavením vlastnosti `UpdatedRowSource` na jednu z hodnot výčtu <xref:System.Data.UpdateRowSource> můžete určit, zda budou výstupní parametry vrácené příkazy `DataAdapter` ignorovány nebo aplikovány na změněný řádek v `DataSet`. Můžete také určit, zda byl první vrácený řádek (pokud existuje) použit pro změněný řádek v `DataTable`.

Následující tabulka popisuje různé hodnoty výčtu `UpdateRowSource` a způsob, jakým ovlivňují chování příkazu používaného s `DataAdapter`.

|Výčet UpdatedRowSource|Popis|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|Výstupní parametry a první řádek vrácené sady výsledků můžou být namapovány na změněný řádek v `DataSet`.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Pouze data v prvním řádku vrácené sady výsledků můžou být namapována na změněný řádek v `DataSet`.|
|<xref:System.Data.UpdateRowSource.None>|Všechny výstupní parametry nebo řádky vracené sady výsledků jsou ignorovány.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|Na změněný řádek v `DataSet`mohou být mapovány pouze výstupní parametry.|

Metoda `Update` vyřeší změny zpět do zdroje dat; ostatní klienti však mohli data ze zdroje dat od posledního vyplňování `DataSet`upravovat. Chcete-li aktualizovat `DataSet` aktuálními daty, použijte metodu `DataAdapter` a `Fill`. Do tabulky budou přidány nové řádky a aktualizované informace budou zahrnuty do stávajících řádků. Metoda `Fill` určuje, zda bude přidán nový řádek, nebo bude aktualizován existující řádek tím, že prozkoumá hodnoty primárního klíče řádků v `DataSet` a řádky vracené `SelectCommand`. Pokud metoda `Fill` narazí na hodnotu primárního klíče pro řádek v `DataSet`, který se shoduje s hodnotou primárního klíče z řádku v výsledkůch vrácených `SelectCommand`, aktualizuje stávající řádek informacemi z řádku vráceného `SelectCommand` a nastaví <xref:System.Data.DataRow.RowState%2A> stávajícího řádku na `Unchanged`. Pokud řádek vrácený `SelectCommand` má hodnotu primárního klíče, která neodpovídá žádné hodnotě primárního klíče řádků v `DataSet`, metoda `Fill` přidá nový řádek s `RowState` `Unchanged`.

> [!NOTE]
> Pokud `SelectCommand` vrátí výsledky VNĚJŠÍho spojení, `DataAdapter` nenastaví `PrimaryKey` hodnotu pro výsledný `DataTable`. Aby bylo zajištěno, že duplicitní řádky budou správně vyřešeny, je nutné definovat `PrimaryKey` sami. Další informace najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).

Chcete-li zpracovat výjimky, které mohou nastat při volání metody `Update`, můžete použít událost `RowUpdated` k reakci na chyby aktualizace řádků, jak se vyskytují (viz [zpracování událostí DataAdapter](handling-dataadapter-events.md)), nebo můžete nastavit `DataAdapter.ContinueUpdateOnError` na `true` před voláním `Update`a reagovat na informace o chybách uložené ve vlastnosti `RowError` určitého řádku po dokončení aktualizace (viz [informace o chybě řádku](./dataset-datatable-dataview/row-error-information.md)).

> [!NOTE]
> Volání `AcceptChanges` na `DataSet`, `DataTable`nebo `DataRow` způsobí, že všechny `Original` hodnoty pro `DataRow` budou přepsány hodnotami `Current` pro `DataRow`. Pokud se hodnoty polí, které identifikují řádek jako jedinečné, změnily po volání `AcceptChanges` hodnoty `Original` již nebudou odpovídat hodnotám ve zdroji dat. `AcceptChanges` se při volání metody aktualizace `DataAdapter`nazývá automaticky pro každý řádek. Původní hodnoty můžete zachovat během volání metody Update tak, že nejprve nastavíte vlastnost `AcceptChangesDuringUpdate` `DataAdapter` na hodnotu false nebo vytvoříte obslužnou rutinu události pro událost `RowUpdated` a nastavíte <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> na <xref:System.Data.UpdateStatus.SkipCurrentRow>. Další informace najdete v tématech [sloučení obsahu datových sad](./dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování událostí DataAdapter](handling-dataadapter-events.md).

## <a name="example"></a>Příklad

Následující příklady ukazují, jak provést aktualizace upravených řádků explicitním nastavením `UpdateCommand` `DataAdapter` a voláním metody `Update`. Všimněte si, že parametr zadaný v klauzuli WHERE příkazu UPDATE je nastaven na použití `Original` hodnoty `SourceColumn`. To je důležité, protože hodnota `Current` mohla být upravena a nemusí odpovídat hodnotě ve zdroji dat. Hodnota `Original` je hodnota, která byla použita k naplnění `DataTable` ze zdroje dat.

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a>Sloupce AutoIncrement

Pokud tabulky ze zdroje dat mají automatické přírůstkové sloupce, sloupce můžete vyplnit v `DataSet` buď vrácením hodnoty automatického zvýšení jako výstupní parametr uložené procedury a mapováním na sloupec v tabulce, vrácením hodnoty AutoIncrement v prvním řádku výsledné sady vrácené uloženou procedurou nebo příkazem jazyka SQL, nebo pomocí `RowUpdated` události `DataAdapter` k provedení dalšího příkazu SELECT. Další informace a příklad najdete v tématu [načtení hodnot identity nebo Autonumber Values](retrieving-identity-or-autonumber-values.md).

## <a name="ordering-of-inserts-updates-and-deletes"></a>Řazení vložení, aktualizací a odstranění

V mnoha případech je důležité pořadí, ve kterém jsou změny provedené prostřednictvím `DataSet` odesílány zdroji dat. Například pokud je hodnota primárního klíče pro existující řádek aktualizována a nový řádek byl přidán s novou hodnotou primárního klíče jako cizí klíč, je důležité zpracovat aktualizaci před vložením.

Metodu `Select` `DataTable` můžete použít k vrácení pole `DataRow`, které odkazuje pouze na řádky s konkrétním `RowState`. Pak můžete předávat vrácené `DataRow` pole do `Update` metody `DataAdapter` pro zpracování upravených řádků. Zadáním podmnožiny řádků, které se mají aktualizovat, můžete řídit pořadí, ve kterém se zpracují vložení, aktualizace a odstranění.

## <a name="example"></a>Příklad

Následující kód například zajistí, že se odstraněné řádky tabulky zpracovávají jako první, pak aktualizované řádky a vložené řádky.

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Použití DataAdapter k načtení a aktualizaci dat

K načtení a aktualizaci dat lze použít modul DataAdapter.

- Ukázka používá DataAdapter. AcceptChangesDuringFill ke klonování dat v databázi. Pokud je vlastnost nastavena na hodnotu false, při vyplňování tabulky není volána metoda AcceptChanges a nově přidané řádky jsou zpracovány jako vložené řádky. Ukázka proto používá tyto řádky k vložení nových řádků do databáze.

- Ukázky používají DataAdapter. vlastnosti TableMappings k definování mapování mezi zdrojovou tabulkou a DataTable.

- Ukázka používá DataAdapter. FillLoadOption k určení toho, jak adaptér vyplní objekt DataTable z DbDataReader. Při vytváření objektu DataTable můžete zapsat data pouze z databáze do aktuální verze nebo původní verze nastavením vlastnosti jako LoadOption. Upsert nebo LoadOption. PreserveChanges.

- Ukázka také aktualizuje tabulku pomocí objekt DbDataAdapter. UpdateBatchSize a provede operace dávkového zpracování.

Před kompilací a spuštěním ukázky je třeba vytvořit ukázkovou databázi:

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

C#a Visual Basic projekty s touto ukázkou kódu najdete v [ukázkách kódu pro vývojáře](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Stavy řádků a verze řádků](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [Metody AcceptChanges a RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Slučování obsahu datové sady](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Načítání hodnot identity nebo automatického číslování](retrieving-identity-or-autonumber-values.md)
- [Přehled ADO.NET](ado-net-overview.md)
