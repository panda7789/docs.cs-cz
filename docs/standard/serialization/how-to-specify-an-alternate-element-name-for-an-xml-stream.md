---
title: 'Postupy: Zadání alternativního názvu elementu pro XML stream'
description: Naučte se vytvořit datový proud XML s alternativním názvem elementu, například pro webové služby XML, které vyžadují stejné informace s mírnými rozdíly.
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
ms.openlocfilehash: d7e482ee6e1e1a7318ab05766508537d4b87789e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289587"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a>Postupy: Zadání alternativního názvu elementu pro XML stream
  
Pomocí <xref:System.Xml.Serialization.XmlSerializer>, můžete vygenerovat více než jeden datový proud XML se stejnou sadou tříd. Můžete to provést, protože dvě různé webové služby XML vyžadují stejné základní informace s pouze mírné rozdíly. Představte si například dvě XML webové služby, které zpracovávají objednávky pro knihy a obě vyžadují tedy čísla ISBN. Jedna služba používá značku, \<ISBN> zatímco druhá používá značku \<BookID> . Máte třídu s názvem `Book` obsahující pole s názvem `ISBN`. Pokud instance `Book` serializován třídy, standardně použije název člena (ISBN) jako název elementu značky. U první webové služby XML je podle očekávání. Pokud chcete odeslat datový proud XML druhý webové služby XML, je nutné přepsat serializace tak, aby byl název elementu na značku, ale `BookID`.  
  
## <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a>Chcete-li vytvořit datový proud XML s názvem alternativní elementu  
  
1. Vytvořit instanci <xref:System.Xml.Serialization.XmlElementAttribute> třídy.  
  
2. Nastavte <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> z <xref:System.Xml.Serialization.XmlElementAttribute> na "BookID".  
  
3. Vytvořit instanci <xref:System.Xml.Serialization.XmlAttributes> třídy.  
  
4. Přidat `XmlElementAttribute` do kolekce přistupovat prostřednictvím <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> vlastnost <xref:System.Xml.Serialization.XmlAttributes> .  
  
5. Vytvořit instanci <xref:System.Xml.Serialization.XmlAttributeOverrides> třídy.  
  
6. Přidat `XmlAttributes` k <xref:System.Xml.Serialization.XmlAttributeOverrides>, předávání typ objektu určeného k přepsání a název člena přepsání.  
  
7. Vytvořit instanci `XmlSerializer` třídy s `XmlAttributeOverrides`.  
  
8. Vytvořit instanci `Book` třídy a serializaci nebo deserializaci ji.  
  
## <a name="example"></a>Příklad  
  
```vb  
Public Function SerializeOverride()  
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
public void SerializeOverride()  
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
  
 Datový proud XML může vypadat takto.  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Serialization.XmlElementAttribute>
- <xref:System.Xml.Serialization.XmlAttributes>
- <xref:System.Xml.Serialization.XmlAttributeOverrides>
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Postupy: Serializace objektu](how-to-serialize-an-object.md)
- [Postupy: Deserializace objektu](how-to-deserialize-an-object.md)
