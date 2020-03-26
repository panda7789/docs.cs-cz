---
title: Jak načíst hodnotu atributu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249191"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="0e126-102">Jak načíst hodnotu atributu (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0e126-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0e126-103">Toto téma ukazuje, jak získat hodnotu atributů.</span><span class="sxs-lookup"><span data-stu-id="0e126-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="0e126-104">Existují dva hlavní způsoby: <xref:System.Xml.Linq.XAttribute> Můžete přetypovat na požadovaný typ; explicitní operátor převodu pak převede obsah prvku nebo atributu na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="0e126-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="0e126-105">Případně můžete využít <xref:System.Xml.Linq.XAttribute.Value%2A> ubytování.</span><span class="sxs-lookup"><span data-stu-id="0e126-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="0e126-106">Nicméně, casting je obecně lepší přístup.</span><span class="sxs-lookup"><span data-stu-id="0e126-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="0e126-107">Pokud přetypování atributu s hodnotou s možnou hodnotou null, kód je jednodušší psát při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="0e126-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="0e126-108">Příklady této techniky naleznete v [tématu Jak načíst hodnotu prvku (LINQ do XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e126-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e126-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e126-109">Example</span></span>  
 <span data-ttu-id="0e126-110">Chcete-li načíst hodnotu atributu, stačí přetypovat <xref:System.Xml.Linq.XAttribute> objekt na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="0e126-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0e126-111">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0e126-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0e126-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e126-112">Example</span></span>  
 <span data-ttu-id="0e126-113">Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e126-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="0e126-114">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e126-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0e126-115">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0e126-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e126-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e126-116">See also</span></span>

- [<span data-ttu-id="0e126-117">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0e126-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
