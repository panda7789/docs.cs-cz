---
title: Serializace grafů objektů, které obsahují objekty XElement (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: db7354598fc84c6fa3f8ec4e5b53799030459387
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711524"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="9c878-102">Serializace grafů objektů, které obsahují objekty XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="9c878-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="9c878-103">Toto téma představuje možnost serializace grafů objektů, které obsahují odkazy na objekty typu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="9c878-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="9c878-104">Na zařízení tento typ serializace, <xref:System.Xml.Linq.XElement> implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9c878-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="9c878-105">Poznámka: pouze <xref:System.Xml.Linq.XElement> třída implementuje serializace.</span><span class="sxs-lookup"><span data-stu-id="9c878-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c878-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c878-106">In This Section</span></span>  
  
|<span data-ttu-id="9c878-107">Téma</span><span class="sxs-lookup"><span data-stu-id="9c878-107">Topic</span></span>|<span data-ttu-id="9c878-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9c878-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9c878-109">Postupy: Serializace pomocí třídy XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="9c878-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="9c878-110">Ukazuje, jak lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c878-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="9c878-111">Postupy: Serializace pomocí třídy DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="9c878-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="9c878-112">Ukazuje, jak lze serializovat pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c878-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c878-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c878-113">See also</span></span>

- [<span data-ttu-id="9c878-114">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="9c878-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
