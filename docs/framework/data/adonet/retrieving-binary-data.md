---
title: Načítání binárních dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: c914a9b0780e2e87e177502b0f9faff0e7c4b617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149047"
---
# <a name="retrieving-binary-data"></a>Načítání binárních dat
Ve výchozím nastavení **datareader** načte příchozí data jako řádek, jakmile je k dispozici celý řádek dat. Binární velké objekty (BLOB) potřebují různé zpracování, ale protože mohou obsahovat gigabajty dat, které nemohou být obsaženy v jednom řádku. Metoda **Command.ExecuteReader** má přetížení, které <xref:System.Data.CommandBehavior> bude trvat argument změnit výchozí chování **DataReader**. Můžete předat <xref:System.Data.CommandBehavior.SequentialAccess> **ExecuteReader** metoda změnit výchozí chování **DataReader** tak, aby namísto načítání řádků dat, bude načítat data postupně, jak je přijata. To je ideální pro načítání objektů BLOB nebo jiných velkých datových struktur. Všimněte si, že toto chování může záviset na zdroj dat. Například vrácení objektu BLOB z aplikace Microsoft Access načte celý objekt BLOB načítají do paměti, nikoli postupně, jak je přijata.  
  
 Při nastavování **datareader** používat **SequentialAccess**, je důležité si uvědomit pořadí, ve kterém máte přístup k polím vrácena. Výchozí chování **DataReader**, který načte celý řádek, jakmile je k dispozici, umožňuje přístup k polím vráceným v libovolném pořadí, dokud se nepřečte další řádek. Při použití **SequentialAccess** však musíte přistupovat k polím vráceným **datovou čtečkou** v pořadí. Například pokud dotaz vrátí tři sloupce, z nichž třetí je OBJEKT BLOB, je nutné vrátit hodnoty první a druhé pole před přístupem k datům BLOB ve třetím poli. Pokud přistupujete ke třetímu poli před prvním nebo druhým polem, první a druhé hodnoty polí již nebudou k dispozici. Důvodem **je, že Sekční přístup** upravil **DataReader** vrátit data v pořadí a data není k dispozici po **DataReader** má číst minulosti.  
  
 Při přístupu k datům v poli BLOB použijte přístupové objekty typu **GetBytes** nebo **GetChars** **aplikace DataReader**, které vyplní pole daty. Můžete také použít **GetString** pro data znaků; Nicméně. chcete-li ušetřit systémové prostředky, možná nebudete chtít načíst celou hodnotu BLOB do proměnné jednoho řetězce. Místo toho můžete zadat konkrétní velikost vyrovnávací paměti dat, která mají být vrácena, a počáteční umístění pro první bajt nebo znak, který má být přečten z vrácených dat. **GetBytes** a **GetChars** `long` vrátí hodnotu, která představuje počet bajtů nebo znaků vrácených. Pokud předáte nulové pole **GetBytes** nebo **GetChars**, bude vrácená dlouhá hodnota celkový počet bajtů nebo znaků v objektu BLOB. Volitelně můžete zadat index v poli jako počáteční pozici pro čtená data.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí ID vydavatele a logo z ukázkové databáze **pubs** v Microsoft SQL Server. ID vydavatele`pub_id`( ) je pole znaků a logo je obrázek, což je objekt BLOB. Vzhledem k tomu, že pole **loga** je bitmapa, příklad vrátí binární data pomocí **GetBytes**. Všimněte si, že ID vydavatele je přístupná pro aktuální řádek dat před logem, protože pole musí být přístupné postupně.  
  
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

- [Binární a vysoké hodnoty na SQL Serveru](./sql/sql-server-binary-and-large-value-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
