---
title: Aktualizace zdrojů dat pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 6989204fac64fc18cae547e272f6d52004c3af69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728827"
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizace zdrojů dat pomocí adaptérů dat
`Update` Metodu <xref:System.Data.Common.DataAdapter> je volána k vyřešení změn z <xref:System.Data.DataSet> zpět do zdroje dat. `Update` Metoda, třeba `Fill` metoda, přebírá jako argumenty instance `DataSet`a volitelně <xref:System.Data.DataTable> objektu nebo `DataTable` název. `DataSet` Instance je `DataSet` , která obsahuje změny, které byly provedeny, a `DataTable` identifikuje tabulky, ze kterých se mají obnovit změny. Pokud ne `DataTable` je zadán první `DataTable` v `DataSet` se používá.  
  
 Při volání `Update` metody `DataAdapter` analyzuje, které byly provedeny změny a spuštěn příslušný příkaz (vložení, aktualizace nebo odstranění). Když `DataAdapter` dojde ke změně <xref:System.Data.DataRow>, použije <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, nebo <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> zpracovat změny. Můžete tak maximalizovat výkon vaší aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a kde je to možné, pomocí uložených procedur. Je nutné explicitně nastavit příkazy před voláním `Update`. Pokud `Update` nazývá a příslušný příkaz pro konkrétní aktualizace neexistuje (třeba ne `DeleteCommand` pro odstraněné řádky), je vyvolána výjimka.  
  
