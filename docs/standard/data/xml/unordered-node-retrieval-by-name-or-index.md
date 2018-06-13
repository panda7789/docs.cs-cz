---
title: Neseřazený uzlu načítání podle názvu nebo Index
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 785a609455a35dd87a9593f00b58fd160ac708e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572938"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Neseřazený uzlu načítání podle názvu nebo Index
**XmlNamedNodeMap** je popsána ve specifikaci World Wide Web Consortium (W3C) jako NamedNodeMap a je potřeba pro zpracování neuspořádaný sada uzlů možnost odkaz uzly index nebo název. Jediným způsobem, jak máte přístup **XmlNamedNodeMap** je při **XmlNamedNodeMap** je vrácen prostřednictvím metody nebo vlastnosti. Existují tři metody nebo vlastnosti, které vracejí **XmlNamedNodeMap**:  
  
-   XmlElement.Attributes  
  
-   XmlDocumentType.Entities  
  
-   XmlDocumentType.Notations  
  
 Například **XmlDocumentType.Entities** vlastnost získá kolekci **XmlEntity** uzly deklarované v deklarace typu dokumentu. Tato kolekce se vrátí jako **XmlNamedNodeMap**, a můžete iteraci prostřednictvím kolekce s použitím **počet** vlastnost a zobrazení informací o entitě. Příklad iterace v rámci **XmlNamedNodeMap**, najdete v části <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **XmlAttributeCollection** je odvozený od **XmlNamedNodeMap** a pouze atributy lze měnit, zatímco zápisy a entity jsou jen pro čtení. Pomocí **XmlNamedNodeMap** pro atributy, můžete získat uzly pro tyto atributy založené na jejich názvy XML. Tímto způsobem snadno pro manipulaci s kolekci atributů na uzlu elementu. To může být rozdíl od aktualizovaného přímo **XmlNodeList**, který je navíc implementovaná **rozhraní IEnumerable** rozhraní, ale index přistupující objekt než řetězec. **RemoveNamedItem** a **SetNamedItem** metody se používají pouze proti **XmlAttributeCollection**. Přidání nebo odebrání z kolekce atributů, jestli se používá **AttributeCollection** nebo **XmlNamedNodeMap** implementace, upraví kolekce atributů v elementu. Následující příklad kódu ukazuje, jak přesunout atribut a vytvořit nový atribut.  
  
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
  
 Chcete-li zobrazit příklad další kód, který ukazuje atribut odebírán z **AttributeCollection**, najdete v části [XmlNamedNodeMap.RemoveNamedItem metoda](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem). Další informace o vlastnostech a metody najdete v tématu [XmlNamedNodeMap členy](AllMembers.T:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
