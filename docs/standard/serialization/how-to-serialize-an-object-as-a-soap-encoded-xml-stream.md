---
title: 'Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: bfbdda0861a6f2867a2e7003dd7054129fd343b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018014"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="83b44-102">Postupy: Serializace objektu jako XML streamu zakódovaného v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="83b44-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="83b44-103">Vzhledem k tomu, že zpráva SOAP je sestavena <xref:System.Xml.Serialization.XmlSerializer> pomocí jazyka XML, lze třídu použít k serializaci tříd a generování kódovaných zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="83b44-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="83b44-104">Výsledný kód XML odpovídá [části 5 dokumentu konsorcium World Wide Web "Simple Object Access Protocol (SOAP) 1,1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="83b44-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="83b44-105">Při vytváření XML webové služby, které komunikují prostřednictvím zpráv protokolu SOAP, můžete upravit datový proud XML použitím sadu atributů protokolu SOAP speciální třídy a členy třídy.</span><span class="sxs-lookup"><span data-stu-id="83b44-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="83b44-106">Seznam atributů naleznete v tématu [atributy, které řídí serializaci kódovaných SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="83b44-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="83b44-107">K serializaci objektu jako datový proud XML kódováním protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="83b44-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="83b44-108">Vytvořte třídu pomocí [nástroje definice schématu XML (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="83b44-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="83b44-109">Použije jeden nebo více atributů speciální nalezen v `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="83b44-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="83b44-110">Naleznete v seznamu v "Atributy serializace SOAP kódovaného tohoto ovládacího prvku."</span><span class="sxs-lookup"><span data-stu-id="83b44-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="83b44-111">Vytvořit `XmlTypeMapping` vytvořením nového `SoapReflectionImporter`a volání `ImportTypeMapping` metoda s typem serializovaná třídy.</span><span class="sxs-lookup"><span data-stu-id="83b44-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="83b44-112">Následující příklad kódu volá `ImportTypeMapping` metodu `SoapReflectionImporter` třídy pro vytvoření. `XmlTypeMapping`</span><span class="sxs-lookup"><span data-stu-id="83b44-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="83b44-113">Vytvořit instanci `XmlSerializer` třídy předáním `XmlTypeMapping` k <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="83b44-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="83b44-114">Volání `Serialize` nebo `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="83b44-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83b44-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="83b44-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83b44-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="83b44-116">See also</span></span>

- [<span data-ttu-id="83b44-117">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="83b44-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [<span data-ttu-id="83b44-118">Atributy, které řídí kódovanou serializaci SOAP</span><span class="sxs-lookup"><span data-stu-id="83b44-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="83b44-119">Serializace XML s webovými službami XML</span><span class="sxs-lookup"><span data-stu-id="83b44-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="83b44-120">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="83b44-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="83b44-121">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="83b44-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="83b44-122">Postupy: Přepsání serializace XML zakódované v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="83b44-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
