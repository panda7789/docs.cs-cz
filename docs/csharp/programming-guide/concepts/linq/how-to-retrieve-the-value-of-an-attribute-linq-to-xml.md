---
title: Jak načíst hodnotu atributu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347437"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="76ccf-102">Jak načíst hodnotu atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="76ccf-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="76ccf-103">V tomto tématu se dozvíte, jak získat hodnotu atributů.</span><span class="sxs-lookup"><span data-stu-id="76ccf-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="76ccf-104">Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> můžete přetypovat na požadovaný typ; operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="76ccf-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="76ccf-105">Alternativně můžete použít vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="76ccf-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="76ccf-106">Přetypování je však všeobecně lepším přístupem.</span><span class="sxs-lookup"><span data-stu-id="76ccf-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="76ccf-107">Pokud přetypování atributu na typ s možnou hodnotou null, kód je jednodušší zapsat při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="76ccf-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="76ccf-108">Příklady této techniky naleznete v tématu [jak načíst hodnotu prvku (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="76ccf-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ccf-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="76ccf-109">Example</span></span>  
 <span data-ttu-id="76ccf-110">Chcete-li načíst hodnotu atributu, stačí přetypování objektu <xref:System.Xml.Linq.XAttribute> na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="76ccf-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="76ccf-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="76ccf-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="76ccf-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="76ccf-112">Example</span></span>  
 <span data-ttu-id="76ccf-113">Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="76ccf-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="76ccf-114">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="76ccf-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="76ccf-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="76ccf-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="76ccf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76ccf-116">See also</span></span>

- [<span data-ttu-id="76ccf-117">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="76ccf-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
