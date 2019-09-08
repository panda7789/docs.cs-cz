---
title: Načítání binárních dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 9acda6631e17031a81ba06d9530739a586fac7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794429"
---
# <a name="retrieving-binary-data"></a>Načítání binárních dat
Ve výchozím nastavení datový objekt **DataReader** načte příchozí data jako řádek, jakmile bude k dispozici celý řádek dat. Binární rozsáhlé objekty (BLOB) vyžadují jiné zacházení, protože mohou obsahovat gigabajty dat, které nemohou být obsaženy na jednom řádku. Metoda **Command. ExecuteReader** má přetížení, které převezme <xref:System.Data.CommandBehavior> argument pro úpravu výchozího chování objektu **DataReader**. Chcete-li <xref:System.Data.CommandBehavior.SequentialAccess> změnit výchozí chování objektu **DataReader** , můžete předat metodě **ExecuteReader** , aby se místo načítání řádků dat načetla data postupně po přijetí. To je ideální pro načítání objektů BLOB nebo jiných velkých datových struktur. Všimněte si, že toto chování může záviset na zdroji dat. Například vrácení objektu BLOB z aplikace Microsoft Access načte celý objekt BLOB, který se načítá do paměti, a ne postupně, jak je přijatý.  
  
 Při nastavování objektu **DataReader** pro použití **SequentialAccess**je důležité poznamenat sekvenci, ve které se budou vracet pole. Výchozí chování objektu **DataReader**, který načte celý řádek, jakmile je k dispozici, umožňuje přístup k polím vráceným v libovolném pořadí, dokud nebude načten další řádek. Při použití **SequentialAccess** ale musíte získat přístup k polím vráceným pomocí objektu **DataReader** v daném pořadí. Například pokud váš dotaz vrátí tři sloupce, třetí z nich je objekt BLOB, je nutné vrátit hodnoty prvních a druhých polí před přístupem k datům objektu BLOB ve třetím poli. Pokud přistupujete k třetímu poli před prvním nebo druhým polem, hodnoty v polích First a Second nebudou již k dispozici. Důvodem je to, že **SequentialAccess** změnil **DataReader** tak, aby vracel data v sekvenci, a data nejsou k dispozici poté, co je v objektu **DataReader** načteno za poslední.  
  
 Při přístupu k datům v poli objektu BLOB použijte přístupové objekty typovaného typu **GetBytes** nebo **GetChars** objektu **DataReader**, který plní pole daty. Pro znaková data můžete také použít **GetString** ; naopak. Chcete-li ušetřit systémové prostředky, nebudete pravděpodobně chtít načíst celou hodnotu objektu BLOB do jediné řetězcové proměnné. Místo toho můžete zadat konkrétní velikost vyrovnávací paměti, která se má vrátit, a počáteční umístění prvního bajtu nebo znaku, který se má načíst ze vrácených dat. **GetByte** a **GetChars** vrátí `long` hodnotu, která představuje počet vrácených bajtů nebo znaků. Pokud předáte pole hodnoty null do **GetBytes** nebo **GetChars**, vrátí se hodnota Long, což bude celkový počet bajtů nebo znaků v objektu BLOB. Volitelně můžete zadat index v poli jako počáteční pozici pro čtená data.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí ID vydavatele a logo z ukázkové databáze **pubs** v Microsoft SQL Server. Vydavatel ID (`pub_id`) je pole znaků a logo je obrázek, který je objektem BLOB. Vzhledem k tomu, že pole **loga** je rastrový obrázek, příklad vrátí binární data pomocí **GetBytes**. Všimněte si, že ID vydavatele je k dispozici pro aktuální řádek dat před logem, protože pole musí být přistupovaná sekvenčně.  
  
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

- [Binární a vysoké hodnoty na SQL Serveru](./sql/sql-server-binary-and-large-value-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
