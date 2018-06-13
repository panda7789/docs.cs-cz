---
title: Klonování vs. Připojení (C#)
ms.date: 07/20/2015
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
ms.openlocfilehash: 31b5498e18e63ffba357b34780c7eb388e08b37f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315760"
---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="62e1d-102">Klonování vs. Připojení (C#)</span><span class="sxs-lookup"><span data-stu-id="62e1d-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="62e1d-103">Při přidávání <xref:System.Xml.Linq.XNode> (včetně <xref:System.Xml.Linq.XElement>) nebo <xref:System.Xml.Linq.XAttribute> objekty na novou větev, pokud se nový obsah nemá nadřazený, jsou objekty jednoduše připojené k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="62e1d-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="62e1d-104">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, je klonovat nový obsah.</span><span class="sxs-lookup"><span data-stu-id="62e1d-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="62e1d-105">Nově naklonovaný obsah je poté připojený k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="62e1d-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62e1d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="62e1d-106">Example</span></span>  
 <span data-ttu-id="62e1d-107">Následující kód ukazuje chování, když přidáte nadřazeným prvkem elementu ke stromu, a při přidání element žádný nadřazený ke stromu.</span><span class="sxs-lookup"><span data-stu-id="62e1d-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="62e1d-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="62e1d-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="62e1d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="62e1d-109">See Also</span></span>  
 [<span data-ttu-id="62e1d-110">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="62e1d-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
