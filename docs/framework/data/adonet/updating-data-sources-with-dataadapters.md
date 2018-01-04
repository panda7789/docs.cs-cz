---
title: "Aktualizace zdrojů dat s DataAdapters"
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
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 44bd1672c6423277fa90eee98ce954e7c1c5334e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="updating-data-sources-with-dataadapters"></a>Aktualizace zdrojů dat s DataAdapters
`Update` Metodu <xref:System.Data.Common.DataAdapter> je volána k vyřešení změny z <xref:System.Data.DataSet> zpět do zdroje dat. `Update` Metoda, například `Fill` metoda, přijímá jako argumenty instanci `DataSet`a volitelné <xref:System.Data.DataTable> objekt nebo `DataTable` název. `DataSet` Instance je `DataSet` obsahuje změny, které byly provedeny, a `DataTable` identifikuje tabulka, ze kterých se budou načítat změny. Pokud žádné `DataTable` není zadaný, první `DataTable` v `DataSet` se používá.  
  
 Při volání `Update` metody `DataAdapter` analyzuje změny, které jste provedli a provede příslušnou příkazu (INSERT, UPDATE nebo DELETE). Když `DataAdapter` dojde ke změně <xref:System.Data.DataRow>, použije <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, nebo <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> zpracovat změny. To umožňuje maximalizovat výkon vaší aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a, kde je to možné, prostřednictvím uložených procedur. Musíte jednoznačně nastavit příkazy před voláním `Update`. Pokud `Update` nazývá a příslušný příkaz neexistuje pro konkrétní aktualizaci (například Ne `DeleteCommand` pro odstranit řádky), je vyvolána výjimka.  
  
