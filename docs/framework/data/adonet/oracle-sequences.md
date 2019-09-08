---
title: Sekvence Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 772aeda94215ccc8e1eff0e1145ed0399791197d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794596"
---
# <a name="oracle-sequences"></a>Sekvence Oracle
Zprostředkovatel dat .NET Framework pro Oracle poskytuje podporu pro načítání hodnot sekvence Oracle generovaných serverem po provedení vložení pomocí <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server a Oracle podporují vytváření automaticky rostoucích sloupců, které je možné určit jako primární klíče. Tyto hodnoty jsou generovány serverem při přidávání řádků do tabulky. V SQL Server nastavíte vlastnost identity sloupce. v Oracle vytvoříte sekvenci. Rozdíl mezi sloupci s automatickým navýšením v SQL Server a posloupnosti v Oracle je následující:  
  
- V SQL Server označíte sloupec jako sloupec s automatickým přírůstkem a SQL Server automaticky generuje nové hodnoty pro sloupec při vložení nového řádku.  
  
- V Oracle vytvoříte sekvenci, která generuje nové hodnoty pro sloupec v tabulce, ale neexistuje žádné přímé propojení mezi sekvencí a tabulkou nebo sloupcem. Sekvence Oracle je objekt, jako je tabulka nebo uložená procedura.  
  
 Když vytvoříte sekvenci v databázi Oracle, můžete definovat její počáteční hodnotu a přírůstek mezi jejími hodnotami. Před odesláním nových řádků můžete také zadat dotaz na nové hodnoty. To znamená, že váš kód může rozpoznat klíčové hodnoty pro nové řádky předtím, než je vložíte do databáze.  
  
 Další informace o vytváření sloupců s automatickým přírůstkem pomocí SQL Server a ADO.NET naleznete v tématu [načítání identity nebo Autonumber Values](retrieving-identity-or-autonumber-values.md) a [vytváření sloupců AutoIncrement](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Příklad  
 Následující C# příklad ukazuje, jak lze načíst nové hodnoty sekvence z databáze Oracle. Příklad odkazuje na pořadí v dotazu INSERT INTO použitém k odeslání nových řádků a vrátí hodnotu sekvence generovanou pomocí klauzule vracející se zavedené v Oracle10g. Tento příklad přidá řadu nevyřízených nových řádků v <xref:System.Data.DataTable> objektu pomocí ADO. Funkce automatického zvyšování hodnoty netto pro generování zástupných hodnot primárního klíče Všimněte si, že přírůstková hodnota ADO.NET vygenerovaná pro nový řádek je pouze "zástupný". To znamená, že databáze může generovat jiné hodnoty z těch, které ADO.NET generuje.  
  
 Před odesláním nedokončených vložení do databáze je v příkladu zobrazen obsah řádků. Potom kód vytvoří nový <xref:System.Data.OracleClient.OracleDataAdapter> objekt a nastaví jeho <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> vlastnosti a. Tento příklad také poskytuje logiku pro vrácení hodnot generovaných serverem pomocí výstupních parametrů. Pak tento příklad provede aktualizaci k odeslání nedokončených řádků a zobrazí obsah <xref:System.Data.DataTable>.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
