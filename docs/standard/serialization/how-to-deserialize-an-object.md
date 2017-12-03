---
title: 'Postupy: deserializaci objektu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 651fb2ca3a3ea81a8a4e894c5f6a71bcf9ac3a50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-deserialize-an-object"></a><span data-ttu-id="8e9cb-102">Postupy: deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="8e9cb-102">How to: Deserialize an Object</span></span>
<span data-ttu-id="8e9cb-103">Při deserializaci objektu, formát přenosu Určuje, zda vytváříte objekt datového proudu nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="8e9cb-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="8e9cb-104">Po formát přenosu je určen, můžete volat <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> nebo <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metod, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="8e9cb-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="8e9cb-105">K deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="8e9cb-105">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="8e9cb-106">Vytvořit <xref:System.Xml.Serialization.XmlSerializer> pomocí typ objektu určeného k deserializaci.</span><span class="sxs-lookup"><span data-stu-id="8e9cb-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>  
  
2.  <span data-ttu-id="8e9cb-107">Volání <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metodu za účelem vytvoření repliky objektu.</span><span class="sxs-lookup"><span data-stu-id="8e9cb-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="8e9cb-108">Při deserializaci, musíte přetypovat vráceného objektu na typ původní, jak je znázorněno v následujícím příkladu, který deserializuje objekt do souboru (Ačkoli může být také deserializovat do datového proudu).</span><span class="sxs-lookup"><span data-stu-id="8e9cb-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object into a file (although it could also be deserialized into a stream).</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8e9cb-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e9cb-109">See Also</span></span>  
 [<span data-ttu-id="8e9cb-110">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="8e9cb-110">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="8e9cb-111">Postupy: serializaci objektu</span><span class="sxs-lookup"><span data-stu-id="8e9cb-111">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
