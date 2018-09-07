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
ms.openlocfilehash: aeb0a8e80a023568f192e832b1e4a3244fc87455
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085118"
---
# <a name="accessing-attributes-in-the-dom"></a>Přístup k atributům v modelu DOM
Atributy jsou vlastnosti elementu, není podřízených objektů daného elementu. Tento rozdíl je důležitý kvůli metody použité k navigaci na stejné úrovni, nadřazené a podřízené uzly z XML Document Object Model (DOM). Například **PreviousSibling** a **NextSibling** metody nepoužívají přejít z elementu, atributu nebo mezi atributy. Místo toho atribut je vlastnost elementu a prvek vlastní, má **OwnerElement** vlastnost a nikoli **parentNode** vlastnost, a má různé metody navigace.  
  
 Je-li aktuální uzel elementu, použijte **HasAttribute** metoda zjistíte, jestli jsou všechny atributy přidružené k elementu. Jakmile je známo, že element má atributy, existuje několik metod pro přístup k atributům. K načtení jednoho atributu z elementu, můžete použít **GetAttribute** a **GetAttributeNode** metody **XmlElement** nebo ji získáte všechny atributy do kolekce. Získání kolekce je užitečné, pokud budete potřebovat k iteraci přes kolekci. Pokud chcete všechny atributy z elementu, použijte **atributy** vlastnost elementu, který chcete načíst všechny atributy do kolekce.  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>Načtení všech atributů do kolekce  
 Pokud chcete, všechny atributy uzlu elementu uvést do kolekce, zavolejte **XmlElement.Attributes** vlastnost. Načte **XmlAttributeCollection** , která obsahuje všechny atributy elementu. **XmlAttributeCollection** třída dědí z **XmlNamedNode** mapy. Proto, metody a vlastnosti, které jsou k dispozici na kolekci zahrnují dostupných na mapě pojmenovaný uzel navíc k metodám a vlastnostem, které jsou specifické pro **XmlAttributeCollection** třídy, jako **ItemOf**  vlastnost nebo **připojit** metody. Každá položka v kolekci atributu představuje **XmlAttribute** uzlu. Pokud chcete zjistit počet atributů na elementu, získat **XmlAttributeCollection**a použít **počet** ve vlastnosti kolik **XmlAttribute** uzly jsou v kolekci.  
  
 Následující příklad kódu ukazuje, jak načíst atribut shromažďování a použití **počet** metoda opakování indexu iterovat nad ním. Kód poté ukazuje, jak načíst jeden atribut z kolekce a zobrazit její hodnotu.  
  
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
  
 V tomto příkladu se zobrazí následující výstup:  
  
 **Output**  
  
 Zobrazte všechny atributy v kolekci.  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 Informace v kolekci atributů lze načíst podle názvu nebo číslo indexu. Výše uvedený příklad ukazuje, jak načíst data podle názvu. Následující příklad ukazuje, jak načíst data, že číslo indexu.  
  
 Vzhledem k tomu, **XmlAttributeCollection** je kolekce a můžete provést iteraci nepřevezme index nebo název, tento příklad ukazuje, vyberete první atribut z kolekce pomocí index založený na nule a pomocí následující soubor **baseuri.xml**, jako vstupní.  
  
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
  
## <a name="retrieving-an-individual-attribute-node"></a>Načítání do jednotlivých atribut uzlu  
 K načtení uzlu jeden atribut z elementu, <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> metoda se používá. Vrátí objekt typu **XmlAttribute**. Jakmile budete mít **XmlAttribute**, všechny metody a vlastnosti, které jsou k dispozici v <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> třídy jsou k dispozici k tomuto objektu, jako je například hledání **OwnerElement**.  
  
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
  
 Taky vám pomůžou jak je znázorněno v předchozím příkladu, kde jeden atribut uzlu je načten z kolekce atributu. Následující příklad kódu ukazuje jak jeden řádek kódu je možné zapisovat na načtení jednoho atributu číslem indexu z kořene dokumentu XML stromu, označovaný také jako **prvek DocumentElement** vlastnost.  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
