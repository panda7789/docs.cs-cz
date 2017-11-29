---
title: "Postupy: čtení dat objektů ze souboru XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="9ad0d-102">Postupy: čtení dat objektů ze souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ad0d-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="9ad0d-103">Tento příklad čte data objektu, která byla dříve zapsána do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ad0d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ad0d-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ad0d-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9ad0d-105">Compiling the Code</span></span>  
 <span data-ttu-id="9ad0d-106">Nahraďte názvem souboru "c:\temp\SerializationOverview.xml" název souboru, který obsahuje serializovaná data.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="9ad0d-107">Další informace o serializaci dat najdete v tématu [postupy: zápis dat objektů do souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="9ad0d-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="9ad0d-108">Třída musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="9ad0d-109">Pouze veřejné vlastnosti a pole jsou deserializovat.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9ad0d-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="9ad0d-110">Robust Programming</span></span>  
 <span data-ttu-id="9ad0d-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="9ad0d-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9ad0d-112">Třída serializována nemá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="9ad0d-113">Data v souboru nepředstavuje data ze třídy k deserializaci.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="9ad0d-114">Soubor neexistuje (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9ad0d-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9ad0d-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ad0d-115">.NET Framework Security</span></span>  
 <span data-ttu-id="9ad0d-116">Vždy zkontrolujte vstupy a nikdy deserializaci dat z nedůvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="9ad0d-117">Objekt znovu vytvořit běží na místním počítači s oprávněními kód, který ji deserializovat.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="9ad0d-118">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="9ad0d-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad0d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ad0d-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="9ad0d-120">Postupy: zápis dat objektů do souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ad0d-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="9ad0d-121">Serializace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ad0d-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="9ad0d-122">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ad0d-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
