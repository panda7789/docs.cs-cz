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
# <a name="retrieving-binary-data"></a><span data-ttu-id="6f3cf-102">Načítání binárních dat</span><span class="sxs-lookup"><span data-stu-id="6f3cf-102">Retrieving Binary Data</span></span>
<span data-ttu-id="6f3cf-103">Ve výchozím nastavení datový objekt **DataReader** načte příchozí data jako řádek, jakmile bude k dispozici celý řádek dat.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="6f3cf-104">Binární rozsáhlé objekty (BLOB) vyžadují jiné zacházení, protože mohou obsahovat gigabajty dat, které nemohou být obsaženy na jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="6f3cf-105">Metoda **Command. ExecuteReader** má přetížení, které převezme <xref:System.Data.CommandBehavior> argument pro úpravu výchozího chování objektu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="6f3cf-106">Chcete-li <xref:System.Data.CommandBehavior.SequentialAccess> změnit výchozí chování objektu **DataReader** , můžete předat metodě **ExecuteReader** , aby se místo načítání řádků dat načetla data postupně po přijetí.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="6f3cf-107">To je ideální pro načítání objektů BLOB nebo jiných velkých datových struktur.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="6f3cf-108">Všimněte si, že toto chování může záviset na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="6f3cf-109">Například vrácení objektu BLOB z aplikace Microsoft Access načte celý objekt BLOB, který se načítá do paměti, a ne postupně, jak je přijatý.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="6f3cf-110">Při nastavování objektu **DataReader** pro použití **SequentialAccess**je důležité poznamenat sekvenci, ve které se budou vracet pole.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="6f3cf-111">Výchozí chování objektu **DataReader**, který načte celý řádek, jakmile je k dispozici, umožňuje přístup k polím vráceným v libovolném pořadí, dokud nebude načten další řádek.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="6f3cf-112">Při použití **SequentialAccess** ale musíte získat přístup k polím vráceným pomocí objektu **DataReader** v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="6f3cf-113">Například pokud váš dotaz vrátí tři sloupce, třetí z nich je objekt BLOB, je nutné vrátit hodnoty prvních a druhých polí před přístupem k datům objektu BLOB ve třetím poli.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="6f3cf-114">Pokud přistupujete k třetímu poli před prvním nebo druhým polem, hodnoty v polích First a Second nebudou již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="6f3cf-115">Důvodem je to, že **SequentialAccess** změnil **DataReader** tak, aby vracel data v sekvenci, a data nejsou k dispozici poté, co je v objektu **DataReader** načteno za poslední.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="6f3cf-116">Při přístupu k datům v poli objektu BLOB použijte přístupové objekty typovaného typu **GetBytes** nebo **GetChars** objektu **DataReader**, který plní pole daty.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="6f3cf-117">Pro znaková data můžete také použít **GetString** ; naopak.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="6f3cf-118">Chcete-li ušetřit systémové prostředky, nebudete pravděpodobně chtít načíst celou hodnotu objektu BLOB do jediné řetězcové proměnné.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="6f3cf-119">Místo toho můžete zadat konkrétní velikost vyrovnávací paměti, která se má vrátit, a počáteční umístění prvního bajtu nebo znaku, který se má načíst ze vrácených dat.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="6f3cf-120">**GetByte** a **GetChars** vrátí `long` hodnotu, která představuje počet vrácených bajtů nebo znaků.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="6f3cf-121">Pokud předáte pole hodnoty null do **GetBytes** nebo **GetChars**, vrátí se hodnota Long, což bude celkový počet bajtů nebo znaků v objektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="6f3cf-122">Volitelně můžete zadat index v poli jako počáteční pozici pro čtená data.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f3cf-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f3cf-123">Example</span></span>  
 <span data-ttu-id="6f3cf-124">Následující příklad vrátí ID vydavatele a logo z ukázkové databáze **pubs** v Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="6f3cf-125">Vydavatel ID (`pub_id`) je pole znaků a logo je obrázek, který je objektem BLOB.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="6f3cf-126">Vzhledem k tomu, že pole **loga** je rastrový obrázek, příklad vrátí binární data pomocí **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="6f3cf-127">Všimněte si, že ID vydavatele je k dispozici pro aktuální řádek dat před logem, protože pole musí být přistupovaná sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="6f3cf-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f3cf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f3cf-128">See also</span></span>

- [<span data-ttu-id="6f3cf-129">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="6f3cf-129">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="6f3cf-130">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f3cf-130">ADO.NET Overview</span></span>](ado-net-overview.md)
