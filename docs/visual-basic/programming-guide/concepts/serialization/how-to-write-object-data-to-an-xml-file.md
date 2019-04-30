---
title: 'Postupy: Zápis dat objektů do souboru XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 52b896b0191f29f68cc31e02fc325638ca6341b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783497"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="9a805-102">Postupy: Zápis dat objektů do souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a805-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="9a805-103">Tento příklad zapíše objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="9a805-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a805-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a805-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a805-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9a805-105">Compiling the Code</span></span>  
 <span data-ttu-id="9a805-106">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="9a805-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9a805-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="9a805-107">Robust Programming</span></span>  
 <span data-ttu-id="9a805-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="9a805-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9a805-109">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="9a805-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="9a805-110">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9a805-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="9a805-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9a805-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="9a805-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9a805-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9a805-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a805-113">.NET Framework Security</span></span>  
 <span data-ttu-id="9a805-114">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9a805-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="9a805-115">Pokud aplikace potřebuje vytvořit soubor, pak tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="9a805-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="9a805-116">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9a805-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="9a805-117">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` přístup do jednoho souboru, spíše než `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="9a805-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a805-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a805-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="9a805-119">Postupy: Čtení dat objektů ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a805-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="9a805-120">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a805-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
