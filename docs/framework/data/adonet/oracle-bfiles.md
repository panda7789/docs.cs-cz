---
title: Soubory Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 5bb9f7e67016cf4b1d467935fe302ab4a40edbfa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304464"
---
# <a name="oracle-bfiles"></a>Soubory Oracle BFILE
Zprostředkovatel dat .NET Framework pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s Oracle <xref:System.Data.OracleClient.OracleType.BFile> datového typu.  
  
 Oracle **BFILE** je datový typ Oracle **LOB** datový typ, který obsahuje odkaz na binárních dat a maximální velikost 4 GB. Oracle **BFILE** se liší od jiných Oracle **LOB** datové typy v tom, že jeho data se ukládají v fyzický soubor v operačním systému místo na serveru. Všimněte si, **BFILE** datový typ poskytuje přístup jen pro čtení k datům.  
  
 Další vlastnosti **BFILE** datový typ, který odlišit od **LOB** se, že datový typ:  
  
-   Obsahuje Nestrukturovaná data.  
  
-   Podporuje bloků na straně serveru.  
  
-   Odkazovat na používá sémantiku kopírování. Například, pokud provádíte operaci kopírování na **BFILE**, pouze **BFILE** zkopíruje Lokátor (což je odkaz na soubor). Data v souboru není zkopírován.  
  
 **BFILE** datový typ by měl použít pro odkazování na objekty LOBs, které jsou velké a proto není praktické ukládá do databáze. Další režii klienta, server a komunikace je zahrnuta při použití **BFILE** datový typ ve srovnání s **LOB** datového typu. Je mnohem efektivnější pro přístup k **BFILE** Pokud potřebujete získat malé množství dat. To je mnohem efektivnější pro přístup k databázi rezidentní objekty LOBs, pokud je třeba získat celý objekt.  
  
 Každý NENULOVOU **OracleBFile** objekt je přidružený dvě entity, které definují umístění podkladový fyzický soubor:  
  
1. Objekt adresáře Oracle, což je alias databáze pro adresář v systému souborů, a  
  
2. Název souboru základního fyzického souboru, který je umístěn v adresáři přidružená k objektu adresáře.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# ukazuje, jak můžete vytvořit **BFILE** Oracle tabulce a potom ho načíst ve formě **OracleBFile** objektu. Tento příklad ukazuje použití <xref:System.Data.OracleClient.OracleDataReader> objektu a **OracleBFile** **Seek** a **čtení** metody. Všimněte si, že chcete-li použít tento příklad, musíte nejprve vytvořit adresář s názvem "c:\\\bfiles" a soubor s názvem "MyFile.jpg" na serveru Oracle.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
