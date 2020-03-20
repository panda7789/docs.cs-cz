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
# <a name="retrieving-binary-data"></a><span data-ttu-id="9dc5c-102">Načítání binárních dat</span><span class="sxs-lookup"><span data-stu-id="9dc5c-102">Retrieving Binary Data</span></span>
<span data-ttu-id="9dc5c-103">Ve výchozím nastavení **datareader** načte příchozí data jako řádek, jakmile je k dispozici celý řádek dat.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="9dc5c-104">Binární velké objekty (BLOB) potřebují různé zpracování, ale protože mohou obsahovat gigabajty dat, které nemohou být obsaženy v jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="9dc5c-105">Metoda **Command.ExecuteReader** má přetížení, které <xref:System.Data.CommandBehavior> bude trvat argument změnit výchozí chování **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="9dc5c-106">Můžete předat <xref:System.Data.CommandBehavior.SequentialAccess> **ExecuteReader** metoda změnit výchozí chování **DataReader** tak, aby namísto načítání řádků dat, bude načítat data postupně, jak je přijata.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="9dc5c-107">To je ideální pro načítání objektů BLOB nebo jiných velkých datových struktur.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="9dc5c-108">Všimněte si, že toto chování může záviset na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="9dc5c-109">Například vrácení objektu BLOB z aplikace Microsoft Access načte celý objekt BLOB načítají do paměti, nikoli postupně, jak je přijata.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="9dc5c-110">Při nastavování **datareader** používat **SequentialAccess**, je důležité si uvědomit pořadí, ve kterém máte přístup k polím vrácena.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="9dc5c-111">Výchozí chování **DataReader**, který načte celý řádek, jakmile je k dispozici, umožňuje přístup k polím vráceným v libovolném pořadí, dokud se nepřečte další řádek.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="9dc5c-112">Při použití **SequentialAccess** však musíte přistupovat k polím vráceným **datovou čtečkou** v pořadí.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="9dc5c-113">Například pokud dotaz vrátí tři sloupce, z nichž třetí je OBJEKT BLOB, je nutné vrátit hodnoty první a druhé pole před přístupem k datům BLOB ve třetím poli.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="9dc5c-114">Pokud přistupujete ke třetímu poli před prvním nebo druhým polem, první a druhé hodnoty polí již nebudou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="9dc5c-115">Důvodem **je, že Sekční přístup** upravil **DataReader** vrátit data v pořadí a data není k dispozici po **DataReader** má číst minulosti.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="9dc5c-116">Při přístupu k datům v poli BLOB použijte přístupové objekty typu **GetBytes** nebo **GetChars** **aplikace DataReader**, které vyplní pole daty.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="9dc5c-117">Můžete také použít **GetString** pro data znaků; Nicméně.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="9dc5c-118">chcete-li ušetřit systémové prostředky, možná nebudete chtít načíst celou hodnotu BLOB do proměnné jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="9dc5c-119">Místo toho můžete zadat konkrétní velikost vyrovnávací paměti dat, která mají být vrácena, a počáteční umístění pro první bajt nebo znak, který má být přečten z vrácených dat.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="9dc5c-120">**GetBytes** a **GetChars** `long` vrátí hodnotu, která představuje počet bajtů nebo znaků vrácených.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="9dc5c-121">Pokud předáte nulové pole **GetBytes** nebo **GetChars**, bude vrácená dlouhá hodnota celkový počet bajtů nebo znaků v objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="9dc5c-122">Volitelně můžete zadat index v poli jako počáteční pozici pro čtená data.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dc5c-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="9dc5c-123">Example</span></span>  
 <span data-ttu-id="9dc5c-124">Následující příklad vrátí ID vydavatele a logo z ukázkové databáze **pubs** v Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="9dc5c-125">ID vydavatele`pub_id`( ) je pole znaků a logo je obrázek, což je objekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="9dc5c-126">Vzhledem k tomu, že pole **loga** je bitmapa, příklad vrátí binární data pomocí **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="9dc5c-127">Všimněte si, že ID vydavatele je přístupná pro aktuální řádek dat před logem, protože pole musí být přístupné postupně.</span><span class="sxs-lookup"><span data-stu-id="9dc5c-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dc5c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dc5c-128">See also</span></span>

- [<span data-ttu-id="9dc5c-129">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="9dc5c-129">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="9dc5c-130">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9dc5c-130">ADO.NET Overview</span></span>](ado-net-overview.md)
