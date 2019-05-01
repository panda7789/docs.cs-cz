---
title: 'Postupy: Zadání alternativního názvu elementu pro XML stream'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: 577b96517632ca1ae06891540f22c2c3c3886cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018005"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="5ec52-102">Postupy: Zadání alternativního názvu elementu pro XML stream</span><span class="sxs-lookup"><span data-stu-id="5ec52-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
  
<span data-ttu-id="5ec52-103">Pomocí <xref:System.Xml.Serialization.XmlSerializer>, můžete vygenerovat více než jeden datový proud XML se stejnou sadou tříd.</span><span class="sxs-lookup"><span data-stu-id="5ec52-103">Using the <xref:System.Xml.Serialization.XmlSerializer>, you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="5ec52-104">Můžete to provést, protože dvě různé webové služby XML vyžadují stejné základní informace s pouze mírné rozdíly.</span><span class="sxs-lookup"><span data-stu-id="5ec52-104">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="5ec52-105">Představte si například dvě XML webové služby, které zpracovávají objednávky pro knihy a obě vyžadují tedy čísla ISBN.</span><span class="sxs-lookup"><span data-stu-id="5ec52-105">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="5ec52-106">Jedna služba používá značky \<ISBN > zatímco druhý používá značky \<BookID >.</span><span class="sxs-lookup"><span data-stu-id="5ec52-106">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="5ec52-107">Máte třídu s názvem `Book` obsahující pole s názvem `ISBN`.</span><span class="sxs-lookup"><span data-stu-id="5ec52-107">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="5ec52-108">Pokud instance `Book` serializován třídy, standardně použije název člena (ISBN) jako název elementu značky.</span><span class="sxs-lookup"><span data-stu-id="5ec52-108">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="5ec52-109">U první webové služby XML je podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="5ec52-109">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="5ec52-110">Pokud chcete odeslat datový proud XML druhý webové služby XML, je nutné přepsat serializace tak, aby byl název elementu na značku, ale `BookID`.</span><span class="sxs-lookup"><span data-stu-id="5ec52-110">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
## <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="5ec52-111">Chcete-li vytvořit datový proud XML s názvem alternativní elementu</span><span class="sxs-lookup"><span data-stu-id="5ec52-111">To create an XML stream with an alternate element name</span></span>  
  
1. <span data-ttu-id="5ec52-112">Vytvořit instanci <xref:System.Xml.Serialization.XmlElementAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ec52-112">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2. <span data-ttu-id="5ec52-113">Nastavte <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> z <xref:System.Xml.Serialization.XmlElementAttribute> na "BookID".</span><span class="sxs-lookup"><span data-stu-id="5ec52-113">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3. <span data-ttu-id="5ec52-114">Vytvořit instanci <xref:System.Xml.Serialization.XmlAttributes> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ec52-114">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4. <span data-ttu-id="5ec52-115">Přidat `XmlElementAttribute` do kolekce přistupovat prostřednictvím <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> vlastnost <xref:System.Xml.Serialization.XmlAttributes> .</span><span class="sxs-lookup"><span data-stu-id="5ec52-115">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5. <span data-ttu-id="5ec52-116">Vytvořit instanci <xref:System.Xml.Serialization.XmlAttributeOverrides> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ec52-116">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6. <span data-ttu-id="5ec52-117">Přidat `XmlAttributes` k <xref:System.Xml.Serialization.XmlAttributeOverrides>, předávání typ objektu určeného k přepsání a název člena přepsání.</span><span class="sxs-lookup"><span data-stu-id="5ec52-117">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7. <span data-ttu-id="5ec52-118">Vytvořit instanci `XmlSerializer` třídy s `XmlAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="5ec52-118">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8. <span data-ttu-id="5ec52-119">Vytvořit instanci `Book` třídy a serializaci nebo deserializaci ji.</span><span class="sxs-lookup"><span data-stu-id="5ec52-119">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ec52-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ec52-120">Example</span></span>  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="5ec52-121">Datový proud XML může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="5ec52-121">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ec52-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ec52-122">See also</span></span>

- <xref:System.Xml.Serialization.XmlElementAttribute>
- <xref:System.Xml.Serialization.XmlAttributes>
- <xref:System.Xml.Serialization.XmlAttributeOverrides>
- [<span data-ttu-id="5ec52-123">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="5ec52-123">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="5ec52-124">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="5ec52-124">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="5ec52-125">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="5ec52-125">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
