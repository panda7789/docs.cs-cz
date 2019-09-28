---
title: Klonování versus Připojování (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 2849c648d8d280200d742663cbc7188b344d8306
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352963"
---
# <a name="cloning-vs-attaching-visual-basic"></a>Klonování versus Připojování (Visual Basic)
Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo objektů <xref:System.Xml.Linq.XAttribute> do nového stromu, pokud nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojeny ke stromu XML. Pokud nový obsah již je nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován. Nově Klonovaný obsah je pak připojen ke stromu XML.  
  
## <a name="example"></a>Příklad  
 Následující kód demonstruje chování při přidání nadřazeného elementu do stromu a při přidání elementu bez nadřazeného prvku do stromu.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Viz také:

- [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
