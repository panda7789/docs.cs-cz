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
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="11014-102">Postupy: serializaci objektu jako datový proud XML kódováním protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="11014-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="11014-103">Protože zprávu protokolu SOAP se sestavuje pomocí XML, <xref:System.Xml.Serialization.XmlSerializer> třídu lze použít k serializaci třídy a generovat kódovaného protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="11014-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="11014-104">Výsledný soubor XML vyhovuje [část 5 World Wide Web Consortium dokumentu "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="11014-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="11014-105">Při vytváření XML webové služby, které komunikují prostřednictvím zpráv protokolu SOAP, můžete upravit datový proud XML použitím sadu atributů protokolu SOAP speciální třídy a členy třídy.</span><span class="sxs-lookup"><span data-stu-id="11014-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="11014-106">Seznam atributů najdete v tématu [atributy, řízení kódovaný SOAP serializace](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="11014-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="11014-107">K serializaci objektu jako datový proud XML kódováním protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="11014-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1.  <span data-ttu-id="11014-108">Vytvoření třídy pomocí [nástroje definice schématu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="11014-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2.  <span data-ttu-id="11014-109">Použije jeden nebo více atributů speciální nalezen v `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="11014-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="11014-110">Naleznete v seznamu v "Atributy serializace SOAP kódovaného tohoto ovládacího prvku."</span><span class="sxs-lookup"><span data-stu-id="11014-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3.  <span data-ttu-id="11014-111">Vytvořit `XmlTypeMapping` vytvořením nového `SoapReflectionImporter`a volání `ImportTypeMapping` metoda s typem serializovaná třídy.</span><span class="sxs-lookup"><span data-stu-id="11014-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="11014-112">Následující kód například volání `ImportTypeMapping` metodu `SoapReflectionImporter` třídy za účelem vytvoření `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="11014-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4.  <span data-ttu-id="11014-113">Vytvořit instanci `XmlSerializer` třídy předáním `XmlTypeMapping` k <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="11014-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  <span data-ttu-id="11014-114">Volání `Serialize` nebo `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="11014-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11014-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="11014-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11014-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="11014-116">See Also</span></span>  
 [<span data-ttu-id="11014-117">XML a serializace protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="11014-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="11014-118">Atributy, které řídí serializace kódovaného protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="11014-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [<span data-ttu-id="11014-119">Serializace XML pomocí webové služby XML</span><span class="sxs-lookup"><span data-stu-id="11014-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [<span data-ttu-id="11014-120">Postupy: serializaci objektu</span><span class="sxs-lookup"><span data-stu-id="11014-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="11014-121">Postupy: deserializaci objektu</span><span class="sxs-lookup"><span data-stu-id="11014-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="11014-122">Postupy: potlačení serializace XML kódovaného protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="11014-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
