---
title: Funkční konstrukce (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 6366c7781372d34e15d62f81a5ceae8ff4ccda2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353467"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="0dadc-102">Funkční konstrukce (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dadc-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="0dadc-103">poskytuje účinný způsob, jak vytvořit prvky XML nazvané *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="0dadc-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="0dadc-104">Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="0dadc-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="0dadc-105">Existuje několik klíčových funkcí rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, které umožňují konstrukci funkčnosti:</span><span class="sxs-lookup"><span data-stu-id="0dadc-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="0dadc-106">Konstruktor <xref:System.Xml.Linq.XElement> přebírá různé typy argumentů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="0dadc-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="0dadc-107">Například můžete předat další objekt <xref:System.Xml.Linq.XElement>, který se stal podřízeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="0dadc-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="0dadc-108">Můžete předat objekt <xref:System.Xml.Linq.XAttribute>, který se stal atributem elementu.</span><span class="sxs-lookup"><span data-stu-id="0dadc-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="0dadc-109">Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a který se změní na textový obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="0dadc-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="0dadc-110">Konstruktor <xref:System.Xml.Linq.XElement> přebírá `params` pole typu <xref:System.Object>, takže můžete konstruktoru předat libovolný počet objektů.</span><span class="sxs-lookup"><span data-stu-id="0dadc-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="0dadc-111">To umožňuje vytvořit prvek, který má složitý obsah.</span><span class="sxs-lookup"><span data-stu-id="0dadc-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="0dadc-112">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vyhodnocena kolekce v objektu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0dadc-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="0dadc-113">Pokud kolekce obsahuje objekty <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="0dadc-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="0dadc-114">To je důležité, protože umožňuje předat výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ho dotazu do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0dadc-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="0dadc-115">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="0dadc-115">The following is an example:</span></span>  
  
 <span data-ttu-id="0dadc-116">Tyto funkce umožňují psát kód pomocí literálů XML pro vytvoření stromu XML a také pro psaní kódu, který používá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů při vytváření stromu XML:</span><span class="sxs-lookup"><span data-stu-id="0dadc-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="0dadc-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0dadc-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dadc-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dadc-118">See also</span></span>

- [<span data-ttu-id="0dadc-119">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dadc-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
