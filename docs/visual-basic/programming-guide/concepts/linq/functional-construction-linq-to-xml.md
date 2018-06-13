---
title: Funkční konstrukce (technologie LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 360c321f993c8adb17767987060a0edcccad082a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644287"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="85c44-102">Funkční konstrukce (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85c44-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="85c44-103"> nabízí efektivní způsob, jak vytvořit elementů XML s názvem *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="85c44-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="85c44-104">Funkční konstrukce je schopnost vytvářet strom XML v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="85c44-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="85c44-105">Existuje několik klíčových funkcích služby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní, které povolit funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="85c44-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="85c44-106"><xref:System.Xml.Linq.XElement> Konstruktor přebírá různé typy argumentů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="85c44-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="85c44-107">Můžete například předat jiné <xref:System.Xml.Linq.XElement> objekt, který se stane podřízený element.</span><span class="sxs-lookup"><span data-stu-id="85c44-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="85c44-108">Můžete předat <xref:System.Xml.Linq.XAttribute> objektu, který bude atribut elementu.</span><span class="sxs-lookup"><span data-stu-id="85c44-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="85c44-109">Nebo můžete předat jiný typ objektu, který je převedeno na řetězec a že bude textového obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="85c44-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="85c44-110"><xref:System.Xml.Linq.XElement> Konstruktor přijímá `params` pole typu <xref:System.Object>, takže můžete předat libovolný počet objektů do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="85c44-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="85c44-111">Umožňuje vytvořit element, který má složitý obsah.</span><span class="sxs-lookup"><span data-stu-id="85c44-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="85c44-112">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu, a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="85c44-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="85c44-113">Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="85c44-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="85c44-114">To je důležité, protože vám umožňuje předat výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="85c44-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="85c44-115">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="85c44-115">The following is an example:</span></span>  
  
 <span data-ttu-id="85c44-116">Tyto funkce umožňují napsat kód pomocí XML – literály vytvořit strom XML a také napsat kód, který používá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, když vytvoříte strom XML:</span><span class="sxs-lookup"><span data-stu-id="85c44-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="85c44-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="85c44-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85c44-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="85c44-118">See Also</span></span>  
 [<span data-ttu-id="85c44-119">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85c44-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
