---
title: "Načítání binární Data"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b32002b8bb9b1eaf7a72a8fac306ecdd5f2e5931
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-binary-data"></a>Načítání binární Data
Ve výchozím nastavení **DataReader** načte příchozích dat jako řádek, jakmile celý řádek dat je k dispozici. Binární rozsáhlé objekty (objekty BLOB) vyžadují odlišné zacházení, ale, protože obsahují GB dat, které nemůžou být obsažené ve jeden řádek. **Command.ExecuteReader** metoda má přetížení, které bude trvat <xref:System.Data.CommandBehavior> argument změnit výchozí chování **DataReader –**. Můžete předat <xref:System.Data.CommandBehavior.SequentialAccess> k **ExecuteReader** metoda změnit výchozí chování **DataReader** tak, aby místo načítání řádky dat, načte data sekvenčně. to znamená přijetí. To je ideální pro načítání objektů BLOB nebo další velké datové struktury. Všimněte si, že toto chování může záviset na zdroj dat. Například vrací objekt BLOB z aplikace Microsoft Access načte celý objekt BLOB se načtena do paměti, spíše než postupně přijetí.  
  
 Při nastavení **DataReader –** používat **SequentialAccess**, je důležité si uvědomit pořadí, ve kterém přístup vrátil pole. Výchozí chování **DataReader –**, což způsobí načtení celý řádek, jakmile je k dispozici, vám umožní přistupovat k pole vrátila v libovolném pořadí, až na další řádek je pro čtení. Při použití **SequentialAccess** však musí přístup pole vrácené **DataReader** v pořadí. Například pokud dotaz vrátí tři sloupce, třetí by se objekt BLOB, musí vracet hodnoty polí první a druhý před přístup k datům objektu BLOB ve třetím poli. Pokud máte přístup k poli třetí před první nebo druhé pole, hodnoty polí první a druhý již nejsou k dispozici. Důvodem je, že **SequentialAccess** změnil **DataReader –** vrátit data v pořadí a dat není k dispozici po **DataReader** má čtení za ho.  
  
 Při přístupu k datům v poli objektů BLOB, použijte **GetBytes** nebo **GetChars** zadali přístupových objektů **DataReader –**, který vyplnit pole s daty. Můžete také použít **GetString** znaková data; ale. Pokud chcete ušetřit prostředky systému možná nebudete chtít načíst hodnotu celý objekt BLOB do jednoho řetězce proměnné. Místo toho můžete zadat konkrétní vyrovnávací paměť o velikosti dat, který se má vrátit a výchozí umístění pro první bajt nebo znak, který má být čtení z vrácená data. **GetBytes** a **GetChars** vrátí `long` hodnotu, která představuje počet bajtů nebo znaků vrátila. Pokud předáte hodnotu null pole pro **GetBytes** nebo **GetChars**, dlouhou hodnotu vrátí, bude celkový počet bajtů nebo znaků v objektu BLOB. Volitelně můžete zadat index v poli jako počáteční pozice pro data, který je čten.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrací ID vydavatele a logo z **pubs** ukázkové databáze v systému Microsoft SQL Server. ID vydavatele (`pub_id`) je znak, a je logo je obrázek, který je objekt BLOB. Protože **logo** pole rastr, v příkladu vrací binární data pomocí **GetBytes**. Všimněte si, že ID vydavatele je přístupné pro aktuální řádek dat před loga, protože pole musí mít přístup postupně.  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s DataReaders](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Binární a vysoké hodnoty na SQL Serveru](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
