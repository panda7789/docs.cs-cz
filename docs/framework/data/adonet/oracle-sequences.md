---
title: Pořadí Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 9f89234168351191c63d81fd4f3b68b01bfac2da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="oracle-sequences"></a>Pořadí Oracle
Zprostředkovatel dat .NET Framework pro Oracle poskytuje podporu pro načítání hodnoty klíče generované serverem Oracle pořadí po provedení vložení pomocí <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server a Oracle podporují vytvoření automaticky zvyšování sloupce, které lze určit jako primární klíče. Tyto hodnoty generované serverem při přidávání řádků do tabulky. V systému SQL Server nastavte vlastnost Identity sloupce; v Oracle vytvoříte pořadí. Rozdíl mezi sloupce s automatickým krokem v systému SQL Server a pořadí v Oracle je, že:  
  
-   Označte sloupec jako sloupec s automatickým krokem v systému SQL Server, a při vložení nového řádku systému SQL Server automaticky vygeneruje nové hodnoty pro sloupec.  
  
-   V Oracle vytvoříte pořadí generovat nové hodnoty pro sloupec v tabulce, ale neexistuje žádné přímé spojení mezi sekvenci a tabulky nebo sloupce. V sekvenci Oracle je objekt, jako jsou tabulky nebo uložené procedury.  
  
 Když vytvoříte pořadí v databázi Oracle, můžete definovat počáteční hodnoty a přírůstek mezi jeho hodnoty. Můžete se také dotázat pořadí nové hodnoty před odesláním nové řádky. To znamená, že váš kód poznáte hodnoty klíče pro nové řádky vložit do databáze.  
  
 Další informace o vytvoření sloupce s automatickým krokem pomocí systému SQL Server a ADO.NET naleznete v tématu [načítání Identity nebo automatické číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md) a [vytváření sloupců AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# ukazuje, jak můžete načíst nové pořadí hodnoty z databáze Oracle. V příkladu odkazuje pořadí v dotazu INSERT INTO používá k odeslání nové řádky a vrátí hodnotu pořadí vygenerováno pomocí klauzule RETURNING byla zavedená v Oracle10g. V příkladu přidáme řadu čekající na vyřízení nové řádky v <xref:System.Data.DataTable> pomocí ADO. Funkce automatického přírůstku je NET ke generování hodnot primárního klíče "zástupný symbol". Všimněte si, že hodnota přírůstku ADO.NET vygenerované pro nový řádek je právě "zástupný symbol". To znamená, že databáze může generovat jiné hodnoty než ty, které generuje ADO.NET.  
  
 Před odesláním čekající vloží do databáze, v příkladu se zobrazí obsah řádky. Potom kód vytvoří novou <xref:System.Data.OracleClient.OracleDataAdapter> objekt a nastaví její <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> a <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> vlastnosti. Tento příklad také poskytuje logiku pro návratové hodnoty generované serverem pomocí výstupní parametry. Potom v příkladu se provede aktualizaci, kterou chcete odeslat čeká na řádky a zobrazí obsah <xref:System.Data.DataTable>.  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
