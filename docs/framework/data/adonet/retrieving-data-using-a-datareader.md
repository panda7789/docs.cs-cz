---
title: Načítání dat pomocí čtečky dat
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 561ebd7ac6948fa42f73ebb4f1eb97c574e6d7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963165"
---
# <a name="retrieve-data-using-a-datareader"></a>Načtení dat pomocí datového objektu DataReader
Chcete-li načíst datapomocí objektu DataReader, vytvořte instanci **objektu Command** a pak vytvořte objekt DataReader voláním **příkazu Command. ExecuteReader** pro načtení řádků ze zdroje dat. Objekt **DataReader** poskytuje datový proud bez vyrovnávací paměti, který umožňuje procedurální logice efektivně zpracovávat výsledky ze zdroje dat postupně. Objekt **DataReader** je dobrou volbou při načítání velkých objemů dat, protože data nejsou ukládána v paměti.

Následující příklad znázorňuje použití objektu DataReader, který `reader` představuje platný objekt DataReader `command` a představuje platný objekt příkazu.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

K získání řádku z výsledků dotazu použijte metodu **DataReader. Read** . Do každého sloupce vráceného řádku můžete přistupovat předáním názvu nebo pořadového čísla sloupce do objektu DataReader. Pro nejlepší výkon ale DataReader poskytuje řadu metod, které umožňují přístup k hodnotám sloupců v jejich nativních datových typech (GetDateTime, GetDouble, GetGUID, GetInt32a tak dále). Seznam typových přístupových metod pro datačtecí metody specifických proposkytovatele dat naleznete v tématech <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.SqlClient.SqlDataReader>. Použití typových přístupových metod, pokud víte, že podkladový datový typ snižuje množství konverze typu požadované při načítání hodnoty sloupce.  
  
 Následující příklad provede iteraci objektu **DataReader** a vrátí dva sloupce z každého řádku.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Zavření objektu DataReader  
 Po dokončení používání objektu DataReader vždy zavolejte metodu **Close** .  
  
 Pokud váš **příkaz** obsahuje výstupní parametry nebo návratové hodnoty, tyto hodnoty nejsou k dispozici , dokud není DataReader uzavřen.  
  
 Když je objekt DataReader otevřený, **připojení** je používáno výhradně tímto objektem DataReader. Pro **připojení**nemůžete spustit žádné příkazy, včetně vytvoření jinéhoobjektu DataReader, dokud nebude původní DataReader uzavřený.  
  