> [!NOTE]
>  Pokud chcete upravit nebo odstranit data pomocí používáte uložené procedury SQL serveru `DataAdapter`, ujistěte se, nepoužívejte SET NOCOUNT ON v definici uložené procedury. To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako konflikt souběžnosti. V takovém případě <xref:System.Data.DBConcurrencyException> bude vyvolána.  
  
 Parametry příkazu lze zadat vstupní a výstupní hodnoty pro příkaz SQL nebo uloženou proceduru pro každý řádek upravený `DataSet`. Další informace najdete v tématu [DataAdapter parametry](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
>  Je důležité si uvědomit rozdíl mezi odstranění řádku <xref:System.Data.DataTable> a odebírání řádek. Při volání `Remove` nebo `RemoveAt` metoda, řádek je odebrán okamžitě. Žádné odpovídající řádky v back-end zdroj dat, nebude mít vliv, pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volání `Update`. Při použití `Delete` metody řádek zůstane v `DataTable` a je označena pro odstranění. Pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volání `Update`, odpovídající řádek v back-end zdroj dat je odstraněn.  
  
 Pokud vaše `DataTable` mapuje nebo se vygeneruje z jedné tabulky databáze, můžete využít výhod <xref:System.Data.Common.DbCommandBuilder> objekt, který má automaticky generovat `DeleteCommand`, `InsertCommand`, a `UpdateCommand` objekty pro `DataAdapter`. Další informace najdete v tématu [generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Mapování hodnot na datovou sadu pomocí UpdatedRowSource  
 Můžete řídit, jak jsou mapována hodnot vrácených ze zdroje dat na `DataTable` následující volání metodě aktualizace `DataAdapter`, pomocí <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnost <xref:System.Data.Common.DbCommand> objektu. Nastavením `UpdatedRowSource` vlastnost na jednu z <xref:System.Data.UpdateRowSource> hodnoty výčtu, můžete řídit zda výstupní parametry vrácený `DataAdapter` příkazy jsou ignorovány nebo použitá na změněných řádků v `DataSet`. Můžete také určit, zda vrátí první řádek (pokud existuje) se použijí na změněných řádků v `DataTable`.  
  
 Následující tabulka popisuje různé hodnoty `UpdateRowSource` výčet a jejich vliv na chování příkazu použít s `DataAdapter`.  
  
|UpdatedRowSource – výčet|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Výstupní parametry a první řádek je sada výsledků vrácená dotazu může být namapovaný na změněné řádek v `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Pouze data na prvním řádku je sada výsledků vrácená dotazu může být namapovaný na změněné řádek v `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Výstup parametry nebo řádky vrácené výsledné sady jsou ignorovány.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Pouze výstupní parametry se dají namapovat na změněné řádek v `DataSet`.|  
  
 `Update` Metoda přeloží změny zpět do zdroje dat; ale jiných klientů může mít změnit dat ve zdroji dat od poslední jste vyplnili `DataSet`. Aktualizace vašeho `DataSet` s aktuální data, použijte `DataAdapter` a `Fill` metoda. Přidá nové řádky do tabulky a aktualizované informace se začlení do existujících řádků. `Fill` Metoda určuje, zda bude přidán nový řádek nebo zaktualizuje stávající řádek porovnáním hodnot primárního klíče řádků v `DataSet` a řádky vrácené `SelectCommand`. Pokud `Fill` metoda zaznamená hodnotu primárního klíče pro řádek v `DataSet` odpovídající hodnotu primárního klíče v řádku v výsledků vrácených `SelectCommand`, aktualizuje existující řádek s informací z řádku vrácené `SelectCommand`a nastaví <xref:System.Data.DataRow.RowState%2A> z existující řádek, abyste `Unchanged`. Pokud řádek vrácený `SelectCommand` má hodnotu primárního klíče, který neodpovídá žádnému z hodnot primárního klíče řádků v `DataSet`, `Fill` metoda přidá nový řádek s `RowState` z `Unchanged`.  
  
> [!NOTE]
>  Pokud `SelectCommand` vrátí výsledky z vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` výsledná hodnota `DataTable`. Je nutné definovat `PrimaryKey` si, že jsou správně přeložit duplicitní řádky. Další informace najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Zpracování výjimek, které mohou nastat při volání `Update` metodu, můžete použít `RowUpdated` událostí reagovat na řádek aktualizace chyby, kdy k nim dojde (najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), nebo můžete nastavit `DataAdapter.ContinueUpdateOnError` k `true` před voláním `Update`a reagovat na informace o chybě, které jsou uložené v `RowError` vlastnost konkrétního řádku po dokončení aktualizace (najdete v části [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Poznámka:** volání `AcceptChanges` na `DataSet`, `DataTable`, nebo `DataRow` způsobí, že všechny `Original` hodnoty pro `DataRow` přepsání s `Current` hodnoty `DataRow`. Pokud hodnoty polí, které identifikují řádku jako jedinečný změnilo po volání `AcceptChanges` `Original` hodnoty budou už shodují s hodnotami v datovém zdroji. `AcceptChanges`je automaticky volána pro každý řádek během volání metodě aktualizace `DataAdapter`. Můžete zachovat původní hodnoty při volání metody aktualizace první nastavením `AcceptChangesDuringUpdate` vlastnost `DataAdapter` na hodnotu false, případně můžete vytvořit obslužnou rutinu události pro `RowUpdated` událostí a nastavení <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> k <xref:System.Data.UpdateStatus.SkipCurrentRow>. Další informace najdete v tématu [slučování obsah datovou sadu](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak provést aktualizace na upravené řádky explicitně nastavením `UpdateCommand` z `DataAdapter` a volání jeho `Update` metoda. Všimněte si, že zadaný parametr v klauzuli WHERE aktualizace příkaz nastaven pro použití `Original` hodnotu `SourceColumn`. To je důležité, protože `Current` hodnota může změnit a nemusí odpovídat hodnotě v datovém zdroji. `Original` Hodnota je hodnota, která byla použita k vyplnění `DataTable` ze zdroje dat.  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>Element AutoIncrement sloupců  
 Pokud automaticky rostoucí sloupců tabulky ze zdroje dat, můžete vyplnit sloupce vaší `DataSet` buď tak, že vrací hodnotu automatického přírůstku jako výstupní parametr uložené procedury a který mapování na sloupec v tabulce, pomocí vrácení hodnota automatického přírůstku na prvním řádku sada výsledků vrácená pomocí uložené procedury nebo příkazu SQL, nebo pomocí `RowUpdated` události `DataAdapter` k provedení příkazu vyberte další. Další informace a příklady naleznete v tématu [načítání Identity nebo automatické číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Řazení vložení, aktualizace a odstranění  
 V mnoha případech pořadí, ve které změny prostřednictvím `DataSet` odešlou zdroj dat je důležité. Například pokud se aktualizuje stávající řádek hodnotu primárního klíče a nový řádek byla přidána s novou hodnotu primárního klíče jako cizí klíč, je potřeba zpracovat aktualizace, než insert.  
  
 Můžete použít `Select` metodu `DataTable` vrátit `DataRow` pole, které odkazuje pouze řádky s konkrétní `RowState`. Potom můžete předat vrácený `DataRow` pole na `Update` metodu `DataAdapter` zpracovat změněné řádky. Zadáním podmnožinu řádků, který má být aktualizován, můžete řídit pořadí, ve kterém jsou zpracovány vložení, aktualizace a odstranění.  
  
## <a name="example"></a>Příklad  
 Následující kód například zajišťuje, aby byly odstraněné řádky v tabulce zpracovaná první, potom aktualizované řádky a řádky vložené.  
  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Použijte modul DataAdapter načíst a aktualizovat Data  
 Modul DataAdapter můžete načíst a aktualizovat data.  
  
-   Příklad používá DataAdapter.AcceptChangesDuringFill klonovat data v databázi. Pokud je vlastnost nastavena jako hodnotu false, metoda AcceptChanges není volán při vyplňování tabulky a nově přidané řádky jsou považovány za vložených řádků. Ano příklad používá tyto řádky do nové řádky vložit do databáze.  
  
-   Ukázky DataAdapter.TableMappings používá k definování mapování mezi zdrojovou tabulku a DataTable.  
  
-   Ukázka používá k určení, jak adaptér doplní DataTable z DbDataReader DataAdapter.FillLoadOption. Při vytváření DataTable můžete pouze zapsat data z databáze do aktuální verze nebo na původní verzi nastavením vlastnosti jako LoadOption.Upsert nebo LoadOption.PreserveChanges.  
  
-   Ukázka bude také aktualizovat tabulky pomocí DbDataAdapter.UpdateBatchSize provést dávkové operace.  
  
 Před zkompilování a spuštění ukázky, je třeba k vytvoření ukázkové databáze:  
  
```  
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
  
 C# a Visual Basic projekty s této ukázce kódu najdete na [ukázky kódu vývojáře](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).  
  
```  
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
      String resetCols = String.Join(",", resetColumns.Select(col => "Max(" + col.ColumnName + ") as " + col.ColumnName));  
  
      String selectString = String.Format("Select {0},{1} from Course Group by {0}", primaryCols, resetCols);  
  
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
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Stavy řádků a verze řádků](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Metody AcceptChanges a RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [Slučování obsahu datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Načítání hodnot identity nebo automatického číslování](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
