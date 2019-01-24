---
title: Načítání binárních dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 2d1b88d25c5c2e94d86c1fed53c472e2b0af493e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643647"
---
# <a name="retrieving-binary-data"></a>Načítání binárních dat
Ve výchozím nastavení **DataReader** načte příchozích dat jako řádek, jakmile celý řádek dat je k dispozici. Binární rozsáhlé objekty (objekty BLOB) potřebovat odlišnému způsobu zacházení však, protože mohou obsahovat GB dat, která nemůže být obsažena v jediném řádku. **Command.ExecuteReader** metoda má přetížení, které bude trvat <xref:System.Data.CommandBehavior> argument, chcete-li změnit výchozí chování **DataReader**. Můžete předat <xref:System.Data.CommandBehavior.SequentialAccess> k **ExecuteReader** metody, chcete-li změnit výchozí chování **DataReader** tak, aby místo načítání řádky dat, bude načítat data postupně po přijetí. To je ideální pro načtení objektů BLOB nebo další velké datové struktury. Všimněte si, že toto chování může záviset na datovém zdroji. Například vrácení objektu BLOB z aplikace Microsoft Access načte celý objekt BLOB se načtena do paměti, spíše než postupně po přijetí.  
  
 Při nastavení **DataReader** používat **SequentialAccess**, je důležité si uvědomit pořadí, ve kterém můžete přístup k polím vrátila. Výchozí chování **DataReader**, což způsobí načtení celý řádek, jakmile je k dispozici, umožňuje přístup k polím vrátil v libovolném pořadí, dokud se na další řádek je pro čtení. Při použití **SequentialAccess** však musí přístup k polím, vrátí **DataReader** v pořadí. Například pokud dotaz vrátí tři sloupce, třetí z nich je objekt BLOB, musí vracet hodnoty polí prvního a druhého před přístup k datům objektu BLOB do třetího pole. Je-li získat přístup k poli třetí před první nebo druhé pole, první a druhé pole hodnoty již nejsou k dispozici. Důvodem je, že **SequentialAccess** byl změněn **DataReader** vrátit data v pořadí a dat není k dispozici po **DataReader** má čtení za ho.  
  
 Při přístupu k datům v poli objektů BLOB, použijte **GetBytes** nebo **provedení metody GetChars** zadaný přistupující objekty **DataReader**, který vyplnit pole s daty. Můžete také použít **GetString** znaková data; ale. Pokud chcete ušetřit prostředky systému nebudete chtít načíst celou hodnotu objektu BLOB do proměnné jeden řetězec. Místo toho můžete zadat konkrétní vyrovnávací paměť o velikosti dat, který se má vrátit a počáteční umístění prvního bajtu nebo znaku číst z vrácená data. **Provedení metody GetBytes** a **provedení metody GetChars** vrátí `long` hodnotu, která představuje počet bajtů nebo znaků, které jsou vráceny. Pokud předáte do pole null **GetBytes** nebo **provedení metody GetChars**, dlouhou hodnotu vrácenou hodnotou celkový počet bajtů nebo znaků v objektu BLOB. Volitelně můžete zadat index v poli jako počáteční pozice pro data čtená.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí ID vydavatele a logo z **pubs** ukázkovou databázi na serveru Microsoft SQL Server. ID vydavatele (`pub_id`) je znak pole, které je logo bitové kopie, což je objekt BLOB. Protože **logo** rastrový obrázek je pole, v příkladu vrací binární data s využitím **GetBytes**. Všimněte si, že ID vydavatele přistupuje pro aktuální řádek dat před loga, protože pole musí mít přístup postupně.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Práce s čtečky dat](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)
- [Binární a vysoké hodnoty na SQL Serveru](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
