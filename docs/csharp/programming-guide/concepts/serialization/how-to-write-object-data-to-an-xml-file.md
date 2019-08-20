---
title: 'Postupy: Zápis dat objektů do souboru XML (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 5da79d68bf7e1c955cb6edededb3914bd9c898e5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590684"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="536c0-102">Postupy: Zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="536c0-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="536c0-103">Tento příklad zapíše objekt z třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="536c0-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="536c0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="536c0-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="536c0-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="536c0-105">Compiling the Code</span></span>  
 <span data-ttu-id="536c0-106">Serializovaná třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="536c0-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="536c0-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="536c0-107">Robust Programming</span></span>  
 <span data-ttu-id="536c0-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="536c0-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="536c0-109">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="536c0-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="536c0-110">Soubor existuje a je určen jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="536c0-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="536c0-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="536c0-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="536c0-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="536c0-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="536c0-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="536c0-113">.NET Framework Security</span></span>  
 <span data-ttu-id="536c0-114">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="536c0-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="536c0-115">Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje `Create` ke složce přístup.</span><span class="sxs-lookup"><span data-stu-id="536c0-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="536c0-116">Pokud soubor již existuje, aplikace potřebuje přístup pouze `Write` k menšímu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="536c0-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="536c0-117">Je-li to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jedinému souboru, `Create` nikoli ke složce.</span><span class="sxs-lookup"><span data-stu-id="536c0-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536c0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="536c0-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="536c0-119">Postupy: Čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="536c0-119">How to: Read Object Data from an XML File (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="536c0-120">SerializaceC#()</span><span class="sxs-lookup"><span data-stu-id="536c0-120">Serialization (C#)</span></span>](./index.md)
