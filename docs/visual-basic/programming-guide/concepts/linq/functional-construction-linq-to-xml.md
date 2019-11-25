---
title: funkční konstrukce (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 6366c7781372d34e15d62f81a5ceae8ff4ccda2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353467"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="999ac-102">Functional Construction (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="999ac-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="999ac-103">provides a powerful way to create XML elements called *functional construction*.</span><span class="sxs-lookup"><span data-stu-id="999ac-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="999ac-104">Functional construction is the ability to create an XML tree in a single statement.</span><span class="sxs-lookup"><span data-stu-id="999ac-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="999ac-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span><span class="sxs-lookup"><span data-stu-id="999ac-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="999ac-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span><span class="sxs-lookup"><span data-stu-id="999ac-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="999ac-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span><span class="sxs-lookup"><span data-stu-id="999ac-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="999ac-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span><span class="sxs-lookup"><span data-stu-id="999ac-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="999ac-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span><span class="sxs-lookup"><span data-stu-id="999ac-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="999ac-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span><span class="sxs-lookup"><span data-stu-id="999ac-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="999ac-111">This enables you to create an element that has complex content.</span><span class="sxs-lookup"><span data-stu-id="999ac-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="999ac-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span><span class="sxs-lookup"><span data-stu-id="999ac-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="999ac-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span><span class="sxs-lookup"><span data-stu-id="999ac-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="999ac-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span><span class="sxs-lookup"><span data-stu-id="999ac-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="999ac-115">The following is an example:</span><span class="sxs-lookup"><span data-stu-id="999ac-115">The following is an example:</span></span>  
  
 <span data-ttu-id="999ac-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span><span class="sxs-lookup"><span data-stu-id="999ac-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="999ac-117">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="999ac-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="999ac-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="999ac-118">See also</span></span>

- [<span data-ttu-id="999ac-119">Creating XML Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="999ac-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
