---
title: Aktualizace zdrojů dat pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 96a57e14d27788786cd4cf10c0000e8c2a125faa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791269"
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizace zdrojů dat pomocí adaptérů dat
Metoda je volána k vyřešení změn z zpátkynazdrojdat.<xref:System.Data.DataSet> <xref:System.Data.Common.DataAdapter> `Update` `Fill` `DataSet` <xref:System.Data.DataTable> Metoda, jako je například metoda, přijímá jako argumenty instanci a, což je nepovinný objekt nebo `DataTable` název. `Update` Instance je, která obsahuje změny, které byly provedeny, a `DataTable` identifikuje tabulku, ze které se mají změny načíst. `DataSet` `DataSet` Pokud není zadán, použije se první `DataTable` v `DataSet`. `DataTable`  
  
 Když zavoláte `Update` metodu `DataAdapter` , analyzuje provedené změny a provede příslušný příkaz (INSERT, Update nebo Delete). <xref:System.Data.DataRow> <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>Když dojde ke změně<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, používá, nebo<xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> ke zpracování změny. `DataAdapter` Díky tomu můžete maximalizovat výkon aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a pokud je to možné, pomocí uložených procedur. Před voláním `Update`je nutné explicitně nastavit příkazy. Pokud `Update` je volána a příslušný příkaz pro konkrétní aktualizaci neexistuje (například ne `DeleteCommand` pro odstraněné řádky), je vyvolána výjimka.  
  
> [!NOTE]
> Pokud používáte SQL Server uložené procedury k úpravám nebo odstraňování dat pomocí `DataAdapter`, ujistěte se, že v definici uložené procedury nepoužijete nastavení počet. To způsobí, že počet ovlivněných řádků vrátil hodnotu nula, což `DataAdapter` interpretuje jako konflikt souběžnosti. V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.  
  
 Parametry příkazu lze použít k určení vstupních a výstupních hodnot příkazu SQL nebo uložené procedury pro každý upravený řádek v `DataSet`. Další informace naleznete v tématu [parametry DataAdapter](dataadapter-parameters.md).  
  
