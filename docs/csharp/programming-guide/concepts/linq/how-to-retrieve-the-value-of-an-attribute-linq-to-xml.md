---
title: 'Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d0babc51dc4992741991be876d0a5ecae8302bd3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667714"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="447d8-102">Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="447d8-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="447d8-103">Toto téma ukazuje, jak získat hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="447d8-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="447d8-104">Existují dva hlavní způsoby: Můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu převede obsah elementu nebo atributu do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="447d8-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="447d8-105">Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="447d8-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="447d8-106">Přetypování je však obvykle bude vhodnější.</span><span class="sxs-lookup"><span data-stu-id="447d8-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="447d8-107">Pokud vložíte atribut na typ připouštějící hodnotu Null, kód je jednodušší zápis při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="447d8-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="447d8-108">Příklady této techniky najdete v tématu [jak: Načtení hodnoty elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="447d8-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="447d8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="447d8-109">Example</span></span>  
 <span data-ttu-id="447d8-110">K načtení hodnoty atributu, jenom udělíte <xref:System.Xml.Linq.XAttribute> objekt požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="447d8-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="447d8-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="447d8-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="447d8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="447d8-112">Example</span></span>  
 <span data-ttu-id="447d8-113">Následující příklad ukazuje způsob k načtení hodnoty atributu, kde se příslušný atribut nachází v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="447d8-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="447d8-114">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="447d8-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="447d8-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="447d8-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="447d8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="447d8-116">See also</span></span>

- [<span data-ttu-id="447d8-117">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="447d8-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
