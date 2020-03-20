---
title: Sekvence Oracle
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: d6e6bb51b8bd317c7161500b89993be689659fad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149411"
---
# <a name="oracle-sequences"></a>Sekvence Oracle
Zprostředkovatel dat rozhraní .NET Framework pro oracle poskytuje podporu pro načítání hodnot klíče Oracle Sequence <xref:System.Data.OracleClient.OracleDataAdapter>generovaných serverem po provedení vložení pomocí rozhraní .  
  
 SQL Server a Oracle podporují vytváření automaticky se rozvíjejících sloupců, které lze označit jako primární klíče. Tyto hodnoty jsou generovány serverem jako řádky jsou přidány do tabulky. V SQL Server nastavíte identity vlastnost sloupce; v oracle vytvoříte Sekvenci. Rozdíl mezi sloupci automatického přírůstku v sql serveru a sekvencemi v oracle je, že:  
  
- Na serveru SQL Server označíte sloupec jako sloupec automatického přírůstku a SQL Server automaticky vygeneruje nové hodnoty pro sloupec při vložení nového řádku.  
  
- V oracle vytvořit posloupnost generovat nové hodnoty pro sloupec v tabulce, ale neexistuje žádné přímé propojení mezi sekvenci a tabulka nebo sloupec. Oracle sekvence je objekt, jako je tabulka nebo uložená procedura.  
  
 Při vytváření sekvence v databázi Oracle můžete definovat jeho počáteční hodnotu a přírůstek mezi jejími hodnotami. Můžete také dotaz pořadí pro nové hodnoty před odesláním nové řádky. To znamená, že váš kód může rozpoznat hodnoty klíče pro nové řádky před jejich vložením do databáze.  
  
 Další informace o vytváření sloupců automatického přírůstku pomocí serveru SQL Server a ADO.NET naleznete v [tématu Načítání hodnot identity nebo automatického čísla](retrieving-identity-or-autonumber-values.md) a [vytváření sloupců automatického přírůstku](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# ukazuje, jak můžete načíst nové sekvenční hodnoty z databáze Oracle. Příklad odkazuje na sekvenci v dotazu INSERT INTO použiték odeslání nových řádků a potom vrátí hodnotu sekvence generované pomocí klauzule RETURNING zavedené v Oracle10g. Příklad přidá řadu čekající nové řádky <xref:System.Data.DataTable> v pomocí ADO. NET je auto-přírůstek funkce generovat "zástupný" hodnoty primárního klíče. Všimněte si, že hodnota přírůstku ADO.NET generována pro nový řádek je pouze "zástupný symbol". To znamená, že databáze může generovat různé hodnoty z nich, ADO.NET generuje.  
  
 Před odesláním čekající vloží do databáze, v příkladu zobrazí obsah řádků. Potom kód vytvoří nový <xref:System.Data.OracleClient.OracleDataAdapter> objekt a <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> nastaví jeho a vlastnosti. <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> Příklad také poskytuje logiku vrátit hodnoty generované serverem pomocí výstupních parametrů. Potom příklad provede aktualizaci odeslat čekající řádky a zobrazí <xref:System.Data.DataTable>obsah .  
  
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

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
