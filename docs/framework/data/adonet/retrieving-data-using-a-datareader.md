---
title: Načítání dat pomocí čtečky dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 4370a7a700a01943548bf067827e6640245caf4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482161"
---
# <a name="retrieving-data-using-a-datareader"></a>Načítání dat pomocí čtečky dat
Načítání dat pomocí **DataReader** zahrnuje vytvoření instance **příkaz** objektu a pak vytvořit **DataReader** voláním  **Command.ExecuteReader** načíst ze zdroje dat řádků. Následující příklad ukazuje použití **DataReader** kde `reader` představuje platné čtečky dat a `command` představuje objekt platný příkaz.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Můžete použít **čtení** metodu **DataReader** objektu získat řádek ve výsledcích dotazu. Každý sloupec vrácený řádek se zpřístupní po předání název nebo Řadový odkaz na sloupec, který se **DataReader**. Ale pro zajištění nejlepšího výkonu **DataReader** poskytuje řadu metod, které umožňují přístup k hodnot sloupce v jejich nativním datové typy (**GetDateTime**, **GetDouble**, **Getguid –**, **GetInt32**, a tak dále). Seznam typu přístupové metody pro data specifickým pro zprostředkovatele **čtečky dat**, naleznete v tématu <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>. Pomocí metody typu přístupového objektu, za předpokladu, že příslušný datový typ je známo, snižuje počet při načítání hodnoty sloupce vyžaduje převod typů.  
  
> [!NOTE]
>  Windows Server 2003 verze rozhraní .NET Framework obsahuje další vlastnosti pro **DataReader**, **HasRows**, což vám umožní zjistit, jestli **DataReader**má nevrátil žádné výsledky před čtením z něj.  
  
 Následující příklad Iteruje přes **DataReader** objekt a vrátí dva sloupce z každého řádku.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** poskytuje bez vyrovnávací paměti datového proudu dat, která umožňuje procedurální logiku pro efektivní zpracování výsledků ze zdroje dat postupně. **DataReader** je dobrou volbou při načítání velkých objemů dat, protože data neukládají do mezipaměti v paměti.  
  
## <a name="closing-the-datareader"></a>Zavření objektu DataReader  
 Vždy byste měli zavolat **Zavřít** metoda po dokončení pomocí **DataReader** objektu.  
  
 Pokud vaše **příkaz** obsahuje výstupní parametry nebo návratové hodnoty, nebudou k dispozici, dokud **DataReader** je zavřený.  
  
 Všimněte si, že při **DataReader** je otevřený, **připojení** používá výhradně, který **DataReader**. Nelze provést žádné příkazy pro **připojení**, včetně vytvoříte další **DataReader**, dokud původní **DataReader** je uzavřen.  
  
> [!NOTE]
>  Nevolejte **Zavřít** nebo **Dispose** na **připojení**, **DataReader**, nebo jakýkoli jiný spravovaný objekt v **Finalize**  metoda vaší třídy. V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo. Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte **Finalize** metoda v definici třídy. Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Při načítání více sad výsledků dotazu pomocí NextResult  
 Dojde k vrácení více sad výsledků dotazu **DataReader** poskytuje **NextResult** metoda procházením skrze výsledek nastaví v pořadí. Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků pomocí dvou příkazů SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Získávání informací o schématu z objektu DataReader  
 Při **DataReader** je otevřít, můžete načíst informace o schématu o aktuální výsledek sada s použitím **GetSchemaTable** metoda. **GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplní řádky a sloupce, které obsahují informace o schématu pro aktuální sadu výsledků. **DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu. Každý sloupec řádku schématu tabulky se mapuje na vlastnost sloupec vrácený v výsledné sady, ve kterém **Názevsloupce** je název vlastnosti a hodnota sloupce je hodnota vlastnosti. Následující příklad kódu zapíše informace o schématu pro **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Práce s kapitol technologie OLE DB  
 Hierarchické sady řádků nebo kapitol (typ OLE DB **DBTYPE_HCHAPTER**, typ ADO **adChapter**) můžete získat pomocí <xref:System.Data.OleDb.OleDbDataReader>. Při dotazu, který zahrnuje kapitola se vrátí jako **DataReader**, kapitoly je vrácen jako sloupec, který **DataReader** a je přístupný jako **DataReader** objektu.  
  
 ADO.NET **datovou sadu** lze také použít k reprezentaci hierarchické sady řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami. Další informace najdete v tématu [datové sady, datové tabulky a zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Následující příklad kódu používá zprostředkovatele MSDataShape ke generování objednávek pro každého zákazníka neočekávaný sloupec kapitoly v seznam zákazníků.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Vrací výsledky s soubory Oracle REF CURSOR  
 Zprostředkovatel dat .NET Framework pro Oracle podporuje použití soubory Oracle REF CURSOR vrácení výsledku dotazu. Vrátí se Oracle REF CURSOR jako <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Můžete načíst **připojení OracleDataReader** objekt, který představuje objekt pro Oracle REF CURSOR pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metoda a můžete také zadat <xref:System.Data.OracleClient.OracleCommand> , který vrací jeden nebo více soubory Oracle REF CURSOR jako  **Vlastnost SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> použitou k vyplnění <xref:System.Data.DataSet>.  
  
 Pro přístup k REF CURSOR vrácená ze zdroje dat Oracle, vytvořte **OracleCommand** pro váš dotaz a přidejte výstupní parametr, který odkazuje kurzor REF **parametry** kolekce vaše  **OracleCommand**. Název parametru musí odpovídat názvu parametru REF CURSOR v dotazu. Nastavit typ parametru **OracleType.Cursor**. **ExecuteReader** metodu vaše **OracleCommand** vrátí **připojení OracleDataReader** pro REF CURSOR.  
  
 Pokud vaše **OracleCommand** vrací více typů REF CURSOR, přidat více výstupní parametry. Dostanete různých typů REF CURSOR pomocí volání **OracleCommand.ExecuteReader** metody. Volání **ExecuteReader** vrátí **připojení OracleDataReader** odkazující na první REF CURSOR. Potom můžete zavolat **OracleDataReader.NextResult** metody pro přístup k dalších typů REF CURSOR. I když parametry v vaše **OracleCommand.Parameters** kolekce shoda REF CURSOR output parametry podle názvu, **připojení OracleDataReader** k nim přistupuje, aby byly přidány  **Parametry** kolekce.  
  
 Představte si třeba následující balíček Oracle a tělo balíčku.  
  
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
  
 Následující kód vytvoří **OracleCommand** typů REF CURSOR z předchozí balíčku Oracle, který vrací tak, že přidáte dva parametry typu **OracleType.Cursor** k **parametry** kolekce.  
  
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
  
 Následující kód vrátí výsledky z předchozího příkazu s **čtení** a **NextResult** metody **připojení OracleDataReader**. Parametry REF CURSOR jsou vráceny v pořadí.  
  
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
  
 Následující příklad používá k naplnění předchozí příkaz **datovou sadu** s výsledky balíčku Oracle.  
  
> [!NOTE]
>  Aby se zabránilo **OverFlowException –**, doporučujeme také zpracovat jakýkoli převod z typu Oracle číslo na platný typ rozhraní .NET Framework před uložením hodnoty v **DataRow**. Můžete použít **FillError** událostí k určení, zda **OverFlowException –** došlo k chybě. Další informace o **FillError** událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
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
 [Práce s čtečky dat](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
