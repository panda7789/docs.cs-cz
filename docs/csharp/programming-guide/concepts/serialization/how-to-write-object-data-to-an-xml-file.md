---
title: Jak zapisovat data objektů do souboru XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: f7ffb47a22d3cd94cd7cb6f702b64180a8790eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167505"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="46c37-102">Jak zapisovat data objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="46c37-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="46c37-103">Tento příklad zapíše objekt z třídy <xref:System.Xml.Serialization.XmlSerializer> do souboru XML pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="46c37-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c37-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="46c37-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="46c37-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="46c37-105">Compiling the Code</span></span>  
 <span data-ttu-id="46c37-106">Serializovaná třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="46c37-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="46c37-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="46c37-107">Robust Programming</span></span>  
 <span data-ttu-id="46c37-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="46c37-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="46c37-109">Třída serializované nemá veřejné, parametrless konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="46c37-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="46c37-110">Soubor existuje a je jen<xref:System.IO.IOException>pro čtení ( ).</span><span class="sxs-lookup"><span data-stu-id="46c37-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="46c37-111">Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).</span><span class="sxs-lookup"><span data-stu-id="46c37-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="46c37-112">Disk je plný<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="46c37-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="46c37-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="46c37-113">.NET Framework Security</span></span>  
 <span data-ttu-id="46c37-114">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="46c37-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="46c37-115">Pokud aplikace potřebuje vytvořit soubor, tato `Create` aplikace potřebuje přístup pro složku.</span><span class="sxs-lookup"><span data-stu-id="46c37-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="46c37-116">Pokud soubor již existuje, aplikace `Write` potřebuje pouze přístup, menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="46c37-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="46c37-117">Pokud je to možné, je bezpečnější vytvořit soubor `Read` během nasazení a udělit `Create` přístup pouze k jednomu souboru, nikoli přístup u složky.</span><span class="sxs-lookup"><span data-stu-id="46c37-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c37-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="46c37-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="46c37-119">Čtení dat objektu ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="46c37-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="46c37-120">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="46c37-120">Serialization (C#)</span></span>](./index.md)
