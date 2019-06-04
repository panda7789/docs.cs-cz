---
title: 'Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 94cab43571f7ade55155e7925975f253e452ceb7
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485003"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="5ae72-102">Postupy: Načtení hodnoty atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ae72-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5ae72-103">Toto téma ukazuje, jak získat hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="5ae72-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="5ae72-104">Existují dva hlavní způsoby: Můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu převede obsah elementu nebo atributu do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="5ae72-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="5ae72-105">Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5ae72-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="5ae72-106">Přetypování je však obvykle bude vhodnější.</span><span class="sxs-lookup"><span data-stu-id="5ae72-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="5ae72-107">Pokud vložíte atribut na typ připouštějící hodnotu Null, kód je jednodušší zápis při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="5ae72-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="5ae72-108">Příklady této techniky najdete v tématu [jak: Načtení hodnoty elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5ae72-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae72-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ae72-109">Example</span></span>  
 <span data-ttu-id="5ae72-110">K načtení hodnoty atributu, jenom udělíte <xref:System.Xml.Linq.XAttribute> objekt požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="5ae72-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="5ae72-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5ae72-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="5ae72-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ae72-112">Example</span></span>  
 <span data-ttu-id="5ae72-113">Následující příklad ukazuje způsob k načtení hodnoty atributu, kde se příslušný atribut nachází v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5ae72-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="5ae72-114">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5ae72-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="5ae72-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5ae72-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ae72-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ae72-116">See also</span></span>

- [<span data-ttu-id="5ae72-117">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5ae72-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
