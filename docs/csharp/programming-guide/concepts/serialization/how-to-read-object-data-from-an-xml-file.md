---
title: 'Postupy: čtení dat objektů ze souboru XML (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 7c3bad56c6a0bee51262586aea4ce97ff0491f24
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083933"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="17d9c-102">Postupy: čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="17d9c-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="17d9c-103">V tomto příkladu čte data objektu, který se předtím zapsala do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="17d9c-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d9c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="17d9c-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="17d9c-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="17d9c-105">Compiling the Code</span></span>  
 <span data-ttu-id="17d9c-106">Název souboru "c:\temp\SerializationOverview.xml" nahraďte názvem souboru, který obsahuje serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="17d9c-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="17d9c-107">Další informace o serializaci dat najdete v tématu [postupy: zápis dat objektů do souboru XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="17d9c-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="17d9c-108">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="17d9c-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="17d9c-109">Pouze veřejné vlastnosti a pole se deserializovat.</span><span class="sxs-lookup"><span data-stu-id="17d9c-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="17d9c-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="17d9c-110">Robust Programming</span></span>  
 <span data-ttu-id="17d9c-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="17d9c-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="17d9c-112">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="17d9c-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="17d9c-113">Data v souboru nepředstavuje data ze třídy k deserializaci.</span><span class="sxs-lookup"><span data-stu-id="17d9c-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="17d9c-114">Soubor neexistuje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="17d9c-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="17d9c-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="17d9c-115">.NET Framework Security</span></span>  
 <span data-ttu-id="17d9c-116">Vždy zkontrolujte vstupy a nikdy deserializovat data z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="17d9c-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="17d9c-117">Objekt znovu vytvořit běží na místním počítači s oprávněními kód, který ji deserializovat.</span><span class="sxs-lookup"><span data-stu-id="17d9c-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="17d9c-118">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="17d9c-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d9c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="17d9c-119">See Also</span></span>

- <xref:System.IO.StreamWriter>  
- [<span data-ttu-id="17d9c-120">Postupy: zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="17d9c-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
- [<span data-ttu-id="17d9c-121">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="17d9c-121">Serialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
- [<span data-ttu-id="17d9c-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="17d9c-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