> [!NOTE]
> Je důležité pochopit rozdíl mezi odstraněním řádku v <xref:System.Data.DataTable> a odebráním řádku. Při volání `Remove` metody nebo `RemoveAt` se řádek odebere okamžitě. Pokud pak předáte `DataTable` nebo `DataSet` k volání `Update`a, nebudou ovlivněny žádné odpovídající řádky ve zdroji dat back- `DataAdapter` end. Když použijete `Delete` metodu, řádek zůstane `DataTable` v a je označený k odstranění. Pokud `DataTable` `DataSet` předáte volánímetody`Update`a a a, je odstraněn odpovídající řádek ve zdroji dat back-endu. `DataAdapter`  
  
 Pokud vaše `DataTable` mapy nebo jsou vygenerovány z jedné tabulky databáze, můžete využít výhod `UpdateCommand` <xref:System.Data.Common.DbCommandBuilder> `DeleteCommand`objektu pro automatické generování objektů, `InsertCommand`a pro `DataAdapter`. Další informace najdete v tématu [generování příkazů pomocí CommandBuilders](generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapování hodnot na datovou sadu pomocí UpdatedRowSource  
 Můžete určit, jak budou hodnoty vrácené ze zdroje dat `DataTable` mapovány zpět na následující volání metody `DataAdapter`aktualizace pro, <xref:System.Data.Common.DbCommand> pomocí <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnosti objektu. Nastavením `UpdatedRowSource` vlastnosti na jednu <xref:System.Data.UpdateRowSource> z hodnot výčtu můžete určit, zda budou `DataAdapter` výstupní parametry vracené příkazy ignorovány `DataSet`nebo aplikovány na změněný řádek v. Můžete také určit, zda byl první vrácený řádek (pokud existuje) použit pro změněný řádek v `DataTable`.  
  
 V následující tabulce jsou popsány různé hodnoty `UpdateRowSource` výčtu a jejich vliv na chování příkazu používaného `DataAdapter`s.  
  
|Výčet UpdatedRowSource|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Výstupní parametry a první řádek vrácené sady výsledků můžou být namapovány na změněný řádek v `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Pouze data v prvním řádku vrácené sady výsledků dotazu mohou být mapována na změněný řádek v `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Všechny výstupní parametry nebo řádky vracené sady výsledků jsou ignorovány.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Pouze výstupní parametry mohou být mapovány na změněný řádek v `DataSet`.|  
  
 Metoda vyřeší vaše změny zpátky na zdroj dat. ostatní klienti však mohou data ze zdroje dat od posledního `DataSet`vyplňování upravovat. `Update` Chcete-li `DataSet` aktualizovat aktuální data, `DataAdapter` použijte metodu a `Fill` . Do tabulky budou přidány nové řádky a aktualizované informace budou zahrnuty do stávajících řádků. Metoda určuje, zda bude přidán nový řádek, nebo bude aktualizován existující řádek tím, že prozkoumá hodnoty primárního klíče řádků `DataSet` v řádcích a řádky vrácené `SelectCommand`. `Fill` Pokud metoda narazí na hodnotu primárního klíče pro řádek `DataSet` v, který se shoduje s hodnotou primárního klíče z řádku v výsledkůch vrácených `SelectCommand`, aktualizuje stávající řádek informacemi z řádku vráceného `Fill` `SelectCommand`a nastaví <xref:System.Data.DataRow.RowState%2A> existující řádek na `Unchanged`. Pokud řádek `SelectCommand` vrácený hodnotou má primární klíč, který se neshoduje s žádnou z hodnot primárního klíče `Unchanged` `DataSet`v řádcích v, `Fill` metoda přidá nový řádek s hodnotou `RowState` .  
  
> [!NOTE]
> Vrátí-li funkce výsledky vnějšího spojení `DataAdapter` , nebude `PrimaryKey` hodnota pro výsledný `DataTable`výsledek nastavena. `SelectCommand` Aby bylo zajištěno `PrimaryKey` , že duplicitní řádky budou správně vyřešeny, je nutné definovat sami sebe. Další informace najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Chcete-li zpracovat výjimky, které mohou nastat `Update` při volání metody, můžete `RowUpdated` použít událost k reakci na chyby aktualizace řádků při jejich výskytu (viz [zpracování událostí DataAdapter](handling-dataadapter-events.md)) nebo můžete nastavit na `DataAdapter.ContinueUpdateOnError` `true` hodnotu před volání `Update`a reakce na informace o chybách uložené `RowError` ve vlastnosti určitého řádku po dokončení aktualizace (viz [informace o chybě řádku](./dataset-datatable-dataview/row-error-information.md)).  
  
 **Poznámka:** Volání `AcceptChanges` `DataTable` `DataRow` `DataRow`na,, `Original` nebo`Current` způsobí, že všechny hodnoty pro a budou přepsány hodnotami pro. `DataRow` `DataSet` Pokud byly změněny hodnoty polí, které identifikují řádek jako jedinečné, potom po volání `AcceptChanges` `Original` hodnoty již nebudou hodnoty ve zdroji dat odpovídat. `AcceptChanges`je volána automaticky pro každý řádek při volání metody `DataAdapter`aktualizace pro. Původní hodnoty můžete zachovat během volání metody aktualizace – nejprve nastavte `AcceptChangesDuringUpdate` vlastnost `DataAdapter` na hodnotu false nebo vytvořením obslužné rutiny události pro `RowUpdated` událost a nastavením <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow>na. Další informace najdete v tématech [sloučení obsahu datových sad](./dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování událostí DataAdapter](handling-dataadapter-events.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak provést aktualizace upravených řádků explicitně nastavením `UpdateCommand` `DataAdapter` typu a a voláním `Update` metody. Všimněte si, že parametr zadaný v klauzuli WHERE příkazu Update je nastaven na použití `Original` hodnoty. `SourceColumn` To je důležité, protože `Current` hodnota je možná upravená a nemusí odpovídat hodnotě ve zdroji dat. Hodnota je hodnota, která byla použita k `DataTable` naplnění zdroje dat. `Original`  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>Sloupce AutoIncrement  
 Pokud tabulky ze zdroje dat mají automatické přírůstkové sloupce, můžete sloupce `DataSet` vyplnit buď tak, že hodnotu automatického zvýšení nastavíte jako výstupní parametr uložené procedury a mapování na sloupec v tabulce, a to vrácením automatické zvýšení hodnoty v prvním řádku sady výsledků vrácené uloženou procedurou nebo příkazem jazyka SQL nebo pomocí `RowUpdated` události `DataAdapter` ke spuštění dalšího příkazu SELECT. Další informace a příklad najdete v tématu [načtení hodnot identity nebo Autonumber Values](retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Řazení vložení, aktualizací a odstranění  
 V mnoha případech je důležité pořadí, ve kterém se změny provedou `DataSet` při odeslání do zdroje dat. Například pokud je hodnota primárního klíče pro existující řádek aktualizována a nový řádek byl přidán s novou hodnotou primárního klíče jako cizí klíč, je důležité zpracovat aktualizaci před vložením.  
  
 Můžete použít `Select` metodu `DataTable` pro vrácení `DataRow` pole, které odkazuje pouze na řádky s určitým `RowState`objektem. Pak můžete předat vrácené `DataRow` pole `Update` metodě `DataAdapter` pro zpracování změněných řádků. Zadáním podmnožiny řádků, které se mají aktualizovat, můžete řídit pořadí, ve kterém se zpracují vložení, aktualizace a odstranění.  
  
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
dataAdapater.Update(table.Select(Nothing, Nothing, _  
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
