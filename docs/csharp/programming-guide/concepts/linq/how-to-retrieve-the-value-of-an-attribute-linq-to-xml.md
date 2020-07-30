---
title: Jak načíst hodnotu atributu (LINQ to XML) (C#)
description: Přečtěte si, jak získat hodnotu atributu. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301551"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="f22f9-104">Jak načíst hodnotu atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f22f9-104">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f22f9-105">V tomto tématu se dozvíte, jak získat hodnotu atributů.</span><span class="sxs-lookup"><span data-stu-id="f22f9-105">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="f22f9-106">Existují dva hlavní způsoby: můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu pak převede obsah elementu nebo atributu na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="f22f9-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="f22f9-107">Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f22f9-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="f22f9-108">Přetypování je však všeobecně lepším přístupem.</span><span class="sxs-lookup"><span data-stu-id="f22f9-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="f22f9-109">Pokud přetypování atributu na typ hodnoty s možnou hodnotou null, kód je jednodušší zapisovat při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="f22f9-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="f22f9-110">Příklady této techniky naleznete v tématu [jak načíst hodnotu prvku (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f22f9-110">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f22f9-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f22f9-111">Example</span></span>  
 <span data-ttu-id="f22f9-112">Chcete-li načíst hodnotu atributu, stačí přetypování <xref:System.Xml.Linq.XAttribute> objektu na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="f22f9-112">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="f22f9-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f22f9-113">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="f22f9-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f22f9-114">Example</span></span>  
 <span data-ttu-id="f22f9-115">Následující příklad ukazuje, jak načíst hodnotu atributu, kde je atribut v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f22f9-115">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="f22f9-116">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f22f9-116">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="f22f9-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f22f9-117">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="f22f9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f22f9-118">See also</span></span>

- [<span data-ttu-id="f22f9-119">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="f22f9-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
