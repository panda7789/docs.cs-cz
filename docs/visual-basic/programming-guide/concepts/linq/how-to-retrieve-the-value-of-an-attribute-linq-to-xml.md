---
title: 'Postupy: Načtení hodnoty atributu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 7cdd3e1f3e4c15d99511e944fd9bc2faac17dc5c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824353"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="50835-102">Postupy: Načtení hodnoty atributu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50835-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="50835-103">Toto téma ukazuje, jak získat hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="50835-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="50835-104">Existují dva hlavní způsoby: Můžete přetypovat <xref:System.Xml.Linq.XAttribute> na požadovaný typ; operátor explicitního převodu převede obsah elementu nebo atributu do zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="50835-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="50835-105">Alternativně můžete použít <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="50835-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="50835-106">Přetypování je však obvykle bude vhodnější.</span><span class="sxs-lookup"><span data-stu-id="50835-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="50835-107">Pokud vložíte atribut na typ připouštějící hodnotu Null, kód je jednodušší zápis při načítání hodnoty atributu, který může nebo nemusí existovat.</span><span class="sxs-lookup"><span data-stu-id="50835-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="50835-108">Příklady této techniky najdete v tématu [jak: Načtení hodnoty elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="50835-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50835-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="50835-109">Example</span></span>  
 <span data-ttu-id="50835-110">Vlastnost integrované atribut v jazyce Visual Basic slouží k načtení hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="50835-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="50835-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="50835-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="50835-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="50835-112">Example</span></span>  
 <span data-ttu-id="50835-113">V jazyce Visual Basic můžete použít vlastnost integrované atribut a nastavit hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="50835-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="50835-114">Navíc pokud použijete vlastnost integrované atribut a nastavit hodnotu atributu, který ještě neexistuje, bude vytvořen atribut.</span><span class="sxs-lookup"><span data-stu-id="50835-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="50835-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="50835-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="50835-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="50835-116">Example</span></span>  
 <span data-ttu-id="50835-117">Následující příklad ukazuje způsob k načtení hodnoty atributu, kde se příslušný atribut nachází v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="50835-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="50835-118">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="50835-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="50835-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="50835-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="50835-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50835-120">See also</span></span>

- [<span data-ttu-id="50835-121">Osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50835-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
