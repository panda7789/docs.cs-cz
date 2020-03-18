---
title: Funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635753"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="243c3-102">Funkční konstrukce (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="243c3-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="243c3-103">poskytuje účinný způsob vytváření elementů XML nazývaných *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="243c3-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="243c3-104">Funkční konstrukce je schopnost vytvořit strom XML v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="243c3-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="243c3-105">Existuje několik klíčových [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkcí programovacího rozhraní, které umožňují funkční konstrukci:</span><span class="sxs-lookup"><span data-stu-id="243c3-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="243c3-106">Konstruktor <xref:System.Xml.Linq.XElement> má různé typy argumentů pro obsah.</span><span class="sxs-lookup"><span data-stu-id="243c3-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="243c3-107">Můžete například předat <xref:System.Xml.Linq.XElement> jiný objekt, který se stane podřízeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="243c3-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="243c3-108">Můžete předat <xref:System.Xml.Linq.XAttribute> objekt, který se stane atributem prvku.</span><span class="sxs-lookup"><span data-stu-id="243c3-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="243c3-109">Nebo můžete předat jakýkoli jiný typ objektu, který je převeden na řetězec a stane se textovým obsahem prvku.</span><span class="sxs-lookup"><span data-stu-id="243c3-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="243c3-110">Konstruktor <xref:System.Xml.Linq.XElement> přebírá `params` pole typu <xref:System.Object>, takže můžete předat libovolný počet objektů konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="243c3-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="243c3-111">To umožňuje vytvořit prvek, který má komplexní obsah.</span><span class="sxs-lookup"><span data-stu-id="243c3-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="243c3-112">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekce v objektu je výčtu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="243c3-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="243c3-113">Pokud kolekce <xref:System.Xml.Linq.XElement> obsahuje <xref:System.Xml.Linq.XAttribute> nebo objekty, každá položka v kolekci je přidán samostatně.</span><span class="sxs-lookup"><span data-stu-id="243c3-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="243c3-114">To je důležité, protože umožňuje předat výsledky dotazu LINQ konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="243c3-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="243c3-115">Tyto funkce umožňují psát kód pro vytvoření stromu XML.</span><span class="sxs-lookup"><span data-stu-id="243c3-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="243c3-116">Například:</span><span class="sxs-lookup"><span data-stu-id="243c3-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="243c3-117">Tyto funkce také umožňují psát kód, který používá výsledky dotazů LINQ při vytváření stromu XML, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="243c3-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="243c3-118">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="243c3-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  