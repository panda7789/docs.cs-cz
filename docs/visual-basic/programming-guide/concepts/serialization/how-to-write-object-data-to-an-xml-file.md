---
title: 'Postupy: zápis dat objektů do souboru XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 434706383c50e5df8e419e3988da8dc7cce87c83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652546"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="06bd9-102">Postupy: zápis dat objektů do souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06bd9-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="06bd9-103">Tento příklad zapíše objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="06bd9-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06bd9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="06bd9-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06bd9-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="06bd9-105">Compiling the Code</span></span>  
 <span data-ttu-id="06bd9-106">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="06bd9-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="06bd9-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="06bd9-107">Robust Programming</span></span>  
 <span data-ttu-id="06bd9-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="06bd9-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="06bd9-109">Třída serializována nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="06bd9-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="06bd9-110">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="06bd9-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="06bd9-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="06bd9-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="06bd9-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="06bd9-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="06bd9-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06bd9-113">.NET Framework Security</span></span>  
 <span data-ttu-id="06bd9-114">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="06bd9-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="06bd9-115">Pokud aplikace potřebuje k vytvoření souboru, tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="06bd9-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="06bd9-116">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup nižší úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="06bd9-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="06bd9-117">Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` přístup do jednoho souboru místo `Create` přístup pro složku.</span><span class="sxs-lookup"><span data-stu-id="06bd9-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06bd9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="06bd9-118">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="06bd9-119">Postupy: čtení dat objektů ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06bd9-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="06bd9-120">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06bd9-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
