---
title: Načítání dat pomocí čtečky dat
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149021"
---
# <a name="retrieve-data-using-a-datareader"></a>Načtení dat pomocí datareaderu
Chcete-li načíst data pomocí **datareaderu**, vytvořte instanci objektu **Příkaz** a pak **vytvořte datareader** voláním **Příkaz.ExecuteReader** pro načtení řádků ze zdroje dat. **DataReader** poskytuje bez vyrovnávací proud dat, který umožňuje procedurální logiku efektivně zpracovávat výsledky ze zdroje dat postupně. **DataReader** je dobrou volbou při načítání velkého množství dat, protože data nejsou uložena v mezipaměti.

Následující příklad ilustruje použití **DataReader** `reader` , kde představuje `command` platný DataReader a představuje platný objekt Příkaz.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Pomocí metody **DataReader.Read** získáte řádek z výsledků dotazu. Ke každému sloupci vráceného řádku můžete přistupovat předáním názvu nebo číslo čísla sloupce **aplikaci DataReader**. Pro nejlepší výkon však **DataReader** poskytuje řadu metod, které umožňují přístup k hodnotám sloupců v jejich nativní datové typy **(GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**a tak dále). Seznam metod přístupového operátoru typu pro datové čtečky <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.SqlClient.SqlDataReader>specifické pro zprostředkovatele dat naleznete v **tématu**a . Použití zadávaných přistupovacích metod, pokud znáte základní datový typ, snižuje množství převodu typu, který je nutný při načítání hodnoty sloupce.  
  
 Následující příklad itetuje prostřednictvím objektu **DataReader** a vrátí dva sloupce z každého řádku.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Zavření čtečky dat  
 Po dokončení použití objektu **DataReader** vždy zavolejte metodu **Close.**  
  
 Pokud **příkaz** obsahuje výstupní parametry nebo vrácené hodnoty, tyto hodnoty nejsou k dispozici, dokud **datareader** je uzavřen.  
  
 Při **datareader** je **otevřena, připojení** je používán výhradně, že **DataReader**. Nelze spustit žádné příkazy pro **připojení**, včetně vytvoření jiné **datareader**, dokud původní **DataReader** je uzavřen.  
  
