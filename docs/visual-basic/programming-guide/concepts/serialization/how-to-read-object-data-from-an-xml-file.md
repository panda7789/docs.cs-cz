---
title: 'Postupy: Čtení dat objektů ze souboru XML'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: c997af4729a24a6b5bd5b22d0153860cff3282d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346424"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="83e1c-102">Postupy: čtení dat objektů ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83e1c-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="83e1c-103">Tento příklad načte data objektů, která byla dříve zapsána do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="83e1c-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83e1c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83e1c-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83e1c-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="83e1c-105">Compiling the Code</span></span>  
 <span data-ttu-id="83e1c-106">Nahraďte název souboru "c:\temp\SerializationOverview.xml" názvem souboru, který obsahuje Serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="83e1c-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="83e1c-107">Další informace o serializaci dat naleznete v tématu [How to: Write Data Object to a XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="83e1c-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="83e1c-108">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="83e1c-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="83e1c-109">Pouze veřejné vlastnosti a pole jsou deserializovány.</span><span class="sxs-lookup"><span data-stu-id="83e1c-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="83e1c-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="83e1c-110">Robust Programming</span></span>  
 <span data-ttu-id="83e1c-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="83e1c-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="83e1c-112">Serializovaná třída nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="83e1c-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="83e1c-113">Data v souboru reprezentují data z třídy, která se má deserializovat.</span><span class="sxs-lookup"><span data-stu-id="83e1c-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="83e1c-114">Soubor neexistuje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="83e1c-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="83e1c-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83e1c-115">.NET Framework Security</span></span>  
 <span data-ttu-id="83e1c-116">Vždy ověřte vstupy a nikdy neserializovat data z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="83e1c-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="83e1c-117">Nově vytvořený objekt je spuštěn v místním počítači s oprávněním kódu, který jej deserializovat.</span><span class="sxs-lookup"><span data-stu-id="83e1c-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="83e1c-118">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="83e1c-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e1c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83e1c-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="83e1c-120">Postupy: zápis dat objektů do souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83e1c-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="83e1c-121">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83e1c-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="83e1c-122">Průvodce programováním Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83e1c-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
