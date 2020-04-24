---
title: Načtení uzlů bez stanoveného pořadí podle názvu nebo indexu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 55ea0e31bb8a2863dc0e0eb30f6ca5700c3110b8
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155734"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Načtení uzlů bez stanoveného pořadí podle názvu nebo indexu
**XmlNamedNodeMap** je popsána ve specifikaci konsorcium World Wide Web (W3C) jako NamedNodeMap a je vyžadována pro zpracování neuspořádané sady uzlů s možností odkazovat uzly podle jejich názvu nebo indexu. Jediným způsobem, jakým máte přístup k **XmlNamedNodeMap** , je, že **XmlNamedNodeMap** je vrácen prostřednictvím metody nebo vlastnosti. Existují tři metody nebo vlastnosti, které vracejí **XmlNamedNodeMap**:  
  
- XmlElement. Attributes  
  
- XmlDocumentType. Entities  
  
- XmlDocumentType. Notation  
  
 Například vlastnost **XmlDocumentType. Entities** Získá kolekci uzlů **XmlEntity** deklarovaných v deklaraci typu dokumentu. Tato kolekce se vrátí jako **XmlNamedNodeMap**a můžete iterovat v rámci kolekce s použitím vlastnosti **Count** a informací o zobrazení entity. Příklad iterace prostřednictvím **XmlNamedNodeMap**naleznete v tématu <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **Atribut XmlAttributeCollection** je odvozen z **XmlNamedNodeMap** a pouze atributy lze upravovat, zatímco zápisy a entity jsou jen pro čtení. Pomocí **XmlNamedNodeMap** pro atributy můžete získat uzly pro tyto atributy na základě jejich názvů XML. To poskytuje snadnou metodu pro manipulaci s kolekcí atributů v uzlu element. To může být kontrast přímo s **XmlNodeList**, které také implementuje rozhraní **IEnumerable** , ale s objektem pro přístup k indexu místo řetězce. Metody **RemoveNamedItem** a **SetNamedItem** se používají pouze proti **atributu XmlAttributeCollection**. Přidání nebo odebrání kolekce atributů bez ohledu na to, zda použití **atributucollection** nebo implementace **XmlNamedNodeMap** , upraví kolekci atributů na elementu. Následující příklad kódu ukazuje, jak přesunout atribut a vytvořit nový atribut.  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
    }  
}  
```  
  
 Chcete-li zobrazit další příklad kódu, který ukazuje odebrání atributu zcollection **atributucollection**, viz [Metoda XmlNamedNodeMap. RemoveNamedItem](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A). Další informace o metodách a vlastnostech naleznete v tématu [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
