---
title: "Postupy: serializaci objektu jako datový proud XML kódováním protokolu SOAP"
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
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 34d0529c302f08287f2714e056eb6a536f3b28ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Postupy: serializaci objektu jako datový proud XML kódováním protokolu SOAP
  
 Protože zprávu protokolu SOAP se sestavuje pomocí XML, <xref:System.Xml.Serialization.XmlSerializer> třídu lze použít k serializaci třídy a generovat kódovaného protokolu SOAP zprávy. Výsledný soubor XML vyhovuje [část 5 World Wide Web Consortium dokumentu "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Při vytváření XML webové služby, které komunikují prostřednictvím zpráv protokolu SOAP, můžete upravit datový proud XML použitím sadu atributů protokolu SOAP speciální třídy a členy třídy. Seznam atributů najdete v tématu [atributy, řízení kódovaný SOAP serializace](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>K serializaci objektu jako datový proud XML kódováním protokolu SOAP  
  
1.  Vytvoření třídy pomocí [nástroje definice schématu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Použije jeden nebo více atributů speciální nalezen v `System.Xml.Serialization`. Naleznete v seznamu v "Atributy serializace SOAP kódovaného tohoto ovládacího prvku."  
  
3.  Vytvořit `XmlTypeMapping` vytvořením nového `SoapReflectionImporter`a volání `ImportTypeMapping` metoda s typem serializovaná třídy.  
  
     Následující kód například volání `ImportTypeMapping` metodu `SoapReflectionImporter` třídy za účelem vytvoření `XmlTypeMapping`.  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  Vytvořit instanci `XmlSerializer` třídy předáním `XmlTypeMapping` k <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktor.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  Volání `Serialize` nebo `Deserialize` metody.  
  
## <a name="example"></a>Příklad  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a>Viz také  
 [XML a serializace protokolu SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Atributy, které řídí serializace kódovaného protokolu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [Serializace XML pomocí webové služby XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [Postupy: serializaci objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Postupy: deserializaci objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [Postupy: potlačení serializace XML kódovaného protokolu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
