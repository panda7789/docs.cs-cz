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
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="c45a5-102">Klonování versus Připojování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c45a5-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="c45a5-103">Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo objektů <xref:System.Xml.Linq.XAttribute> do nového stromu, pokud nový obsah nemá žádný nadřazený objekt, objekty jsou jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c45a5-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="c45a5-104">Pokud nový obsah již je nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován.</span><span class="sxs-lookup"><span data-stu-id="c45a5-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="c45a5-105">Nově Klonovaný obsah je pak připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c45a5-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c45a5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c45a5-106">Example</span></span>  
 <span data-ttu-id="c45a5-107">Následující kód demonstruje chování při přidání nadřazeného elementu do stromu a při přidání elementu bez nadřazeného prvku do stromu.</span><span class="sxs-lookup"><span data-stu-id="c45a5-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="c45a5-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c45a5-108">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="c45a5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c45a5-109">See also</span></span>

- [<span data-ttu-id="c45a5-110">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c45a5-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
