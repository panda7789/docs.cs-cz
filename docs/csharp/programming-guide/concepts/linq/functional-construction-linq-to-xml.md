---
title: Funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635753"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="d589f-102">Funkční konstrukce (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d589f-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d589f-103">poskytuje účinný způsob, jak vytvořit prvky XML nazvané *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="d589f-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="d589f-104">Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="d589f-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="d589f-105">Existuje několik klíčových funkcí rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, které umožňují konstrukci funkčnosti:</span><span class="sxs-lookup"><span data-stu-id="d589f-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="d589f-106">Konstruktor <xref:System.Xml.Linq.XElement> přebírá různé typy argumentů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="d589f-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="d589f-107">Například můžete předat další objekt <xref:System.Xml.Linq.XElement>, který se stal podřízeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="d589f-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="d589f-108">Můžete předat objekt <xref:System.Xml.Linq.XAttribute>, který se stal atributem elementu.</span><span class="sxs-lookup"><span data-stu-id="d589f-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="d589f-109">Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a který se změní na textový obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="d589f-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="d589f-110">Konstruktor <xref:System.Xml.Linq.XElement> přebírá `params` pole typu <xref:System.Object>, takže můžete konstruktoru předat libovolný počet objektů.</span><span class="sxs-lookup"><span data-stu-id="d589f-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="d589f-111">To umožňuje vytvořit prvek, který má složitý obsah.</span><span class="sxs-lookup"><span data-stu-id="d589f-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="d589f-112">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vyhodnocena kolekce v objektu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d589f-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="d589f-113">Pokud kolekce obsahuje objekty <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="d589f-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="d589f-114">To je důležité, protože umožňuje předat výsledky dotazu LINQ do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d589f-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="d589f-115">Tyto funkce umožňují napsat kód pro vytvoření stromu XML.</span><span class="sxs-lookup"><span data-stu-id="d589f-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="d589f-116">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="d589f-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="d589f-117">Tyto funkce také umožňují napsat kód, který používá výsledky dotazů LINQ při vytváření stromu XML takto:</span><span class="sxs-lookup"><span data-stu-id="d589f-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d589f-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d589f-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  