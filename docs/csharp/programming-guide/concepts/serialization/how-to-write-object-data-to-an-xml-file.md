---
title: Zápis dat objektů do souboru XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 6f18ae194d2ed70f633665a29772622319ea9493
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241991"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="77827-102">Zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="77827-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="77827-103">Tento příklad zapíše objekt z třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="77827-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77827-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="77827-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="77827-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="77827-105">Compiling the Code</span></span>  
 <span data-ttu-id="77827-106">Serializovaná třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="77827-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="77827-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="77827-107">Robust Programming</span></span>  
 <span data-ttu-id="77827-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="77827-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="77827-109">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="77827-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="77827-110">Soubor existuje a je určen jen pro čtení ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="77827-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="77827-111">Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="77827-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="77827-112">Disk je plný ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="77827-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="77827-113">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="77827-113">.NET Security</span></span>  
 <span data-ttu-id="77827-114">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="77827-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="77827-115">Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje `Create` ke složce přístup.</span><span class="sxs-lookup"><span data-stu-id="77827-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="77827-116">Pokud soubor již existuje, aplikace potřebuje `Write` přístup pouze k menšímu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="77827-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="77827-117">Je-li to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jedinému souboru, nikoli ke `Create` složce.</span><span class="sxs-lookup"><span data-stu-id="77827-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77827-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="77827-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="77827-119">Čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="77827-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="77827-120">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="77827-120">Serialization (C#)</span></span>](./index.md)
