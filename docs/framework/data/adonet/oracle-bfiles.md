---
title: Oracle BFILEs
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: bb0a7dad2b7919130097ddd689739b8d17557ea1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-bfiles"></a>Oracle BFILEs
Zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleBFile> třídy, která se používá pro práci s Oracle <xref:System.Data.OracleClient.OracleType.BFile> datového typu.  
  
 Oracle **BFILE** datový typ je Oracle **obchodní** datový typ, který obsahuje odkaz na binární data s maximální velikost 4 GB. Oracle **BFILE** se liší od jiných Oracle **obchodní** datové typy, že data jsou uložena v fyzického souboru operačního systému místo na serveru. Všimněte si, že **BFILE** datový typ poskytuje přístup jen pro čtení k datům.  
  
 Další vlastnosti **BFILE** datový typ, který odlišující jej od **obchodní** datový typ jsou to:  
  
-   Obsahuje Nestrukturovaná data.  
  
-   Podporuje rozdělování na straně serveru.  
  
-   Používá referenční sémantiku kopírování. Například, pokud provádíte na operace kopírování **BFILE**, jenom **BFILE** zkopíruje Lokátor (což je odkaz na soubor). Data v souboru není zkopírována.  
  
 **BFILE** datový typ měli použít pro odkazování na objekty LOBs, které jsou velké a proto není potřeba ukládat v databázi. Další režii klienta, komunikace a server je zahrnuta při použití **BFILE** datový typ ve srovnání s **obchodní** datového typu. Přístup je efektivnější **BFILE** Pokud potřebujete získat malé množství dat. Je efektivnější k přístupu k databázi rezidentní objekty LOBs, pokud je nutné získat celý objekt.  
  
 Každý NENULOVOU **OracleBFile** objekt je přidružený ke dvě entity, které definují umístění základní fyzický soubor:  
  
1.  Objekt Oracle adresář, který je alias databáze pro adresář v systému souborů, a  
  
2.  Název souboru základní fyzického souboru, který je umístěný v adresáři přidružená k objektu adresáře.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# ukazuje, jak můžete vytvořit **BFILE** v Oracle tabulky a následně načíst ve formě **OracleBFile** objektu. Tento příklad ukazuje, jak pomocí <xref:System.Data.OracleClient.OracleDataReader> objektu a **OracleBFile** **Seek** a **čtení** metody. Všimněte si, že chcete-li použít tuto ukázku, musíte nejprve vytvořit adresář s názvem "c:\\\bfiles" a soubor s názvem "MyFile.jpg" na serveru Oracle.  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
