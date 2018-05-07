---
title: Přístup k atributům v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b295c94fda22d4a17fb485add13ec67f1e9ae8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-attributes-in-the-dom"></a>Přístup k atributům v modelu DOM
Atributy jsou vlastnosti elementu, ne podřízených objektů daného elementu. Tento rozdíl je důležitý kvůli metody použité k přejděte na stejné úrovni, nadřazené a podřízené uzly z XML modelu DOM (Document Object). Například **PreviousSibling** a **NextSibling** metody nepoužívají se k přejděte z prvku, atributu nebo mezi atributy. Místo toho atribut je vlastnost elementu a vlastní element, má **OwnerElement** vlastnost a ne **parentNode** vlastnost, a má odlišné metody navigace.  
  
 Je-li aktuální uzel elementu, použijte **HasAttribute** metoda, pokud jsou k dispozici žádné atributy přidružené k tomuto prvku. Jakmile se ví, že element má atributy, existuje více metod pro přístup k atributům. Chcete-li získat jeden atribut z elementu, můžete použít **GetAttribute** a **GetAttributeNode** metody **XmlElement** nebo můžete získat všechny atributy do kolekce. Získání kolekce je užitečné, pokud potřebujete Iterujte přes kolekci. Pokud chcete, aby všechny atributy z elementu, použijte **atributy** vlastnost elementu pro načtení všech atributů do kolekce.  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>Načítání všechny atributy do kolekce  
 Pokud chcete, všechny atributy uzlu elementu uvést do kolekce, zavolejte **XmlElement.Attributes** vlastnost. To získá **XmlAttributeCollection** obsahující všechny atributy elementu. **XmlAttributeCollection** třída dědí z **XmlNamedNode** mapy. Proto metody a vlastnosti, které jsou k dispozici v kolekci zahrnují ty, které jsou k dispozici na mapě pojmenované uzlu kromě metody a vlastnosti specifické pro **XmlAttributeCollection** třídy, jako **ItemOf**  vlastnost nebo **připojení** metoda. Představuje každou položku v kolekci atributů **XmlAttribute** uzlu. Počet atributů v elementu najdete získat **XmlAttributeCollection**a použít **počet** vlastnosti kolik **XmlAttribute** jsou uzly v kolekci.  
  
 Následující příklad kódu ukazuje, jak načíst atribut kolekce a pomocí **počet** metoda pro opakování index iteraci nad ním. Kód pak ukazuje, jak načíst jeden atribut z kolekce a zobrazit jeho hodnotu.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  
    public static void Main()  
    {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 Tento příklad zobrazí následující výstup:  
  
 **Output**  
  
 Zobrazte všechny atributy v kolekci.  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 Informace v kolekci atributů může načíst název nebo číslo indexu. Výše uvedený příklad ukazuje, jak načíst data podle názvu. Další příklad ukazuje, jak načíst data tak, že číslo indexu.  
  
 Protože **XmlAttributeCollection** je kolekce a můžete vstupní nepřevezme index nebo název tento příklad ukazuje, výběrem první atribut z kolekce pomocí index počítaný od nuly nebo pomocí následující soubor, **baseuri.xml**, jako vstupní.  
  
### <a name="input"></a>Vstup  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a>Načítání uzlu jednotlivých atributu.  
 Načíst uzlu jeden atribut z elementu, <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> metoda se používá. Vrátí objekt typu **XmlAttribute**. Až budete mít **XmlAttribute**, všechny metody a vlastnosti, které jsou k dispozici v <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> třídy jsou k dispozici na tento objekt, jako je hledání **OwnerElement**.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
 public class Sample  
 {  
      public static void Main()  
      {  
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 Můžete také provést jak je znázorněno v předchozím příkladu, kde jeden atribut uzlu se načítají z kolekce atributů. Následující příklad kódu ukazuje způsob, jakým jeden řádek kódu je možné zapsat do načíst jeden atribut číslem indexu z kořene dokumentu XML stromu, označované také jako **prvek DocumentElement** vlastnost.  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
