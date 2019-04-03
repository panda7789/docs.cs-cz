---
title: Klonování versus Připojení (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 59ffedfdbb2820683f1e6cc232154688f5c29fc8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832291"
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="8545a-102">Klonování versus Připojení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8545a-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="8545a-103">Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objektů do nového stromu, pokud nový obsah nemá žádný nadřazený objekt, jsou objekty jednoduše připojené do stromu XML.</span><span class="sxs-lookup"><span data-stu-id="8545a-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="8545a-104">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, je klonovat nový obsah.</span><span class="sxs-lookup"><span data-stu-id="8545a-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="8545a-105">Nově naklonované obsah je poté připojen k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="8545a-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8545a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8545a-106">Example</span></span>  
 <span data-ttu-id="8545a-107">Následující kód ukazuje chování při přidávání nadřazeným prvkem elementu do stromu a přidejte element s žádný nadřazený objekt na strom.</span><span class="sxs-lookup"><span data-stu-id="8545a-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="8545a-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8545a-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="8545a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8545a-109">See also</span></span>

- [<span data-ttu-id="8545a-110">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8545a-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
