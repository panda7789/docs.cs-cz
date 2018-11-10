---
title: Načítání dat pomocí čtečky dat
ms.date: 10/259/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: d3c59b667c05be083e44de8cc3e7e44d50fefc71
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "43516788"
---
# <a name="retrieve-data-using-a-datareader"></a>Načtení dat pomocí čtečky dat
K načtení dat pomocí **DataReader**, vytvoření instance **příkaz** objektu a pak vytvořte **DataReader** voláním **Command.ExecuteReader**  načíst ze zdroje dat řádků. **DataReader** poskytuje bez vyrovnávací paměti datového proudu dat, která umožňuje procedurální logiku pro efektivní zpracování výsledků ze zdroje dat postupně. **DataReader** je dobrou volbou, pokud načítáte velkých objemů dat, protože data neukládají do mezipaměti v paměti.

Následující příklad ukazuje použití **DataReader**, kde `reader` představuje platné čtečky dat a `command` představuje objekt platný příkaz.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Použití **DataReader.Read** metoda získat řádek z výsledků dotazu. Každý sloupec vrácený řádek se zpřístupní po předání názvu nebo ordinální číslo sloupce, který se **DataReader**. Ale pro zajištění nejlepšího výkonu **DataReader** poskytuje řadu metod, které umožňují přístup k hodnot sloupce v jejich nativním datové typy (**GetDateTime**, **GetDouble**, **Getguid –**, **GetInt32**, a tak dále). Seznam typu přístupové metody pro data specifickým pro zprostředkovatele **čtečky dat**, naleznete v tématu <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>. Pomocí metod typu přístupového objektu, když víte, podkladová data typu snižuje počet při načítání hodnoty sloupce vyžaduje převod typů.  
  
 Následující příklad provede iteraci **DataReader** a vrátí dva sloupce z každého řádku.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Zavření objektu DataReader  
 Vždy volat **Zavřít** metoda po dokončení používání **DataReader** objektu.  
  
 Pokud vaše **příkaz** obsahuje výstupní parametry nebo návratové hodnoty, tyto hodnoty nejsou k dispozici, dokud **DataReader** je zavřený.  
  
 Při **DataReader** je otevřený, **připojení** používá výhradně, který **DataReader**. Nelze provést žádné příkazy pro **připojení**, včetně vytvoříte další **DataReader**, dokud původní **DataReader** je uzavřen.  
  
> [!NOTE]
>  Nevolejte **Zavřít** nebo **Dispose** na **připojení**, **DataReader**, nebo jakýkoli jiný spravovaný objekt v **Finalize**  metoda vaší třídy. V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo. Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte **Finalize** metoda v definici třídy. Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Načítání více výsledků nastaví pomocí NextResult  
 Pokud **DataReader** vrátí více sad výsledků dotazu, volání **NextResult** metoda procházením skrze výsledek nastaví postupně. Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků pomocí dvou příkazů SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Získávání informací o schématu z objektu DataReader  
 Při **DataReader** je otevřít, můžete načíst informace o schématu o aktuální výsledek sada s použitím **GetSchemaTable** metoda. **GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplní řádky a sloupce, které obsahují informace o schématu pro aktuální sadu výsledků. **DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu. Každý sloupec v tabulce schématu se mapuje na vlastnost sloupců vrácených v řádky výsledek nastavit, kam **Názevsloupce** je název vlastnosti a hodnota sloupce je hodnota vlastnosti. Následující příklad zapíše informace o schématu pro **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Práce s kapitol OLE DB  
 Hierarchické sady řádků nebo kapitol (typ OLE DB **DBTYPE_HCHAPTER**, typ ADO **adChapter**), můžete získat pomocí <xref:System.Data.OleDb.OleDbDataReader>. Při dotazu, který zahrnuje kapitola se vrátí jako **DataReader**, kapitoly je vrácen jako sloupec, který **DataReader** a je přístupný jako **DataReader** objektu.  
  
 ADO.NET **datovou sadu** lze také použít k reprezentaci hierarchické sady řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami. Další informace najdete v tématu [datové sady, datové tabulky a zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Následující příklad kódu používá zprostředkovatele MSDataShape ke generování objednávek pro každého zákazníka neočekávaný sloupec kapitoly v seznam zákazníků.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Vrací výsledky s soubory Oracle REF CURSOR  
 Zprostředkovatel dat .NET Framework pro Oracle podporuje použití soubory Oracle REF CURSOR vrácení výsledku dotazu. Vrátí se Oracle REF CURSOR jako <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Můžete načíst <xref:System.Data.OracleClient.OracleDataReader> objekt, který představuje Oracle REF CURSOR pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody. Můžete také určit, <xref:System.Data.OracleClient.OracleCommand> , který vrací jeden nebo více soubory Oracle REF CURSOR jako **SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> použitou k vyplnění <xref:System.Data.DataSet>.  
  
 Pro přístup k REF CURSOR vrácená ze zdroje dat Oracle, vytvořte <xref:System.Data.OracleClient.OracleCommand> pro váš dotaz a přidejte výstupní parametr, který odkazuje kurzor REF <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce vaše <xref:System.Data.OracleClient.OracleCommand>. Název parametru musí odpovídat názvu parametru REF CURSOR v dotazu. Nastavit typ parametru <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Metodu vaše <xref:System.Data.OracleClient.OracleCommand> vrátí <xref:System.Data.OracleClient.OracleDataReader> pro REF CURSOR.  
  
 Pokud vaše <xref:System.Data.OracleClient.OracleCommand> vrací více typů REF CURSOR, přidat více výstupní parametry. Dostanete různých typů REF CURSOR pomocí volání <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody. Volání <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> vrátí <xref:System.Data.OracleClient.OracleDataReader> odkazující na první REF CURSOR. Potom můžete zavolat <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metody pro přístup k dalších typů REF CURSOR. I když parametry v vaše <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekce shoda REF CURSOR output parametry podle názvu, <xref:System.Data.OracleClient.OracleDataReader> k nim přistupuje, v pořadí, ve kterém byly přidány do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce.  
  
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
  
 Následující kód vytvoří <xref:System.Data.OracleClient.OracleCommand> typů REF CURSOR z předchozí balíčku Oracle, který vrací tak, že přidáte dva parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> k <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekce.  
  
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
  
 Následující kód vrátí výsledky z předchozího příkazu s <xref:System.Data.OracleClient.OracleDataReader.Read> a <xref:System.Data.OracleClient.OracleDataReader.NextResult> metody <xref:System.Data.OracleClient.OracleDataReader>. Parametry REF CURSOR jsou vráceny v pořadí.  
  
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
  
 Následující příklad používá k naplnění předchozí příkaz <xref:System.Data.DataSet> s výsledky balíčku Oracle.  
  
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

> [!NOTE]
>  Aby se zabránilo **OverFlowException –**, doporučujeme také zpracovat jakýkoli převod z typu Oracle číslo na platný typ rozhraní .NET Framework před uložením hodnoty v <xref:System.Data.DataRow>. Můžete použít <xref:System.Data.Common.DataAdapter.FillError> událostí k určení, zda **OverFlowException –** došlo k chybě. Další informace o <xref:System.Data.Common.DataAdapter.FillError> událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Viz také:  
 [Práce s čtečky dat](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
