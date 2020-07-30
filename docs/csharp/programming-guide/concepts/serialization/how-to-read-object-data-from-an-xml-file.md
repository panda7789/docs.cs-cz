---
title: Čtení dat objektů ze souboru XML (C#)
description: Tento příklad v jazyce C# čte data objektů, která byla dříve zapsána do souboru XML pomocí třídy XmlSerializer.
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 525a93812279756b3802d43d85bb5e61d8f7415e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302786"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="f3ba8-103">Čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f3ba8-103">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="f3ba8-104">Tento příklad načte data objektů, která byla dříve zapsána do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ba8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3ba8-105">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3ba8-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f3ba8-106">Compiling the Code</span></span>  
<span data-ttu-id="f3ba8-107">Nahraďte název souboru "c:\temp\SerializationOverview.xml" názvem souboru, který obsahuje Serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="f3ba8-108">Další informace o serializaci dat naleznete v tématu [jak zapisovat data objektů do souboru XML (C#)](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f3ba8-108">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="f3ba8-109">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="f3ba8-110">Pouze veřejné vlastnosti a pole jsou deserializovány.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f3ba8-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f3ba8-111">Robust Programming</span></span>  
 <span data-ttu-id="f3ba8-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f3ba8-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f3ba8-113">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="f3ba8-114">Data v souboru reprezentují data z třídy, která se má deserializovat.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="f3ba8-115">Soubor neexistuje ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="f3ba8-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="f3ba8-116">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="f3ba8-116">.NET Security</span></span>  
 <span data-ttu-id="f3ba8-117">Vždy ověřte vstupy a nikdy neserializovat data z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="f3ba8-118">Nově vytvořený objekt je spuštěn v místním počítači s oprávněním kódu, který jej deserializovat.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="f3ba8-119">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="f3ba8-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ba8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3ba8-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="f3ba8-121">Zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f3ba8-121">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="f3ba8-122">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="f3ba8-122">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="f3ba8-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f3ba8-123">C# Programming Guide</span></span>](../../index.md)
