---
title: "Funkční konstrukce (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="2ac50-102">Funkční konstrukce (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2ac50-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2ac50-103">nabízí efektivní způsob, jak vytvořit elementů XML s názvem *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="2ac50-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="2ac50-104">Funkční konstrukce je schopnost vytvářet strom XML v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="2ac50-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="2ac50-105">Existuje několik klíčových funkcích služby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programovací rozhraní, které povolit funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="2ac50-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="2ac50-106"><xref:System.Xml.Linq.XElement> Konstruktor přebírá různé typy argumentů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="2ac50-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="2ac50-107">Můžete například předat jiné <xref:System.Xml.Linq.XElement> objekt, který se stane podřízený element.</span><span class="sxs-lookup"><span data-stu-id="2ac50-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="2ac50-108">Můžete předat <xref:System.Xml.Linq.XAttribute> objektu, který bude atribut elementu.</span><span class="sxs-lookup"><span data-stu-id="2ac50-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="2ac50-109">Nebo můžete předat jiný typ objektu, který je převedeno na řetězec a že bude textového obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="2ac50-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="2ac50-110"><xref:System.Xml.Linq.XElement> Konstruktor přijímá `params` pole typu <xref:System.Object>, takže můžete předat libovolný počet objektů do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2ac50-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="2ac50-111">Umožňuje vytvořit element, který má složitý obsah.</span><span class="sxs-lookup"><span data-stu-id="2ac50-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="2ac50-112">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu, a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="2ac50-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="2ac50-113">Pokud kolekce obsahuje <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="2ac50-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="2ac50-114">To je důležité, protože vám umožňuje předat výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2ac50-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="2ac50-115">Tyto funkce umožňují napsat kód pro vytvoření strom XML.</span><span class="sxs-lookup"><span data-stu-id="2ac50-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="2ac50-116">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="2ac50-116">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="2ac50-117">Tyto funkce umožňují taky napsat kód, který používá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazuje při vytváření strom XML následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2ac50-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="2ac50-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2ac50-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ac50-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ac50-119">See Also</span></span>  
 [<span data-ttu-id="2ac50-120">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2ac50-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
