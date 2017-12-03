---
title: 'Postupy: serializaci objektu'
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
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92f7d19d84f8146a5c7933119874f4223dc20b6b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-serialize-an-object"></a>Postupy: serializaci objektu
K serializaci objektu, nejprve vytvořte objekt, který má být serializován a nastavíte jeho veřejné vlastnosti a pole. Chcete-li to provést, je třeba určit přenos formát, ve kterém má být uložena jako datový proud nebo jako soubor XML datového proudu. Například pokud datový proud XML musí být uložen ve formě trvalé, vytvořit <xref:System.IO.FileStream> objektu.  
  
> [!NOTE]
>  Další příklady serializace XML, najdete v části [serializace XML Příklady](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>K serializaci objektu  
  
1.  Vytvoření objektu a nastavíte jeho veřejné polí a vlastností.  
  
2.  Vytvořit <xref:System.Xml.Serialization.XmlSerializer> pomocí daného typu objektu. Další informace naleznete <xref:System.Xml.Serialization.XmlSerializer> třídy konstruktory.  
  
3.  Volání <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> metoda ke generování datový proud XML nebo soubor, který představuje polí a veřejné vlastnosti objektu. Následující příklad vytvoří soubor.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Představení serializace XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Postupy: deserializaci objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
