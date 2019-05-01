---
title: Funkční konstrukce (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f677c0d0e204b5d12718701ab70b8a3c1bd3530c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977467"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="edf43-102">Funkční konstrukce (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edf43-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="edf43-103">poskytuje efektivní způsob, jak vytvořit XML elementů s názvem *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="edf43-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="edf43-104">Funkční konstrukce je schopnost vytvářet stromu XML v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="edf43-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="edf43-105">Existuje několik klíčových funkcích služby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní, která umožňují funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="edf43-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="edf43-106"><xref:System.Xml.Linq.XElement> Konstruktoru přijímá různé typy argumentů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="edf43-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="edf43-107">Například lze předat jiné <xref:System.Xml.Linq.XElement> objekt, který bude podřízený element.</span><span class="sxs-lookup"><span data-stu-id="edf43-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="edf43-108">Můžete předat <xref:System.Xml.Linq.XAttribute> objekt, který bude atribut prvku.</span><span class="sxs-lookup"><span data-stu-id="edf43-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="edf43-109">Nebo můžete předat jakéhokoli jiného typu objektu, který je převeden na řetězec a stane se textového obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="edf43-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="edf43-110"><xref:System.Xml.Linq.XElement> Přebírá konstruktor `params` pole typu <xref:System.Object>tak, aby libovolný počet objektů, které můžete předat konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="edf43-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="edf43-111">To umožňuje vytvořit element, který se složitým obsahem.</span><span class="sxs-lookup"><span data-stu-id="edf43-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="edf43-112">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="edf43-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="edf43-113">Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="edf43-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="edf43-114">To je důležité, protože to umožňuje předat výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="edf43-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="edf43-115">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="edf43-115">The following is an example:</span></span>  
  
 <span data-ttu-id="edf43-116">Tyto funkce umožňují také napsat kód pomocí literálů XML k vytvoření stromu XML a také napsat kód, který používá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazuje při vytváření stromu XML:</span><span class="sxs-lookup"><span data-stu-id="edf43-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="edf43-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="edf43-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edf43-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edf43-118">See also</span></span>

- [<span data-ttu-id="edf43-119">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edf43-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
