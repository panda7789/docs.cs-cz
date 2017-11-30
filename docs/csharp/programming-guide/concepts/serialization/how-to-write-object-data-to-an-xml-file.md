---
title: "Postupy: zápis dat objektů do souboru XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f43075c0b4d04ff935e7a29ed270b348209d17b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="7ffb5-102">Postupy: zápis dat objektů do souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7ffb5-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="7ffb5-103">Tento příklad zapíše objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ffb5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ffb5-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ffb5-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7ffb5-105">Compiling the Code</span></span>  
 <span data-ttu-id="7ffb5-106">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7ffb5-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7ffb5-107">Robust Programming</span></span>  
 <span data-ttu-id="7ffb5-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="7ffb5-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="7ffb5-109">Třída serializována nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="7ffb5-110">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="7ffb5-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="7ffb5-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="7ffb5-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="7ffb5-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="7ffb5-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7ffb5-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ffb5-113">.NET Framework Security</span></span>  
 <span data-ttu-id="7ffb5-114">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="7ffb5-115">Pokud aplikace potřebuje k vytvoření souboru, tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="7ffb5-116">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup nižší úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="7ffb5-117">Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` přístup do jednoho souboru místo `Create` přístup pro složku.</span><span class="sxs-lookup"><span data-stu-id="7ffb5-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffb5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ffb5-118">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="7ffb5-119">Postupy: čtení dat objektů ze souboru XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7ffb5-119">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="7ffb5-120">Serializace (C#)</span><span class="sxs-lookup"><span data-stu-id="7ffb5-120">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
