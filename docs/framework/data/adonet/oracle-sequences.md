---
title: Sekvence Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 4c1829cc3f9506b0317e6638fd2760a91c7d19d6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520335"
---
# <a name="oracle-sequences"></a>Sekvence Oracle
Zprostředkovatel dat .NET Framework pro Oracle poskytuje podporu pro načtení hodnoty klíče generovaný serverem sekvence Oracle po provedení operace vložení pomocí <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server a Oracle podporu vytváření automatické zvyšování hodnoty sloupce, které lze označit jako primární klíče. Tyto hodnoty jsou generovány serveru při přidání řádků do tabulky. V systému SQL Server nastavte vlastnost Identity sloupce; v databázi Oracle vytvoříte pořadí. Rozdíl mezi sloupce s automatickým krokem v systému SQL Server a pořadí v Oracle je, že:  
  
-   V systému SQL Server označte sloupec jako sloupec s automatickým krokem a systému SQL Server automaticky vytvoří nové hodnoty pro sloupec, když vložíte nový řádek.  
  
-   V databázi Oracle vytvoříte pořadí generovat nové hodnoty pro sloupec v tabulce, ale neexistuje žádné přímé spojení mezi sekvence a tabulky nebo sloupce. Sekvence Oracle je objekt, jako jsou tabulky a uložené procedury.  
  
 Když vytvoříte pořadí v databázi Oracle, můžete definovat počáteční hodnoty a mezi jeho hodnoty přírůstku. Před odesláním nové řádky se můžete dotazovat také pořadí pro nové hodnoty. To znamená, že váš kód dokáže rozpoznat klíčové hodnoty pro nové řádky, před jejich vložení do databáze.  
  
 Další informace o vytváření s využitím SQL serveru a ADO.NET sloupce s automatickým krokem, najdete v článku [načítání Identity nebo automatického číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md) a [vytváření sloupců s automatickým navyšováním](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# ukazuje, jak můžete načíst nové hodnoty pořadí z databáze Oracle. V příkladu odkazuje pořadí v používá k odeslání nových řádků vložit do dotazu a vrátí hodnotu pořadí vygenerované pomocí klauzule RETURNING zavedený Oracle10g. Příklad přidá řadu čekající na nové řádky v <xref:System.Data.DataTable> pomocí ADO. NET pro automatické zvyšování čísla funkcionalitou pro vygenerování hodnoty primárního klíče "zástupný text". Všimněte si, že hodnota přírůstku ADO.NET vygenerovaný pro nový řádek jenom "zástupný symbol". To znamená, že databáze může vygenerovat jiné hodnoty než ty, které generuje ADO.NET.  
  
 Před odesláním čekající na vyřízení vložení informací do databáze, v příkladu se zobrazí obsah řádky. Potom kód vytvoří novou <xref:System.Data.OracleClient.OracleDataAdapter> objekt a nastaví její <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> a <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> vlastnosti. V příkladu také poskytuje logiku pro návratové hodnoty generovaný serverem pomocí výstupní parametry. Poté, v příkladu se provede aktualizace na odeslání čekajících řádků a zobrazí obsah <xref:System.Data.DataTable>.  
  
```csharp  
public void OracleSequence(String connectionString)  
{  
   String insertString =   
      "INSERT INTO SequenceTest_Table (ID, OtherColumn)" +  
      "VALUES (SequenceTest_Sequence.NEXTVAL, :OtherColumn)" +  
      "RETURNING ID INTO :ID";  
  
   using (OracleConnection conn = new OracleConnection(connectionString))  
   {  
      //Open a connection.  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
  
      // Prepare the database.  
      cmd.CommandText = "DROP SEQUENCE SequenceTest_Sequence";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "DROP TABLE SequenceTest_Table";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "CREATE TABLE SequenceTest_Table " +  
                     "(ID int PRIMARY KEY, OtherColumn varchar(255))";  
      cmd.ExecuteNonQuery();  
  
      cmd.CommandText = "CREATE SEQUENCE SequenceTest_Sequence " +  
                        "START WITH 100 INCREMENT BY 5";  
      cmd.ExecuteNonQuery();  
  
      DataTable testTable = new DataTable();  
      DataColumn column = testTable.Columns.Add("ID", typeof(int));  
      column.AutoIncrement = true;  
      column.AutoIncrementSeed = -1;  
      column.AutoIncrementStep = -1;  
      testTable.PrimaryKey = new DataColumn[] { column };  
      testTable.Columns.Add("OtherColumn", typeof(string));  
      for (int rowCounter = 1; rowCounter <= 15; rowCounter++)  
      {  
         testTable.Rows.Add(null, "Row #" + rowCounter.ToString());  
      }  
  
      Console.WriteLine("Before Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      Console.WriteLine();  
  
      cmd.CommandText =   
        "SELECT ID, OtherColumn FROM SequenceTest_Table";  
      OracleDataAdapter da = new OracleDataAdapter(cmd);  
      da.InsertCommand = new OracleCommand(insertString, conn);  
      da.InsertCommand.Parameters.Add(":ID", OracleType.Int32, 0, "ID");  
      da.InsertCommand.Parameters[0].Direction = ParameterDirection.Output;  
      da.InsertCommand.Parameters.Add(":OtherColumn", OracleType.VarChar, 255, "OtherColumn");  
      da.InsertCommand.UpdatedRowSource = UpdateRowSource.OutputParameters;  
      da.UpdateBatchSize = 10;  
  
      da.Update(testTable);  
  
      Console.WriteLine("After Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      // Close the connection.  
      conn.Close();  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
