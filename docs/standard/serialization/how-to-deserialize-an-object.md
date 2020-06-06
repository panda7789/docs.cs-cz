---
title: Jak deserializovat objekt pomocí XmlSerializer
description: Naučte se, jak objekt deserializovat. Formát přenosu Určuje, zda se má vytvořit datový proud nebo objekt souboru.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e08ae0d77539219223650fd3bcbd1bcee4df2739
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379117"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="78761-104">Jak deserializovat objekt pomocí XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="78761-104">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="78761-105">Při deserializaci objektu, formát přenosu Určuje, zda vytváříte objekt datového proudu nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="78761-105">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="78761-106">Po formát přenosu je určen, můžete volat <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> nebo <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metod, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="78761-106">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="78761-107">K deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="78761-107">To deserialize an object</span></span>

1. <span data-ttu-id="78761-108">Vytvořit <xref:System.Xml.Serialization.XmlSerializer> pomocí typ objektu určeného k deserializaci.</span><span class="sxs-lookup"><span data-stu-id="78761-108">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="78761-109">Volání <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metodu za účelem vytvoření repliky objektu.</span><span class="sxs-lookup"><span data-stu-id="78761-109">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="78761-110">Při deserializaci je nutné přetypování vráceného objektu na typ původní, jak je znázorněno v následujícím příkladu, který deserializace objekt ze souboru (i když může být také deserializovaný z datového proudu).</span><span class="sxs-lookup"><span data-stu-id="78761-110">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a><span data-ttu-id="78761-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="78761-111">See also</span></span>

- [<span data-ttu-id="78761-112">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="78761-112">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="78761-113">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="78761-113">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
