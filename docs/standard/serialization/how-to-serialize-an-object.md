---
title: 'Postupy: Serializace objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928998"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="625da-102">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="625da-102">How to: Serialize an Object</span></span>
<span data-ttu-id="625da-103">K serializaci objektu, nejprve vytvořte objekt, který má být serializován a nastavíte jeho veřejné vlastnosti a pole.</span><span class="sxs-lookup"><span data-stu-id="625da-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="625da-104">Chcete-li to provést, je třeba určit přenos formát, ve kterém má být uložena jako datový proud nebo jako soubor XML datového proudu.</span><span class="sxs-lookup"><span data-stu-id="625da-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="625da-105">Například pokud datový proud XML musí být uložen ve formě trvalé, vytvořit <xref:System.IO.FileStream> objektu.</span><span class="sxs-lookup"><span data-stu-id="625da-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="625da-106">Další příklady serializace XML naleznete v tématu [Příklady serializace XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="625da-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="625da-107">K serializaci objektu</span><span class="sxs-lookup"><span data-stu-id="625da-107">To serialize an object</span></span>  
  
1. <span data-ttu-id="625da-108">Vytvoření objektu a nastavíte jeho veřejné polí a vlastností.</span><span class="sxs-lookup"><span data-stu-id="625da-108">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="625da-109">Vytvořit <xref:System.Xml.Serialization.XmlSerializer> pomocí daného typu objektu.</span><span class="sxs-lookup"><span data-stu-id="625da-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="625da-110">Další informace naleznete <xref:System.Xml.Serialization.XmlSerializer> třídy konstruktory.</span><span class="sxs-lookup"><span data-stu-id="625da-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="625da-111">Volání <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> metoda ke generování datový proud XML nebo soubor, který představuje polí a veřejné vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="625da-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="625da-112">Následující příklad vytvoří soubor.</span><span class="sxs-lookup"><span data-stu-id="625da-112">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="625da-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="625da-113">See also</span></span>

- [<span data-ttu-id="625da-114">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="625da-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="625da-115">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="625da-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