> [!NOTE]
> Nevolat **Close** nebo **Dispose** na **připojení**, **DataReader**nebo jakýkoli jiný spravovaný objekt v **Finalize** metoda vaší třídy. Ve finalizační metodě uvolněte pouze nespravované prostředky, které přímo vlastní vaše třída. Pokud vaše třída nevlastní žádné nespravované prostředky, nezahrnujte metodu **Finalize** do definice třídy. Další informace naleznete v [tématu Garbage Collection](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Načítání více sad výsledků pomocí funkce NextResult  
 Pokud **DataReader** vrátí více sad výsledků, volejte **NextResult** metoda iterát prostřednictvím sady výsledků postupně. Následující příklad ukazuje <xref:System.Data.SqlClient.SqlDataReader> zpracování výsledků dvou příkazů <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> SELECT pomocí metody.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Získání informací o schématu z datareaderu  
 Když je otevřena **datareader,** můžete načíst informace o schématu o aktuální sadě výsledků pomocí **metody GetSchemaTable.** **GetSchemaTable** vrátí <xref:System.Data.DataTable> objekt naplněný řádky a sloupci, které obsahují informace o schématu pro aktuální sadu výsledků. **DataTable** obsahuje jeden řádek pro každý sloupec sady výsledků. Každý sloupec tabulky schématu mapuje na vlastnost sloupců vrácených v řádcích sady výsledků, kde **ColumnName** je název vlastnosti a hodnota sloupce je hodnota vlastnosti. Následující příklad zapíše informace o schématu pro **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Práce s kapitolami TECHNOLOGIE OLE DB  
 Hierarchické sady řádků nebo kapitoly (typ OLE DB **DBTYPE_HCHAPTER**, **adChapter**typu <xref:System.Data.OleDb.OleDbDataReader>ADO ) lze načíst pomocí . Pokud je dotaz, který obsahuje kapitolu, vrácen jako **DataReader**, je tato kapitola vrácena jako sloupec v této **aplikaci DataReader** a je vystavena jako objekt **DataReader.**  
  
 ADO.NET **DataSet** lze také použít k reprezentaci hierarchické sady řádků pomocí relace nadřazený podřízený mezi tabulkami. Další informace naleznete v [tématu DataSets, DataTables a DataViews](./dataset-datatable-dataview/index.md).  
  
 Následující příklad kódu používá zprostředkovatele MSDataShape ke generování sloupce kapitol objednávek pro každého zákazníka v seznamu zákazníků.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Vrácení výsledků pomocí řešení Oracle REF CURSORs  
 Zprostředkovatel dat rozhraní .NET Framework pro oracle podporuje použití řešení Oracle REF CURSORs k vrácení výsledku dotazu. Oracle REF CURSOR je <xref:System.Data.OracleClient.OracleDataReader>vrácena jako .  
  
 Pomocí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody <xref:System.Data.OracleClient.OracleDataReader> můžete načíst objekt, který představuje Oracle REF CURSOR. <xref:System.Data.OracleClient.OracleCommand> Můžete také určit, který vrátí jeden nebo více Řešení REF CURSORs jako **SelectCommand** pro <xref:System.Data.OracleClient.OracleDataAdapter> slouží k vyplnění . <xref:System.Data.DataSet>  
  
 Chcete-li získat přístup k ref cursor <xref:System.Data.OracleClient.OracleCommand> vrácené ze zdroje dat Oracle, vytvořte pro <xref:System.Data.OracleClient.OracleCommand.Parameters> dotaz <xref:System.Data.OracleClient.OracleCommand>a přidejte výstupní parametr, který odkazuje na KURZOR REF na kolekci vašeho . Název parametru se musí shodovat s názvem parametru REF CURSOR v dotazu. Nastavte typ parametru <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>na . Metoda <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> vrátí <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> pro REF CURSOR.  
  
 Pokud <xref:System.Data.OracleClient.OracleCommand> vrátí více REF CURSORS, přidejte více výstupních parametrů. Můžete přistupovat k různým REF CURSORs voláním <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody. Volání vrátí <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> <xref:System.Data.OracleClient.OracleDataReader> odkazující na první KURZOR REF. Potom můžete volat <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metodu pro přístup k následné REF CURSORs. Přestože parametry <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> v kolekci odpovídají výstupní parametry <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR podle názvu, přistupuje k nim v pořadí, ve kterém byly přidány do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekce.  
  
 Zvažte například následující oracle balíček a balíček tělo.  
  
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
  
 Následující kód vytvoří, <xref:System.Data.OracleClient.OracleCommand> který vrátí REF CURSORs z předchozího balíčku <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> Oracle <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> přidáním dvou parametrů typu do kolekce.  
  
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
  
 Následující kód vrátí výsledky předchozího <xref:System.Data.OracleClient.OracleDataReader.Read> příkazu <xref:System.Data.OracleClient.OracleDataReader.NextResult> pomocí <xref:System.Data.OracleClient.OracleDataReader>metody a . Parametry REF CURSOR jsou vráceny v pořadí.  
  
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
  
 Následující příklad používá předchozí příkaz <xref:System.Data.DataSet> k naplnění s výsledky balíčku Oracle.  
  
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
> Chcete-li se vyhnout **PřetečeníException**, doporučujeme také zpracovat jakýkoli převod z typu Oracle NUMBER <xref:System.Data.DataRow>na platný typ rozhraní .NET Framework před uložením hodnoty v . <xref:System.Data.Common.DataAdapter.FillError> Událost můžete použít k určení, pokud došlo k **OverflowException.** Další informace o <xref:System.Data.Common.DataAdapter.FillError> události naleznete v tématu [Zpracování událostí datového adaptéru](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Přehled ADO.NET](ado-net-overview.md)
