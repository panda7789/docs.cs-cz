---
title: Soubory Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149437"
---
# <a name="oracle-bfiles"></a>Soubory Oracle BFILE
Zprostředkovatel dat rozhraní .NET Framework <xref:System.Data.OracleClient.OracleBFile> pro oracle zahrnuje třídu, <xref:System.Data.OracleClient.OracleType.BFile> která se používá pro práci s datovým typem Oracle.  
  
 Datový typ Oracle **BFILE** je datový typ Oracle **LOB,** který obsahuje odkaz na binární data s maximální velikostí 4 gigabajty. Oracle **BFILE** se liší od ostatních datových typů Oracle **LOB** v tom, že jeho data jsou uložena ve fyzickém souboru v operačním systému namísto na serveru. Všimněte si, že datový typ **BFILE** poskytuje přístup jen pro čtení k datům.  
  
 Další charakteristiky datového typu **BFILE,** které jej odlišují od datového typu **LOB,** jsou, že:  
  
- Obsahuje nestrukturovaná data.  
  
- Podporuje bloků na straně serveru.  
  
- Používá sémantiku referenční kopie. Pokud například provedete operaci kopírování na **BFILE**, zkopíruje se pouze lokátor **BFILE** (což je odkaz na soubor). Data v souboru nejsou zkopírována.  
  
 Datový typ **BFILE** by měl být použit pro odkazování na loby, které jsou velké velikosti a proto není praktické ukládat v databázi. Při použití datového typu **BFILE** ve srovnání s datovým typem **LOB** se jedná o další režii klienta, serveru a komunikace. Je efektivnější přístup k **BFILE,** pokud potřebujete pouze získat malé množství dat. Je efektivnější přístup k databázi rezidentní LOBs, pokud potřebujete získat celý objekt.  
  
 Každý objekt **OracleBFile,** který není null, je přidružen ke dvěma entitam, které definují umístění základního fyzického souboru:  
  
1. Objekt Oracle DIRECTORY, který je aliasem databáze pro adresář v systému souborů, a  
  
2. Název souboru podkladového fyzického souboru, který je umístěn v adresáři přidruženém k objektu DIRECTORY.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# ukazuje, jak můžete vytvořit **BFILE** v tabulce Oracle a pak jej načíst ve formě objektu **OracleBFile.** Příklad ukazuje použití <xref:System.Data.OracleClient.OracleDataReader> objektu a **metody OracleBFile** **Seek** a **Read.** Všimněte si, že chcete-li použít tuto ukázku,\\musíte nejprve vytvořit adresář s názvem "c: \bfiles" a soubor s názvem "MyFile.jpg" na serveru Oracle.  
  
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

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