> [!NOTE]
> Nevolejte funkci **Close** nebo **Dispose** pro **připojení**, objekt **DataReader**nebo jakýkoli jiný spravovaný objekt v metodě **Finalize** třídy. V finalizační metodě pouze uvolní nespravované prostředky, které vaše třída vlastní. Pokud vaše třída nevlastní žádné nespravované prostředky, nezahrnujte do definice třídy metodu **Finalize** . Další informace najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Načítání více sad výsledků pomocí NextResult  
 Pokud **DataReader** vrátí více sad výsledků, zavolejte metodu **NextResult** pro iteraci skrze sady výsledků dotazu. Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků dvou příkazů Select <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> pomocí metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Získávání informací o schématu z objektu DataReader  
 Když je objekt DataReader otevřený, můžete načíst informace o schématu aktuální sady výsledků pomocí metody GetSchema. GetSchemas vrátí <xref:System.Data.DataTable> objekt naplněný řádky a sloupci, které obsahují informace o schématu pro aktuální sadu výsledků dotazu. **Objekt DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků dotazu. Každý sloupec tabulky schématu se mapuje na vlastnost sloupců vrácených v řádcích sady výsledků, kde **ColumnName** je název vlastnosti a hodnota sloupce je hodnota vlastnosti. Následující příklad vypíše informace o schématu pro **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Práce s OLE DB kapitolami  
 Hierarchické sady řádků nebo kapitoly (OLE DB typu **DBTYPE_HCHAPTER**, ADO Type **adChapter**), lze <xref:System.Data.OleDb.OleDbDataReader>načíst pomocí. Pokud je jako objekt DataReader vrácen dotaz, který obsahujekapitolu, je tato kapitola vrácena jako sloupec v objektu **DataReader** a je vystavena jako objekt DataReader.  
  
 Datovou **sadu** ADO.NET lze také použít k reprezentaci hierarchických sad řádků pomocí vztahů nadřazenosti a podřízenosti mezi tabulkami. Další informace najdete v tématu [datové sady, datové tabulky a datazobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Následující příklad kódu používá poskytovatele MSDataShape k vygenerování sloupce kapitoly objednávek pro každého zákazníka v seznamu zákazníků.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Vracení výsledků pomocí REFERENČNÍch KURZORů Oracle  
 Zprostředkovatel dat .NET Framework pro Oracle podporuje použití odkazů Oracle REF CURSOR k vrácení výsledku dotazu. Referenční kurzor Oracle se vrátí jako <xref:System.Data.OracleClient.OracleDataReader>.  
  
 <xref:System.Data.OracleClient.OracleDataReader> Objekt, který představuje referenční kurzor Oracle, můžete načíst <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> pomocí metody. Můžete také zadat <xref:System.Data.OracleClient.OracleCommand> , který vrátí jeden nebo více referenčních kurzorů Oracle <xref:System.Data.OracleClient.OracleDataAdapter> jako **vlastnost SelectCommand** , která se používá k naplnění <xref:System.Data.DataSet>.  
  
 Chcete-li získat přístup k referenčnímu ukazateli vrácenému ze zdroje <xref:System.Data.OracleClient.OracleCommand> dat Oracle, vytvořte pro dotaz dotaz a přidejte výstupní parametr, který odkazuje na <xref:System.Data.OracleClient.OracleCommand.Parameters> ukazatel ref na <xref:System.Data.OracleClient.OracleCommand>kolekci vaší. Název parametru se musí shodovat s názvem parametru REF CURSOR v dotazu. Nastavte typ parametru na <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>. Metoda vašeho <xref:System.Data.OracleClient.OracleCommand> vrátí<xref:System.Data.OracleClient.OracleDataReader> pro kurzor ref. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>  
  
 <xref:System.Data.OracleClient.OracleCommand> Pokud vrátí více ukazatelů ref, přidejte více výstupních parametrů. Můžete získat přístup k různým odkazovým Kurzorům voláním <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> Volání<xref:System.Data.OracleClient.OracleDataReader> funkce vrátí odkaz na první odkazový kurzor. Pak můžete zavolat <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metodu pro přístup k dalším odkazovým Kurzorům. I když parametry ve vaší <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekci odpovídají výstupním parametrům REF CURSOR podle názvu <xref:System.Data.OracleClient.OracleDataReader> , přistupuje je v pořadí, ve kterém byly přidány do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce.  
  
 Zvažte například následující balíček Oracle a tělo balíčku.  
  
```sql
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
  
 Následující kód vytvoří objekt <xref:System.Data.OracleClient.OracleCommand> , který vrátí referenční kurzory z předchozího balíčku Oracle přidáním dvou parametrů typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekce.  
  
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
  
 Následující kód vrátí výsledky předchozího příkazu pomocí <xref:System.Data.OracleClient.OracleDataReader.Read> metody <xref:System.Data.OracleClient.OracleDataReader>a <xref:System.Data.OracleClient.OracleDataReader.NextResult> . Parametry REF CURSOR jsou vráceny v pořadí.  
  
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
  
 Následující příklad používá předchozí příkaz k naplnění <xref:System.Data.DataSet> výsledků balíčku Oracle.  
  
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
> Abyste se vyhnuli **OverflowException**, doporučujeme, abyste před uložením hodnoty v <xref:System.Data.DataRow>. také pokaždé konverze z typu čísla Oracle na platný typ .NET Framework. <xref:System.Data.Common.DataAdapter.FillError> Událost můžete použít k určení, zda došlo k **OverflowException** . Další informace o <xref:System.Data.Common.DataAdapter.FillError> události naleznete v tématu [zpracování událostí DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
