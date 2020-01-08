---
title: 'Postupy: Zápis dat objektů do souboru XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 989920709428f0e9cb4ddb8aeacfc71a2df220d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345981"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="3a8ec-102">Postupy: zápis dat objektů do souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a8ec-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="3a8ec-103">Tento příklad zapíše objekt z třídy do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a8ec-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a8ec-104">Example</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="3a8ec-105">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3a8ec-105">Compile the code</span></span>  
 <span data-ttu-id="3a8ec-106">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3a8ec-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3a8ec-107">Robust Programming</span></span>  
 <span data-ttu-id="3a8ec-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="3a8ec-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="3a8ec-109">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="3a8ec-110">Soubor existuje a je určen jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3a8ec-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="3a8ec-111">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="3a8ec-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="3a8ec-112">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3a8ec-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3a8ec-113">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3a8ec-113">.NET Framework Security</span></span>  
 <span data-ttu-id="3a8ec-114">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="3a8ec-115">Pokud aplikace potřebuje vytvořit soubor, musí tato aplikace `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="3a8ec-116">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, což je méně oprávnění.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="3a8ec-117">Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jednomu souboru místo `Create` přístupu pro složku.</span><span class="sxs-lookup"><span data-stu-id="3a8ec-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8ec-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a8ec-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="3a8ec-119">Postupy: čtení dat objektů ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a8ec-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="3a8ec-120">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a8ec-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
