---
title: Čtení dat objektu ze souboru XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167815"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="59e05-102">Čtení dat objektu ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="59e05-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="59e05-103">Tento příklad čte data objektu, která byla <xref:System.Xml.Serialization.XmlSerializer> dříve zapsána do souboru XML pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="59e05-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59e05-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="59e05-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="59e05-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="59e05-105">Compiling the Code</span></span>  
<span data-ttu-id="59e05-106">Nahraďte název souboru "c:\temp\SerializationOverview.xml" názvem souboru obsahujícího serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="59e05-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="59e05-107">Další informace o serializaci dat naleznete v tématu [Jak zapsat data objektů do souboru XML (C#).](./how-to-write-object-data-to-an-xml-file.md)</span><span class="sxs-lookup"><span data-stu-id="59e05-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="59e05-108">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="59e05-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="59e05-109">Dekonstruovány jsou pouze veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="59e05-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="59e05-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="59e05-110">Robust Programming</span></span>  
 <span data-ttu-id="59e05-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="59e05-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="59e05-112">Třída serializované nemá veřejné, parametrless konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="59e05-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="59e05-113">Data v souboru nepředstavují data z třídy, která má být rekonstruována.</span><span class="sxs-lookup"><span data-stu-id="59e05-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="59e05-114">Soubor neexistuje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="59e05-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="59e05-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59e05-115">.NET Framework Security</span></span>  
 <span data-ttu-id="59e05-116">Vždy ověřujte vstupy a nikdy nerekonstruujte data z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="59e05-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="59e05-117">Znovu vytvořený objekt je spuštěn v místním počítači s oprávněními kódu, který jej rekonstruoval.</span><span class="sxs-lookup"><span data-stu-id="59e05-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="59e05-118">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="59e05-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e05-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="59e05-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="59e05-120">Jak zapisovat data objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="59e05-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="59e05-121">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="59e05-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="59e05-122">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="59e05-122">C# Programming Guide</span></span>](../../index.md)
