---
title: 'Postupy: Zápis dat objektů do souboru XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 17f8463a4b905028d37a2e005562867f87f4bd2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624371"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="06fcd-102">Postupy: Zápis dat objektů do souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06fcd-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="06fcd-103">Tento příklad zapíše objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="06fcd-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06fcd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="06fcd-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="06fcd-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="06fcd-105">Compiling the Code</span></span>  
 <span data-ttu-id="06fcd-106">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="06fcd-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="06fcd-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="06fcd-107">Robust Programming</span></span>  
 <span data-ttu-id="06fcd-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="06fcd-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="06fcd-109">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="06fcd-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="06fcd-110">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="06fcd-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="06fcd-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="06fcd-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="06fcd-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="06fcd-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="06fcd-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06fcd-113">.NET Framework Security</span></span>  
 <span data-ttu-id="06fcd-114">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="06fcd-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="06fcd-115">Pokud aplikace potřebuje vytvořit soubor, pak tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="06fcd-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="06fcd-116">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="06fcd-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="06fcd-117">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` přístup do jednoho souboru, spíše než `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="06fcd-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fcd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06fcd-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="06fcd-119">Postupy: Čtení dat objektů ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06fcd-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="06fcd-120">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06fcd-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