> [!NOTE]
>  Pokud chcete upravit nebo odstranit data s využitím používáte uložených procedur SQL serveru `DataAdapter`, ujistěte se, že SET NOCOUNT na nepoužívejte v definici uloženou proceduru. To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako ke konfliktu souběžnosti. V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.  
  
 Parametry příkazu je možné zadat vstupní a výstupní hodnoty pro příkaz SQL nebo uloženou proceduru pro každý řádek upravený `DataSet`. Další informace najdete v tématu [parametry adaptéru dat](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
>  Je důležité pochopit rozdíl mezi odstranění řádku v <xref:System.Data.DataTable> a odebrání řádku. Při volání `Remove` nebo `RemoveAt` metoda řádku je odebrán okamžitě. Žádné odpovídající řádky v back-endového zdroje dat nebude mít vliv, pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volat `Update`. Při použití `Delete` metody řádku zůstává ve `DataTable` a je označená k odstranění. Pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volat `Update`, odpovídající řádek v back-endového zdroje dat se odstraní.  
  
 Pokud vaše `DataTable` mapuje nebo je generován z jedné tabulky databáze, které můžete využít <xref:System.Data.Common.DbCommandBuilder> objektu automaticky generuje `DeleteCommand`, `InsertCommand`, a `UpdateCommand` objekty pro `DataAdapter`. Další informace najdete v tématu [generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Použití UpdatedRowSource k mapování hodnot do datové sady  
 Můžete řídit, jak jsou mapovány hodnot vrácených ze zdroje dat zpět do `DataTable` následující volání metody Update `DataAdapter`, s použitím <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnost <xref:System.Data.Common.DbCommand> objektu. Tím, že nastavíte `UpdatedRowSource` vlastnost na jednu z <xref:System.Data.UpdateRowSource> hodnot výčtu, můžete řídit, zda výstupní parametry vrácené `DataAdapter` příkazy jsou ignorována nebo použitý pro změněné řádky v `DataSet`. Můžete také určit, zda vrátí první řádek (pokud existuje) je použitý pro změněné řádky v `DataTable`.  
  
 Následující tabulka popisuje různé hodnoty `UpdateRowSource` výčet a způsob, jakým ovlivňují chování použít s příkaz `DataAdapter`.  
  
|UpdatedRowSource Enumeration|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Výstupní parametry a první řádek je sada výsledků dotazu vrácená může mapovat na změněný řádek v `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Změněný řádek v lze mapovat pouze data v prvním řádku je sada výsledků dotazu vrácená `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Žádné výstupní parametry nebo řádky vrácené výsledné sady jsou ignorovány.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Pouze výstupní parametry lze mapovat na změněný řádek v `DataSet`.|  
  
 `Update` Metoda vyřeší, vaše změny zpět do zdroje dat, ale ostatní klienty může mít upravená data ve zdroji dat od posledního jste vyplnili `DataSet`. Aktualizujte vaše `DataSet` s aktuálními údaji, použijte `DataAdapter` a `Fill` metoda. Nové řádky se přidají do tabulky a aktualizované informace budou zahrnuta do existující řádky. `Fill` Metody Určuje, jestli se přidá nový řádek nebo aktualizuje existující řádek porovnáním hodnoty primárního klíče pro řádky v tabulce `DataSet` a řádků vrácených `SelectCommand`. Pokud `Fill` metoda zjistí hodnotu primárního klíče pro řádek v `DataSet` odpovídající hodnotu primárního klíče z řádků ve výsledcích vrácených `SelectCommand`, aktualizuje existující řádek s informacemi z řádků vrácených `SelectCommand`a nastaví <xref:System.Data.DataRow.RowState%2A> existující řádku `Unchanged`. Pokud řádek vrácený `SelectCommand` má hodnotu primárního klíče, který neodpovídá žádnému hodnoty primárního klíče řádků v `DataSet`, `Fill` metoda přidá nový řádek s `RowState` z `Unchanged`.  
  
> [!NOTE]
>  Pokud `SelectCommand` vrátí výsledky z vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` hodnoty pro výsledné `DataTable`. Je nutné definovat `PrimaryKey` sobě a ujistěte se, že jsou správně přeložit duplicitní řádky. Další informace najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Zpracování výjimek, které mohou nastat při volání `Update` metodu, můžete použít `RowUpdated` události a reagovat na chyby aktualizace řádku, jak se objeví (naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), nebo můžete nastavit `DataAdapter.ContinueUpdateOnError` k `true` před voláním `Update`a reagovat na chybové informace uložené v `RowError` vlastnosti konkrétního řádku po dokončení aktualizace (naleznete v tématu [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Poznámka:** volání `AcceptChanges` na `DataSet`, `DataTable`, nebo `DataRow` způsobí, že všechny `Original` hodnoty `DataRow` chcete ji přepsat `Current` hodnoty `DataRow`. Pokud byly změněny hodnoty polí, které identifikují řádky jako jedinečné, po volání `AcceptChanges` `Original` hodnoty se už nebude odpovídat hodnotám ve zdroji dat. `AcceptChanges` je volána automaticky pro každý řádek při volání metody Update `DataAdapter`. Při volání metody Update první zadaný v nastavení můžete zachovat původní hodnoty `AcceptChangesDuringUpdate` vlastnost `DataAdapter` na hodnotu false, případně můžete vytvořit obslužnou rutinu události pro `RowUpdated` událostí a nastavení <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> k <xref:System.Data.UpdateStatus.SkipCurrentRow>. Další informace najdete v tématu [slučování obsahu datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak provádět aktualizace pro upravené řádky explicitním nastavením `UpdateCommand` z `DataAdapter` a volání jeho `Update` metoda. Všimněte si, že tento parametr zadán v klauzuli WHERE aktualizace příkazu nastaveno pro použití `Original` hodnotu `SourceColumn`. To je důležité, protože `Current` hodnota může změnit a nemusí odpovídat hodnotě ve zdroji dat. `Original` Hodnota je hodnota, která byla použita k vyplnění `DataTable` z datového zdroje.  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>Sloupců s automatickým navyšováním  
 Pokud tabulky ze zdroje dat. automatické zvyšování sloupců, můžete přejít k vyplnění sloupce, které vaše `DataSet` buď vrácením hodnoty automatické zvyšování čísla jako výstupní parametr uložené procedury a mapování, který sloupec v tabulce, Autor vrácení Automatické zvyšování čísla hodnotu na prvním řádku vrácený příkaz jazyka SQL nebo uloženou proceduru nebo s použitím sady výsledků `RowUpdated` událost `DataAdapter` provádět další příkaz SELECT. Další informace a příklad najdete v tématu [načítání Identity nebo automatického číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Pořadí vložení, aktualizace a odstranění  
 V mnoha případech platí, pořadí, ve které změny provedené `DataSet` jsou odesílány zdroj dat je důležité. Například pokud se aktualizuje existující řádek hodnoty primárního klíče a nový řádek se přidala se nová hodnota primárního klíče jako cizí klíč, je potřeba zpracovat aktualizace, než jsou insert.  
  
 Můžete použít `Select` metodu `DataTable` se vraťte `DataRow` pole, které odkazuje pouze na řádky s konkrétní `RowState`. Můžete předat vráceného `DataRow` pole na `Update` metodu `DataAdapter` zpracovat změněné řádky. Zadáním podmnožinu řádků, které mají být aktualizovány, můžete řídit pořadí, ve kterém jsou zpracovány vložení, aktualizace a odstranění.  
  
## <a name="example"></a>Příklad  
 Například následující kód zajišťuje, že jsou odstraněné řádky v tabulce zpracovaných první, pak aktualizované řádky a řádky vložené.  
  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Umožňuje načíst a aktualizovat Data adaptéru dat  
 Můžete použít adaptéru dat se načítají a aktualizují data.  
  
-   Ukázka používá DataAdapter.AcceptChangesDuringFill se klonovat data v databázi. Pokud je vlastnost nastavená na hodnotu false, metoda AcceptChanges není volána při vyplňování tabulky a nově přidané řádky jsou považovány za vložené řádky. Tedy Ukázka používá tyto řádky k vložení nových řádků do databáze.  
  
-   Ukázky pomocí DataAdapter.TableMappings definuje mapování mezi zdrojovou tabulku a DataTable.  
  
-   Ukázka používá DataAdapter.FillLoadOption určit, jakým způsobem adaptér naplňuje objekt DataTable z DbDataReader. Při vytváření objektu DataTable můžete pouze zapisovat data z databáze na aktuální verzi nebo verzi původního nastavením vlastnosti jako LoadOption.Upsert nebo LoadOption.PreserveChanges.  
  
-   Ukázka také aktualizovat tabulky pomocí DbDataAdapter.UpdateBatchSize k provádění operací služby batch.  
  
 Před kompilace a spuštění ukázky, budete muset vytvoření ukázkové databáze:  
  
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
  
 Projekty C# a Visual Basic se tento vzorový kód můžete najít na [ukázky kódu vývojáře](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).  
  
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
- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Stavy řádků a verze řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [Metody AcceptChanges a RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Slučování obsahu datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)
- [Načítání hodnot identity nebo automatického číslování](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
