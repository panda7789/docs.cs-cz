---
title: 'Postupy: zápis dat objektů do souboru XML (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: b8fb60640c9bdc0337d45b6901b1be3979dbac1f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44047734"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="4010b-102">Postupy: zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4010b-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="4010b-103">Tento příklad zapíše objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="4010b-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4010b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4010b-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4010b-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4010b-105">Compiling the Code</span></span>  
 <span data-ttu-id="4010b-106">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="4010b-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4010b-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4010b-107">Robust Programming</span></span>  
 <span data-ttu-id="4010b-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="4010b-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="4010b-109">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="4010b-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="4010b-110">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="4010b-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4010b-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4010b-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="4010b-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="4010b-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4010b-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4010b-113">.NET Framework Security</span></span>  
 <span data-ttu-id="4010b-114">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4010b-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="4010b-115">Pokud aplikace potřebuje vytvořit soubor, pak tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="4010b-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="4010b-116">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4010b-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="4010b-117">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` přístup do jednoho souboru, spíše než `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="4010b-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4010b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4010b-118">See Also</span></span>

- <xref:System.IO.StreamWriter>  
- [<span data-ttu-id="4010b-119">Postupy: čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4010b-119">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
- [<span data-ttu-id="4010b-120">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="4010b-120">Serialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
