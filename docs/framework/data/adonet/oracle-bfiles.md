---
title: Soubory Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 214140bb8fcf43154b014ea3db609d355a27af7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794625"
---
# <a name="oracle-bfiles"></a>Soubory Oracle BFILE
Zprostředkovatel dat .NET Framework pro Oracle obsahuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle. <xref:System.Data.OracleClient.OracleType.BFile>  
  
 Datový typ Oracle **BFILE** je typ dat **LOB** Oracle, který obsahuje odkaz na binární data s maximální velikostí 4 gigabajtů. Oracle **BFILE** se liší od jiných datových typů typu Oracle **LOB** v tom, že jeho data se ukládají do fyzického souboru v operačním systému místo na serveru. Všimněte si, že datový typ **BFILE** poskytuje přístup k datům jen pro čtení.  
  
 Další vlastnosti datového typu **BFILE** , které ho odlišují od datového typu **LOB** , jsou tyto:  
  
- Obsahuje nestrukturovaná data.  
  
- Podporuje rozblokování na straně serveru.  
  
- Používá sémantiku kopírování odkazů. Například při provádění operace kopírování na **BFILE**se zkopíruje pouze **BFILE** Lokátor (což je odkaz na soubor). Data v souboru se nekopírují.  
  
 Datový typ **BFILE** by se měl používat pro odkazování na objekty LOBs sy, které jsou velké velikosti, a proto není praktické ukládat do databáze. Při použití datového typu **BFILE** v porovnání s datovým typem **LOB** je zapojená další režie klienta, serveru a komunikace. Přístup k **BFILE** je efektivnější, jenom když potřebujete získat jen malé množství dat. Přístup k objekty LOBs s rezidentu v databázi je efektivnější, pokud potřebujete získat celý objekt.  
  
 Každý objekt **OracleBFile** , který nemá hodnotu null, je přidružen ke dvěma entitám, které definují umístění podkladového fyzického souboru:  
  
1. Objekt adresáře Oracle, který je aliasem databáze pro adresář v systému souborů a  
  
2. Název souboru podkladového fyzického souboru, který je umístěn v adresáři přidruženém k objektu adresáře.  
  
## <a name="example"></a>Příklad  
 Následující C# příklad ukazuje, jak můžete vytvořit **BFILE** v tabulce Oracle a pak ho načíst ve formě objektu **OracleBFile** . Příklad ukazuje použití <xref:System.Data.OracleClient.OracleDataReader> objektu a metod **hledání** a **čtení** **OracleBFile** . Všimněte si, že aby bylo možné tuto ukázku použít, musíte nejprve na serveru Oracle vytvořit adresář s\\názvem "c: \bfiles" a souborem s názvem "MyFile. jpg".  
  
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

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
