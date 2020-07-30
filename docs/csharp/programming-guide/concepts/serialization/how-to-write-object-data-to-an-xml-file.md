---
title: Zápis dat objektů do souboru XML (C#)
description: Tento příklad jazyka C# zapíše objekt z třídy do souboru XML pomocí třídy XmlSerializer. Přečtěte si, jak zkompilovat kód.
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: c88a85f8bc65a195f404dab6aa39675bac7e4f84
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303124"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="d3109-104">Zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d3109-104">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="d3109-105">Tento příklad zapíše objekt z třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="d3109-105">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3109-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3109-106">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3109-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d3109-107">Compiling the Code</span></span>  
 <span data-ttu-id="d3109-108">Serializovaná třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="d3109-108">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d3109-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d3109-109">Robust Programming</span></span>  
 <span data-ttu-id="d3109-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="d3109-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d3109-111">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="d3109-111">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="d3109-112">Soubor existuje a je určen jen pro čtení ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d3109-112">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d3109-113">Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="d3109-113">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d3109-114">Disk je plný ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d3109-114">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="d3109-115">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="d3109-115">.NET Security</span></span>  
 <span data-ttu-id="d3109-116">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d3109-116">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="d3109-117">Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje `Create` ke složce přístup.</span><span class="sxs-lookup"><span data-stu-id="d3109-117">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="d3109-118">Pokud soubor již existuje, aplikace potřebuje `Write` přístup pouze k menšímu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d3109-118">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="d3109-119">Je-li to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jedinému souboru, nikoli ke `Create` složce.</span><span class="sxs-lookup"><span data-stu-id="d3109-119">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3109-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3109-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="d3109-121">Čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d3109-121">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="d3109-122">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="d3109-122">Serialization (C#)</span></span>](./index.md)
