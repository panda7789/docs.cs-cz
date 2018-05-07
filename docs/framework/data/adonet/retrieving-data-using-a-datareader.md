---
title: Načítání dat pomocí DataReader –
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 0c78db5ce7a6a988e40718daca1d828096a734d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-data-using-a-datareader"></a>Načítání dat pomocí DataReader –
Načítání dat pomocí **DataReader –** zahrnuje vytvoření instance **příkaz** objektu a pak vytvořit **DataReader –** voláním  **Command.ExecuteReader** k načtení řádků ze zdroje dat. Následující příklad ilustruje, použití **DataReader –** kde `reader` představuje platnou DataReader – a `command` představuje platný objekt příkazu.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Můžete použít **čtení** metodu **DataReader –** objekt, který chcete získat řádek z výsledků dotazu. Každý sloupec vrácený řádek dostanete předáním odkazu na pořadí sloupce, který se na název **DataReader –**. Pro nejlepší výkon, ale **DataReader –** poskytuje řadu metod, které vám umožní přístup k hodnot sloupce v jeho nativní datové typy (**GetDateTime**, **GetDouble**, **Getguid –**, **GetInt32**a tak dále). Seznam typové přístupových metod pro data specifický pro zprostředkovatele **DataReaders**, najdete v části <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>. Pomocí zadaných přístupových metod, za předpokladu, že se označuje základní datový typ, snižuje množství při načítání hodnoty sloupce vyžaduje převod typů.  
  
> [!NOTE]
>  Zahrnuje další vlastnost pro Windows Server 2003 verze rozhraní .NET Framework **DataReader –**, **HasRows**, což umožňuje zjistit, jestli **DataReader –**má nevrátil žádné výsledky před čtení z něj.  
  
 Následující příklad kódu iteruje **DataReader** objekt a vrátí dva sloupce z každého řádku.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** poskytuje bez vyrovnávací paměti datový proud dat, která umožňuje procedurální logiku a efektivní zpracování výsledků ze zdroje dat postupně. **DataReader** je vhodné použít při načítání velkých objemů dat, protože není uložen v mezipaměti v paměti.  
  
## <a name="closing-the-datareader"></a>Zavření objektu DataReader  
 Vždy byste měli zavolat **Zavřít** metoda po dokončení pomocí **DataReader** objektu.  
  
 Pokud vaše **příkaz** výstup obsahuje parametry nebo návratové hodnoty, nebude dostupná, dokud nebude **DataReader –** je uzavřený.  
  
 Všimněte si, že chvíli **DataReader –** je otevřený **připojení** se používá výhradně v tomto **DataReader –**. Nelze provést žádné příkazy pro **připojení**, včetně vytváření jiného **DataReader –**, dokud nebude původní **DataReader –** je uzavřený.  
  
> [!NOTE]
>  Nevolejte **Zavřít** nebo **Dispose** na **připojení**, **DataReader –**, nebo jiné spravovaného objektu v **dokončení**  metoda vaší třídy. V finalizační metodu vydání pouze nespravovaných prostředků, které vlastní třídu přímo. Pokud vaše třída nevlastní žádné nespravovaných prostředků, nezahrnujte **Finalize** metoda v definici vaší třídy. Další informace najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Načítání více sad výsledků dotazu pomocí NextResult  
 Pokud jsou vráceny více sad výsledků dotazu, **DataReader –** poskytuje **NextResult** metoda k iteraci v rámci výsledek nastaví v pořadí. Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků pomocí dvou příkazů SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metoda.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Získávání informací o schématu z objektu DataReader  
 Při **DataReader –** je otevřená, můžete načíst informace o schématu o aktuální výsledek nastavit pomocí **GetSchemaTable** metoda. **GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplněný řádků a sloupců, které obsahují informace o schématu pro aktuální sadu výsledků dotazu. **DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu. Každý sloupec řádku tabulky schématu je namapován na vlastnost sloupec, vrátí se v nastavit výsledek, kde **ColumnName** je název vlastnosti a hodnota sloupce je hodnota vlastnosti. Následující příklad kódu zapíše informace o schématu **DataReader –**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Práce s kapitolám OLE DB  
 Hierarchická sady řádků či kapitolám (typ OLE DB **DBTYPE_HCHAPTER**, ADO typ **adChapter**) se dá načíst pomocí <xref:System.Data.OleDb.OleDbDataReader>. Pokud se dotaz, který zahrnuje kapitola vrátí jako **DataReader –**, kapitoly je vrácen jako sloupec v tom, že **DataReader –** a je k dispozici jako **DataReader** objektu.  
  
 Technologie ADO.NET **datovou sadu** lze také použít k reprezentaci hierarchické sady řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami. Další informace najdete v tématu [datové sady, DataTables a DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Následující příklad kódu používá zprostředkovatele MSDataShape ke generování objednávek každému zákazníkovi neočekávaný sloupec kapitoly v seznamu zákazníků.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Vrátí výsledky s kurzory REF Oracle  
 Zprostředkovatel dat .NET Framework pro Oracle podporuje použití Oracle REF kurzory vrácení výsledku dotazu. V Oracle REF kurzor se vrátí jako <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Můžete načíst **připojení OracleDataReader** objekt, který představuje k KURZORU REF Oracle pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metodu a můžete také zadat <xref:System.Data.OracleClient.OracleCommand> , který vrací jeden nebo více kurzory REF Oracle jako  **SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> použitou k vyplnění <xref:System.Data.DataSet>.  
  
 Pro přístup k KURZORU REF vrátí ze zdroje dat Oracle, vytvořit **OracleCommand** pro svůj dotaz a přidejte výstupní parametr, který odkazuje na REF ukazatele **parametry** kolekce vaší  **OracleCommand**. Název parametru musí odpovídat názvu parametru REF KURZORU v dotazu. Nastavte typ parametru **OracleType.Cursor**. **ExecuteReader** metodu vaše **OracleCommand** vrátí **připojení OracleDataReader** pro kurzor REF.  
  
 Pokud vaše **OracleCommand** vrátí více REF kurzory, přidat více výstupní parametry. Různé kurzory REF můžete přejít pomocí volání **OracleCommand.ExecuteReader** metoda. Volání **ExecuteReader** vrátí **připojení OracleDataReader** odkazující na první REF kurzor. Potom můžete zavolat **OracleDataReader.NextResult** metody přístup následné REF kurzory. I když parametry ve vaší **OracleCommand.Parameters** kolekce shodu kurzor REF výstupní parametry podle názvu, **připojení OracleDataReader** k nim přistupuje v pořadí, aby byly přidány do  **Parametry** kolekce.  
  
 Zvažte například následující balíček Oracle a tělo balíčku.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 Následující kód vytvoří **OracleCommand** , vrátí kurzory REF z předchozí balíčku Oracle přidáním dva parametry typu **OracleType.Cursor** k **parametry** kolekce.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 Následující kód vrátí výsledky předchozí příkaz pomocí **čtení** a **NextResult** metody **připojení OracleDataReader**. Parametry KURZORU REF jsou vráceny v pořadí.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 Následující příklad používá předchozí příkaz k naplnění **datovou sadu** s výsledky balíčku Oracle.  
  
> [!NOTE]
>  Aby nedošlo **OverflowException**, doporučujeme také zpracovat žádné převod z typu Oracle číslo na platný typ rozhraní .NET Framework před uložením hodnoty v **DataRow**. Můžete použít **FillError** událostí k určení, zda **OverflowException** došlo k chybě. Další informace o **FillError** událostí, najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s DataReaders](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
